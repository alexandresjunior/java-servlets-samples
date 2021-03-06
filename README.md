# Java Servlets Samples

The name “servlet” gives an idea of a small server whose purpose is basically to receive HTTP requests, process them and respond to the client. This response can be HTML, an image, a json file etc. This technology is packaged in a small JAR considered practically a Java "standard" and allows you to create small web servers and make our web application respond to a browser on an `address + port`.

It works as follows:

1. Client (via browser) makes an HTTP request to the server;
2. The responsible servlet handles the request and responds to the client accordingly;
3. The client receives the data and displays it.

When developing web applications in Java, it is not necessary to implement classes that will support HTTP. Java itself already has a technology called `servlet` (mini-server) in its libraries. The `Hello, world!` example covers the servlet behaviors that have been defined in the `HttpServlet` class of the `javax.servlet` package, which is used in most cases. The `Servlet` interface is what defines exactly how a servlet works, but that's not going to be used, since it allows the use of any protocol based on requests and responses, and not specifically HTTP.

Also, as in Java, we always try to work using object-oriented paradigm, our servlet will also be an object of a Java class. Each servlet is, therefore, a Java object that receives such **requests** and produces **responses**, such as a dynamically generated HTML page.


## Hello, world!

In order to do the famous `Hello, world!` example, you must have already installed and configured **Tomcat** in Eclipse. Then you must create a new project of the *Dynamic Web Project* type, type the name of the project `hello-world-servlet`, choose the target runtime which is *Tomcat* and click *finish* (you might want to answer *no* to the question about changing IDE perspective).

On the *Servers* tab, right-click on *Tomcat* and then on *Add and Remove*... now just add the project created, whose generated directory structure looks like the following:

* `src` - Java source code (`.java`)
* `build` - where Eclipse compiles the classes (`.class`)
* `WebContent` - content directory (pages, images, css etc. go here)
* `WebContent/WEB-INF/` - hidden folder with project settings and resources
* `WebContent/WEB-INF/lib/` - `.jar` libraries.
* `WebContent/WEB-INF/classes/` - compiled files are copied here.

**Obs.:** The `META-INF` folder is optional, but it is generated by Eclipse. This is where the Manifest file as used in `.jar` files is.

To create a servlet class, it will have to be a subclass of `HttpServlet` and override the `service()` method, which is responsible for receiving requests and returning their responses. Inside `src` folder, there is the `com.servlets.HelloWorldServlet` class. Notice that the method receives two objects that represent, respectively, the **request** made by the user and the **response** that will be displayed at the end.

This first example does not perform any logic and just shows a static welcome message to the user. It is possible to obtain an object that represents the output to be sent to the user through the `getWriter` method of the response variable. And, from that, use a `PrintWriter` to print something in the client's response.

The only purpose of the servlet above is to display a simple HTML message to users who request it. But notice how it is possible to write other more powerful Java code to generate HTML Strings based on dynamic information coming, for example, from a database.

The servlet is defined, but how can you access it from the browser? You must map our class to URL's inside the `web.xml` file that is created inside the `WEB-CONTENT/WEB-INF` folder automatically by the IDE you are using. To map, we will use the tags `<servlet>` and `<servlet-mapping>`. First the name of the servlet and its class are defined, and then which way it will be accessible, in this case, via `http://localhost:8080/hello-world-servlet/helloWorld`.
