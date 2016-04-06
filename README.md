# JsonWrap
在使用Ajax向服务器放松请求时，服务器需要返回数据。但数据的格式一般都是JSON格式，本工具类就是把服务器处理后的数据封装成JSON字符串。
此类包含三个函数：
1.toJsonString(collection<?> collection);
接收实现Collection接口的集合类，把该集合中的对象封装成JSON字符串，此过程使用了反射技术来读取对象属性和属性值。
2.tJsonString2(Object object);
接收非集合对象，往往应用在服务器返回的是一个对象，而不是多个。
3.wrap(boolean b,String message);
接收一个布尔类型和字符串类型参数，往往应用在服务器返回的是一个判断结果，且需要向浏览返回一些信息。
