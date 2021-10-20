# 	HTTP协议

- URL：Uniform Resource Locator,统一资源定位，即网络地址，类似www.baidu.com

### 使用HTTP协议访问Web

- 输入URL时，Web浏览器从Web服务器端获取文件资源(resource)等信息从而显示出web页面。
- 像这种通过发送请求获取服务器资源的Web浏览器等都可称为客户端(Client)
- Web使用HTTP(HyperText Transfer Protocol,超文本传输协议)作为规范完成从客户端到服务器端一系列运作流程，可以说Web是建立在HTTP协议上通信的

### HTTP的诞生

- CERN(欧洲核子研究组织)的蒂姆伯纳斯李博士提出了一种能让远隔两地的研究者们共享知识的设想，最初设想的基本理念是:借助多文档之间相互关联形成的超文本连成可互相参阅的WWW(World Wide Web,万维网)
- 到今天已提出了3项WWW构建技术，分别是
  - 把SGML(Standard Generalized Markup Language,标准通用标记语言)作为页面的文本标记语言的HTML
  - 作为文档传递协议的HTTP
  - 指定文档所在地址的URL
- 1997年1月公布的HTTP/1.1是目前主流的HTTP协议版本，可见作为Web文档传输协议的HTTP版本几乎没有更新，HTTP/2.0正在制定，但达到较高覆盖率仍需较长时间。
- 当年HTTP出现是为了解决文本传输的难题，由于协议本身十分简单，于是在此基础上设想了很多应用方法并投入了实际使用，现在HTTP协议已经超出了Web这个框架的局限，被运用到了各种场景里。