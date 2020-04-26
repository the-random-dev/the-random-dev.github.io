---
layout: article
title: S.O.L.I.D Principles
tags: programming SOLID principles quality
comments: true
key: solid-principles-2020-04-26
sharing: true
description: Do you have a S.O.L.I.D. code? S.O.L.I.D principles was introduced by Robert C. Martin, aka Uncle Bob, in 2000 and the acronym itself was introduced by Michael Feathers.Those are 5 principles for object-oriented programming that helps you develop a better code quality.

---

Do you have a S.O.L.I.D. code?

S.O.L.I.D principles was introduced by Robert C. Martin, aka Uncle Bob, in 2000 and the acronym itself was introduced by Michael Feathers.

Those are 5 principles for object-oriented programming that helps you develop a better code quality.

### S - Single Responsability Principle (SRP)

"One class should have only one responsibility":  each function, method or class needs to do just one thing, and do it well. For example, if you have created a class Person, a person has a name and surname, date of birth, and other information. But operations like reading and writing it on a database is not a responsibility of a person. So move it those operations to another class.

It allows develop more maintainable and reusable code because each part does only what is expected to do. You can reduce the number of tests for each class, you will have less coupling and a more organized code.

Let's see this code:
```java
public class 𝙳𝚊𝚝𝚊 
{
    public void send(String data)
    {
        try
        {
            // Operation to send data
        }
        catch(Exception ex)
        {
            System.out.println(ex.ToString());
            File.WriteAllTextr("error.log", ex.ToString());
        }

        
    }
}
```
The responsability of that class is send a message. It is not a responsability what to do with an error message. Let's change it to respect our SRP Principle:

```java
public class 𝙳𝚊𝚝𝚊 
{
    private Logger logger;
    
    ... // Constructor and inicialization of logger object

    public void send(String data)
    {
        try
        {
            // Operation to send data
        }
        catch(Exception ex)
        {
            logger.log(ex.toString());
        }

        
    }
}
```

```java
public class Logger 
{
    public void log(S𝚝𝚛𝚒𝚗𝚐 data)
    {
        
        System.out.println(ex.ToString());
        File.WriteAllTextr("error.log", ex.ToString());
    }
}
```
Now our class data just does data operations, while the operation of logging errors is responsibility of Logger class.

### O - Open Closed Principle (OCP)
"Software entities should be open for extension, but closed for modification": This is one of most important principle of OOP, let's do an example, in our software we can send data over Wi-Fi and Ethernet:

```java
public class 𝙳𝚊𝚝𝚊 
{
    public void send(String 𝚍𝚊𝚝𝚊, Transmitter tx)
    {
        if(tx == Transmitter.WIFI)
        {
            ...
        } 
        else if(tx == Transmitter.ETHERNET)
        {
            ...
        }
        this.sendMessage(); 
    }
}
```
Every single time we have a new way to transmit data, we would change that class. To correct it:

Data class:
```java
public abstract class 𝙳𝚊𝚝𝚊
{ 
    public abstract void send(String data);
}
```
A class for Wi-fi:
```java
public abstract class 𝚆if𝚒𝙳𝚊𝚝𝚊 𝚎𝚡𝚝𝚎𝚗𝚍𝚜 𝙳𝚊𝚝𝚊
{ 
    @Override
    public abstract void send(String data)
    {
        ...
    }
}
```
Another class for Ethernet:
```java
public abstract class 𝙴𝚝𝚑𝚎𝚛𝚗𝚎𝚝𝙳𝚊𝚝𝚊 𝚎𝚡𝚝𝚎𝚗𝚍𝚜 𝙳𝚊𝚝𝚊
{ 
    @Override
    public abstract void send(String data)
    {
        ...
    }
}
```
In the future, if someone needs to send data over Bluetooth, we extend our class Data (open for extension) but won't change our base class Data (closed for modification). Now we have a more reusable code.

### L - Liskov Substitution Principle (LSP)
"If S is a subtype of T, then objects of type T may be replaced (or substituted) with objects of type S": WHAT???
In other words:"If it looks like a duck, quacks like a duck, but need batteries, you probably have the wrong abstraction".
Let's suppose we have our class Shape:
```java

public class Ellipse 
{
      public float area(float width, float height) {…}
}
```

```java
public  class 𝙲𝚒𝚛𝚌𝚕𝚎 extends Ellipse
{
      public float area(float width, float height) {…}
}
```

It respects our Open-Closed Principle, and in a real world a circle is a special case of an Ellipse. But it can generate some inconsistence, an user could pass a different value of a width and height. Would we consider one value? Would we generate an Exception? In this case, the problem is that circle does not inherit Ellipse, it is a problem of abstraction.

### I - Interface Segregation Principle (ISP)

"Many client-specific interfaces are better than one general-purpose interface." It basically says, each class should not be forced to implement methods that are not used. In short, it is better more interfaces with less methods than a interface with more methods that won't be implemented on their classes.

```java
public interface IMessage
{
    public void send(String data);
    public String receive();
    public void close();
}
```

```java
public class UDP implements IMessage
{
    public void send(String data) {}
    public String receive() {}

    public void close()
    {
        // UDP is not a connection, so we cannot close it
    }
}
```


```java
public interface IMessage
{
    public void send(String data);
    public String receive();
}
```
```java
public interface IConnection
{
    public void close();
}
```
Now we do not need to implement useless methods on our UDP class

### D. Dependency Inversion Principle (DIP)
"One should depend upon abstractions, not concretions.": it helps you decoupling your software modules. One example, all databases have operations for connection, writing and reading data. It is better create an interface and a method that wraps those operations than implementing it directly on our classes. If later we change our database, we need just to change the abstraction class and not change all entire application to adapt it to our database.


In our example we have our wifi module:
```java
public WifiModule extends IDevice
{
    public void TurnOn()
    {
        ...
    }
}
```
And a class that we can turn on our Wifi Module.

```java
public DeviceControl
{
    private WifiModule wifiModule;
    
    public void TurnOnDevice()
    {
        wifiModule.TurnOn(); 
    }
}
```
Now let's suppose we decide to change our device to a Ethernet module. We would to change our DeviceControl class to our EthernetModule. When we depends on interface, we could change it without relying on our DeviceControl class:


```java
public interface IDevice
{
    public void TurnOn();
}
```

```java
public WifiModule extends IDevice
{
    public void TurnOn()
    {
        ///
    }
}
```

```java
public EthernetModule extends IDevice
{
    public void TurnOn()
    {
        ///
    }
}
```

```java
public DeviceControl
{
    private IDevice device;
    
    ...    

    public void TurnOnDevice()
    {
        device.TurnOn(); //
    }
}
```

It means, we can develop a more modularized code and each part is less dependent of other parts.


### Conclusion

S.O.L.I.D principles help us to create a more robust code, easy to maintain and also reduces the chances to inject bugs in parts that was working before.