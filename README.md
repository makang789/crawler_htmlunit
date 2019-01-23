# crawler_htmlunit
htmlunit进行爬虫
  使用到htmlunit如何去除日志。
      解决方案
      针对不同的日志实现收集了几种不同的实现方案，以备后用
      log4j
      使用的是slf4j-api和slf4j-log4j12和log4j
      在配置文件log4j.properties中加入如下配置项
          log4j.logger.httpclient.wire=fatal
          log4j.logger.org.apache.commons=fatal
          log4j.logger.com.gargoylesoftware.htmlunit=fatal
          log4j.logger.com.gargoylesoftware.htmlunit.WebTestCase=fatal
          log4j.logger.com.gargoylesoftware.htmlunit.javascript.DebugFrameImpl=fatal
      java.util.logging
      在方法中加入如下行
          java.util.logging.Logger.getLogger("com.gargoylesoftware").setLevel(Level.OFF); 
      org.apache.commons.logging.Log
      在方法中加入如下行
          LogFactory.getFactory().setAttribute("org.apache.commons.logging.Log", "org.apache.commons.logging.impl.NoOpLog");
