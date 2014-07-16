URL: <http://www.laurentluce.com/posts/python-threads-synchronization-locks-rlocks-semaphores-conditions-events-and-queues/>

###Python threads synchronization: Locks, RLocks, Semaphores, Conditions, Events and Queues

This article describes the Python threading synchronization mechanisms in details. We are going to study the following type: 
Lock, RLock, Semaphore, Condition, Event and Queue. Also, we are going to look at the Python internals behind those 
mechanisms.

The source code of the programs below can be found at github.com/laurentluce/python-tutorials under threads/.

First, let’s look at a simple program using the threading module with no synchronization.

####Threading

We want to write a program fetching the content of some URLs and writing it to a file. We could do it serially with no threads but to speed things up, we are going to create 2 threads processing half of the URLs each.

Note: The best way here would be to use a queue with the URLs to fetch but this example is more suitable to begin our tutorial.


The class FetchUrls is thread based and it takes a list of URLs to fetch and a file object to write the content to.

```
class FetchUrls(threading.Thread):
    """
    Thread checking URLs.
    """

    def __init__(self, urls, output):
        """
        Constructor.

        @param urls list of urls to check
        @param output file to write urls output
        """
        threading.Thread.__init__(self)
        self.urls = urls
        self.output = output
    
    def run(self):
        """
        Thread run method. Check URLs one by one.
        """
        while self.urls:
            url = self.urls.pop()
            req = urllib2.Request(url)
            try:
                d = urllib2.urlopen(req)
            except urllib2.URLError, e:
                print 'URL %s failed: %s' % (url, e.reason)
            self.output.write(d.read())
            print 'write done by %s' % self.name
            print 'URL %s fetched by %s' % (url, self.name)
```

The main function starts the 2 threads and then wait for them to finish.

```
def main():
    # list 1 of urls to fetch
    urls1 = ['http://www.google.com', 'http://www.facebook.com']
    # list 2 of urls to fetch
    urls2 = ['http://www.yahoo.com', 'http://www.youtube.com']
    f = open('output.txt', 'w+')
    t1 = FetchUrls(urls1, f)
    t2 = FetchUrls(urls2, f)
    t1.start()
    t2.start()
    t1.join()
    t2.join()
    f.close()

if __name__ == '__main__':
    main()
```

The issue is that both threads are going to write to the file at the same time, resulting in a big mess. We need to find a way to only have 1 thread writing to the file at a given time. To do that, one way is to use synchronization mechanisms like locks.

####Lock


Locks have 2 states: locked and unlocked. 2 methods are used to manipulate them: acquire() and release(). Those are the rules:



if the state is unlocked: a call to acquire() changes the state to locked.
if the state is locked: a call to acquire() blocks until another thread calls release().
if the state is unlocked: a call to release() raises a RuntimeError exception.
if the state is locked: a call to release() changes the state to unlocked().

To solve our issue of 2 threads writing to the same file at the same time, we pass a lock to the FetchUrls constructor and we use it to protect the file write operation. I am just going to highlight the modifications relevant to locks. The source code can be found in threads/lock.py.

```
class FetchUrls(threading.Thread):
    ...

    def __init__(self, urls, output, lock):
        ...
        self.lock = lock
    
    def run(self):
        ...
        while self.urls:
            ...
            self.lock.acquire()
            print 'lock acquired by %s' % self.name
            self.output.write(d.read())
            print 'write done by %s' % self.name
            print 'lock released by %s' % self.name
            self.lock.release()
            ...

def main():
    ...
    lock = threading.Lock()
    ...
    t1 = FetchUrls(urls1, f, lock)
    t2 = FetchUrls(urls2, f, lock)
    ...
    
```

<img src="http://www.laurentluce.com/images/blog/threads/lock.png"/>

Let’s look at the program output when we run it:

```
$ python locks.py
lock acquired by Thread-2
write done by Thread-2
lock released by Thread-2
URL http://www.youtube.com fetched by Thread-2
lock acquired by Thread-1
write done by Thread-1
lock released by Thread-1
URL http://www.facebook.com fetched by Thread-1
lock acquired by Thread-2
write done by Thread-2
lock released by Thread-2
URL http://www.yahoo.com fetched by Thread-2
lock acquired by Thread-1
write done by Thread-1
lock released by Thread-1
URL http://www.google.com fetched by Thread-1
```


