---
layout: post
title: Spring, conceptos básicos
lang: es
country: ES
description: "Spring, conceptos básicos, Inversion of Control,  Dependency Injection"
modified: 2015-01-20
tags: [Spring framework, dependency injection, inversion of control, java]
image:
  feature: abstract-9.jpg
  credit: dargadgetz
  creditlink: http://www.dargadgetz.com/ios-7-abstract-wallpaper-pack-for-iphone-5-and-ipod-touch-retina/
---


[<img src="{{ site.url }}/images/20160120Spring-conceptos-basicos/image01.png" alt="Spring Framework logo">{: .image-right}](http://docs.spring.io/spring/docs/current/spring-framework-reference/html/beans.html){:target="_blank"}
En este post voy a intentar demostrar la sencillez de dos conceptos muy importantes en Spring:

* Inversion of Control (IoC) = Inversión del Control.
* Dependecy Injection(DI) =  Inyección de Dependencias. 


## Inversion of Control & Dependency Injection


“**Es el proceso mediante el cual los objetos definen sus dependencias**, bien mediante argumentos en el constructor, argumentos en un método factoría o propiedades que se asignan una vez el objeto está creado.”

La definición de estas dependencias se puede hacer con xml, anotaciones o mediante código java.

<img src="{{ site.url }}/images/20160120Spring-conceptos-basicos/image00.png" alt="Formatos expresar dependencias">{: .image-center} 


Entonces aparece en escena nuestro amigo el contenedor: 
<img src="{{ site.url }}/images/20160120Spring-conceptos-basicos/image04.png" alt="Contenedor">
{% highlight java %}
 	org.springframework.context.ApplicationContext
{% endhighlight %}

Es el contenedor quien inyecta las dependencias al crear el bean.

Este proceso es el inverso a la creación de instancias o asignación de dependencias, tanto usando la creación directa de las mismas o un mecanismo como Service Locator Pattern.

<img src="{{ site.url }}/images/20160120Spring-conceptos-basicos/image03.png" alt="Esquema funcionamiento contenedor Spring">


Por resumirlo mucho: Es el contenedor quien hace el trabajo de crear instancias en lugar de las clases, de ahí el nombre Inversion of Control.(Inversión del control)


No mas “a = new A(....);” este trabajo sucio se lo dejamos al contenedor (IoC container).


Bean: Un bean es un objeto que es instanciado, ensamblado o gestionado por un IoC Container.


Una de las ventajas de usar un contenedor (IoC Container), es que la gestión de dependencias ya no se hace dentro de las clases. Cada clase o Bean es autocontenida, sólo tiene que preocuparse de su alcance, será el contenedor quien le proporcione las instancias de clases que necesita.


{% highlight java %}
Alta cohesión y bajo nivel de acoplamiento.
{% endhighlight %}

## Ejemplo

Este sencillo ejemplo muestra:

* La configuración minima para ejecutar un Spring Container
* Cómo funciona la IoC o DI a un nivel muy básico


[ <img src="{{ site.url }}/images/gitHub-logo.png" alt="logo gitHub" style="max-width: 30px;"> Spring-01-Ioc-Di-concepts](https://github.com/rafasoriazu/Spring-01-Ioc-Di-concepts){:target="_blank"}



[<img src="{{ site.url }}/images/codenvy-logo.jpg" alt="logo Codenvy" style="max-width: 30px;"> Codenvy](https://codenvy.com/ide-resources/share/project/rafasoriazu/Spring-01-Ioc-Di-concepts){:target="_blank"}


### Configuración mínima

**pom.xml** en el cual vamos a declarar los paquetes de Spring que necesitamos

Sólo con spring-context ya nos basta.

Por dependencias transitivas, nos descargará también los paquetes del "core container"

{% highlight java %}
<dependencies>
  	<dependency>
   	<groupId>org.springframework</groupId>
    	<artifactId>spring-context</artifactId>
    	<version>4.1.6.RELEASE</version>
	</dependency>
  </dependencies>  
{% endhighlight %}

<img src="{{ site.url }}/images/20160120Spring-conceptos-basicos/image02.png" alt="Esquema paquetes Spring">


### Configuraciones

application-context.xml

{% highlight java %}
      <!-- A simple bean definition -->
   <bean id="messageBean" class="me.itnotes.Message">
       <!-- collaborators and configuration for this bean go here -->
        <property name="message" value="Hola mundo. "/>
   </bean>
{% endhighlight %}

### Pojo

{% highlight java %}
public class Message {

  private String message;

	public String getMessage() {
		return message;
	}

	public void setMessage(String message) {
		this.message = message;
	}
	
	public void processMessage(){
     message=" Este es el mensaje que tengo: " +message;
   }
}
{% endhighlight %}


### Runner

{% highlight java %}
public class Runner {

	public static void main(String[] args) {
	//Creamos el applicationContext con lo definido en application-context.xml
	ApplicationContext applicationContext = new ClassPathXmlApplicationContext("/application-context.xml");   
	//Obtenemos el bean que se nos ha creado
	Message message = (Message) applicationContext.getBean("messageBean");
    //LLamada a un metodo tonoto del bean
    message.processMessage();
    System.out.println(message.getMessage());
    //Cerrar el applicationContext
    ((ConfigurableApplicationContext)applicationContext).close();
         
	}

}

{% endhighlight %}