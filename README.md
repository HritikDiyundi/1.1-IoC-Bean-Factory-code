# 1.1-IoC-Bean-Factory-code

# Welcome to Spring BeanFactory Example

This repository provides a simple example demonstrating the usage of BeanFactory in the Spring Framework.

## Procedure:

1. **Create a Spring project using start.spring.io:**
   - Start by setting up a new Spring project using [start.spring.io](https://start.spring.io/). Choose the dependencies you need and generate the project.

2. **Create a POJO class:**
   - Define your Plain Old Java Object (POJO) class that represents the entity you want to work with in your Spring application.

3. **Configure the Student bean in the bean-factory-demo.xml file:**
   - Create a configuration file, such as `bean-factory-demo.xml`, where you define the beans for your Spring application. Configure your `Student` bean with appropriate dependencies and settings.

4. **Write it to application class:**
   - Write your application class where you initialize the Spring context and access the beans defined in the XML configuration file. You can then use these beans in your application logic.

Follow these steps to kickstart your Spring project and harness the power of dependency injection with ease!


## Usage

### Step 1: Define Your Class

Create a class, like `User`, with dependencies you want to manage. Here's a snippet:

```java
public class User {
    private String name;

    public User(String name) {
        this.name = name;
    }

    public void greet() {
        System.out.println("Hello, my name is " + name);
    }
}
```

### Step 2: Define Your Class Configure with XML

In an XML file, let's say beans.xml, configure your class and its dependencies. Example:

```java
<beans xmlns="http://www.springframework.org/schema/beans"
       xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
       xsi:schemaLocation="http://www.springframework.org/schema/beans
                           http://www.springframework.org/schema/beans/spring-beans.xsd">

    <bean id="user" class="com.example.User">
        <constructor-arg value="John" />
    </bean>
</beans>

```


### Step 3: Utilize BeanFactory
Now, leverage BeanFactory to manage your beans. Here's how:

``` java
import org.springframework.beans.factory.BeanFactory;
import org.springframework.beans.factory.xml.XmlBeanFactory;
import org.springframework.core.io.ClassPathResource;

public class Main {
    public static void main(String[] args) {
        // Initialize BeanFactory with the XML configuration file
        BeanFactory factory = new XmlBeanFactory(new ClassPathResource("beans.xml"));

        // Retrieve the User bean from the BeanFactory
        User user = (User) factory.getBean("user");

        // Use the user object
        user.greet();
    }
}
```


### Expected Output
The output of running the code will be:

```java
Hello, my name is **John**

```
