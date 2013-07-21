+ Feature应该描述特性，而不是程序的组成部分

+ 避免特性与domain逻辑的不一致性

+ 用组织代码的思想来组织特性与场景
  
  + 运行速度
    + fast
    + slow
    + glacial
  
  + 多种方式来分解
    + 放在各自的独立的特性中
    + 放在各自的文件夹下面
    + 给他们打标签
    
  + 使用标签
    + 运行时间
      + checkin
      + hourly
      + daily
    
    + 外部依赖
      + local
      + database
      + network
      
    + 其他
    
  + 使用rake 任务来运行特性
  
  + 不要过度使用background
  
  + 特性要独立，可以自我决断
  
  + 要为not-happy-path编写用例场景
  
  + 遵循DRY，不断重构代码
  
  + 在step definition中使用库（例如chronic来解析时间）
  
  + 重新阅读及重构和改善场景与步骤的编写
  
  + 重构feature与step使其更好地反映领域
  
  + 使用复合步骤来强化你的语言
  
  + 使用并行的step definition来支持特性的不同实现
  
  + 避免使用联合步骤
  
<http://www.engineyard.com/blog/2009/15-expert-tips-for-using-cucumber/>
