# A simple example of a Java Service Provider (SPI) mechanism

## Introduction
This is a simple implementation of the [SPI](https://docs.oracle.com/javase/tutorial/ext/basics/spi.html) extension mechanism from Java.

  * The whole extension SPI mechanism is in the work package.
  * An example of a service (ie extension) is located in the workExtension package. The extension registration occurs by placing a file under the resources/META-INF/services
that points to the work provider (In this example, to HelloWorkProvider)

You see the whole mechanism in action by calling the main method of the Main class in the src directory.

```java
URI uri = new URI("hello");
Work work = Works.getWork(uri);
work.execute();
```

The Works factory method (getWork) will trigger the search and load of all WorkProviders service. 
When it finds the "hello" service provider, it will call its getWork function in order to get an instance of the service object 
(in this example: the workExtension.HelloWorld)



## Documentation / Reference

  * The whole mechanism is really well explain in the java doc of the [java.util.ServiceLoader](http://docs.oracle.com/javase/8/docs/api/java/util/ServiceLoader.html).
  * This code was made by taking as example the nio FileSystemProvider implementation. [java.nio.file.spi.FileSystemProvider](https://docs.oracle.com/javase/8/docs/api/java/nio/file/spi/FileSystemProvider.html)
  * [Java - Service Provider Interface (SPI)](http://gerardnico.com/wiki/language/java/spi)