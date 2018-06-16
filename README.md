# Example spring boot application deployed to Heroku

## Heroku deployment
To prepare the application to be deployed to Heroku:

1. Add the Procfile with the instruction to run the application once it has been built (don't forget to specify ```$JAVA_OPTS``` and ```--server.port=$PORT``` )      
  
In Heroku create an application and link it to your repository on GitHub. You'll be able to link
automatic deployments for changes to a specific branch or do manual deployment in any moments using any branch

The application is deployed to:

https://test-iuresti.herokuapp.com/ 

## Simple mvc example

### pom.xml

The dependencies added for the simple mvc project using jsp are:

* spring-boot-starter-web
* spring-boot-starter-tomcat
* tomcat-embed-jasper
* javax.servlet
* jstl

Optionally you can add the webjars like ```bootstrap``` to make it easier to create nice views

### views

In this example I'm using welcome.jsp to construct a simple view. With the dependencies listed above, we'll
be able to use jstl to create cleaner and more expresive code in the views.

The configuration you'll need to add to your application.yml is

```$yml
spring:
  mvc:
    view:
      prefix: /
      suffix: .jsp
```

You can locate your jsp files on a subdirectory by modifying `spring.mvc.view.prefix` parameter like Mkyong does
in his [example](https://www.mkyong.com/spring-boot/spring-boot-hello-world-example-jsp/) where he adds the files to 
webapp/WEB-INF/jsp/. The result is the same.

To reach the view from the browser I'm creating the class `HomeController` annotated with
`@Controller`. In this class the method `welcome` is annotated with `@RequestMapping("/")`.

The annotation tells spring boot that when the user requests the resource `/` it must return the view `welcome`

The name of the view corresponds to a the file `welcome.jsp` (notice the parameter `spring.mvc.view.suffix`)

You can pass data from the controller to the view through the object `model` received as parameter in the method 
`welcome` of `HomeController`. For an example of this see that I'm setting the value with key `message` in HomeController and
the the value is used in `welcome.jsp` in `<h2>Message: ${message}</h2>`


## References

### MVC Example
* https://www.mkyong.com/spring-boot/spring-boot-hello-world-example-jsp/
* https://hellokoding.com/spring-boot-hello-world-example-with-jsp/

### Heroku deployment


### CI
