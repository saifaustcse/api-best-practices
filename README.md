## Software Design Patterns

> Though there are 1000’s of articles about **Software Design Patterns**, I have written this article is in order to document with simple C# realworld example with short and easy description. I have also created another repository regarding [Software Design principles](https://github.com/saifaustcse/software-design-patterns) which can be helpful as well.

## Give a Star! :star:

> If you like or are using this project to learn or start your solution, please give it a star. Thanks!

## Find me

> Find me if you wish [@Saif(https://www.linkedin.com/in/saif-aust-cse/).

### Table of Contents

| No. | Topic                                                               |
| --- | ------------------------------------------------------------------- |
| 1   | [What are Design Patterns?](#What-are-Design-Patterns)              |
| 2   | [Factory Design Pattern](#Factory-Design-Pattern)                   |
| 3   | [Factory Method Design Pattern](#Factory-Method-Design-Pattern)     |
| 4   | [Abstract Factory Design Pattern](#Abstract-Factory-Design-Pattern) |
| 5   | [Builder Design Pattern](#Builder-Design-Pattern)                   |
| 6   | [Fluent Interface Design Pattern](#Fluent-Interface-Design-Pattern) |
| 7   | [Prototype Design Pattern](#Prototype-Design-Pattern)               |
| 8   | [Singleton Design Pattern](#Singleton-Design-Pattern)               |
| 9   | [Adapter Design Pattern](#Adapter-Design-Pattern)                   |
| 10  | [Bridge Design Pattern](#Bridge-Design-Pattern)                     |
| 11  | [Composite Design Pattern](#Composite-Design-Pattern)               |
| 12  | [Decorator Design Pattern](#Decorator-Design-Pattern)               |
| 13  | [Facade Design Pattern](#Facade-Design-Pattern)                     |
| 14  | [Flyweight Design Pattern](#Flyweight-Design-Pattern)               |
| 15  | [Proxy Design Pattern](#Proxy-Design-Pattern)                       |
| 30  | [References](#references)                                           |

1.  ### What are Design Patterns?

    A Design Pattern is a general reusable solution to a commonly occurring problem within a given context in software design
    It describes the problem, the solution, when to apply the solution, and its consequences. It also gives implementation hints and examples.

    In 1994, four authors Erich Gamma, Richard Helm, Ralph Johnson and John Vlissides published a book titled **Design Patterns: Elements of Reusable Object-Oriented Software** which initiated the concept of Design Pattern in Software development.

    As per the design pattern reference book Design Patterns - Elements of Reusable Object-Oriented Software , there are 23 design patterns which can be classified in three categories: Creational, Structural and Behavioral patterns.

    **Creational Design Patterns**

    > Creational design patterns are design patterns that deal with object creation mechanisms, trying to create objects in a manner suitable to the situation. The basic form of object creation could result in design problems or added complexity to the design. Creational design patterns solve this problem by somehow controlling this object creation.

    The following design patterns belong to the Creational Design pattern category:

    - [Builder](#Builder-Design-Pattern)
    - [Factory](#Factory-Design-Pattern)
    - [Factory Method](#Factory-Method-Design-Pattern)
    - [Abstract Factory](#Factory-Method-Design-Pattern)
    - [Fluent Interface](#Fluent-Interface-Design-Pattern)
    - [Prototype](#Prototype-Design-Pattern)
    - [Singleton](#Singleton-Design-Pattern)

    **Structural Design Patterns**

    > Structural design patterns are design patterns that ease the design by identifying a simple way to realize relationships among entities. Structural patterns are concerned with how classes and objects are composed to form larger structures.

    The following design patterns belong to the Structural Design pattern category:

    - [Adapter](#Adapter-Design-Pattern)
    - [Bridge](#Bridge-Design-Pattern)
    - [Composite](#Composite-Design-Pattern)
    - [Decorator](#Decorator-Design-Pattern)
    - [Facade](#Facade-Design-Pattern)
    - [Flyweight](#Flyweight-Design-Pattern)
    - [Proxy](#Proxy-Design-Pattern)

    **Behavioral Design Patterns**

    > Behavioral patterns are concerned with algorithms and the assignment of responsibilities between objects. Behavioral patterns describe not just the patterns of objects or classes but also the patterns of communication between them.

    The following design patterns belong to the Behavioral Design pattern category:

    - Chain of Responsibility
    - Command
    - Interpreter
    - Iterator
    - Mediator
    - Memento
    - Observer
    - State
    - Strategy
    - Visitor
    - Template Method.

    Along with GoF 23 Design Patterns, there are some other design patterns which are used frequently in most of the real-time applications.

    - Dependency Injection
    - Repository Design Pattern
    - Inversion of Control

    **[⬆ Back to Top](#table-of-contents)**

2.  ### Factory Design Pattern

    Intent

    > Define an object for creating other objects.

    In technical terms, we can say that a factory is a class with a method. That method will create and return different types of objects based on the input parameter, it received.

    Advantages

    - We can get an object of similar type based on the parameter.
    - We create an object without exposing the creation logic to the client

    We need to choose the Factory Design Pattern, when

    - The Object needs to be extended to the subclasses
    - Classes don’t know what exact sub-classes it has to create
    - The Product implementation going to change over time and the Client remains unchanged

    Problems

    If we need to add any new class then we also need to update Factory class which violates the open/closed design principle.

    <details>
    <summary><b>Factory Design Pattern realword example (Notification)</b></summary>
    <br>

    <div  style="text-align: center;">
         <img src="https://github.com/saifaustcse/software-design-patterns/blob/main/images/factory-notification-brief.PNG?raw=true" width="600" height="300">
    <div>

    Run the following C# console application in visual studio or visual studio code, also you can run code in [online](https://code.sololearn.com/#cs)

        using System;

        namespace factoryDesignPattern
        {
            class Program
            {

                static void Main()
                {
                    // Client Code
                    NotificationFactory notificationFactory = new NotificationFactory();
                    INotification notification = notificationFactory.createNotification("SMS");
                    notification.NotifyUser();

                    Console.ReadKey();

                }
            }

            public interface INotification
            {
                void NotifyUser();
            }

            public class SMSNotification : INotification
            {

                public void NotifyUser()
                {
                    // TODO Auto-generated method stub
                    Console.WriteLine("Sending an SMS notification");
                }
            }

            public class EmailNotification : INotification
            {

                public void NotifyUser()
                {
                    // TODO Auto-generated method stub
                    Console.WriteLine("Sending an EMAIL notification");
                }
            }

            public class PushNotification : INotification
            {

                public void NotifyUser()
                {
                    // TODO Auto-generated method stub
                    Console.WriteLine("Sending a push notification");
                }
            }

            public class NotificationFactory
            {
                public INotification createNotification(String channel)
                {
                    if (channel == "SMS")
                    {
                        return new SMSNotification();
                    }
                    else if (channel == "EMAIL")
                    {
                        return new EmailNotification();
                    }
                    else if (channel == "PUSH")
                    {
                        return new PushNotification();
                    }
                    return null;
                }
            }
        }

    </details>

    <details>
    <summary><b>Factory Design Pattern realword example (Credit Card)</b></summary>
    <br>

    Run the following C# console application in visual studio or visual studio code, also you can run code in [online](https://code.sololearn.com/#cs)

        using System;
        using System.Collections.Generic;

        namespace FactoryDesignPattern
        {
            public class MainApp
            {
                static void Main(string[] args)
                {
                    string cardType = "MoneyBack";
                    CreditCard cardDetails = null;

                    if (cardType == "MoneyBack")
                    {
                        cardDetails = new MoneyBack();
                    }
                    else if (cardType == "Titanium")
                    {
                        cardDetails = new Titanium();
                    }
                    else if (cardType == "Platinum")
                    {
                        cardDetails = new Platinum();
                    }
                    if (cardDetails != null)
                    {
                        Console.WriteLine("CardType : " + cardDetails.GetCardType());
                        Console.WriteLine("CreditLimit : " + cardDetails.GetCreditLimit());
                        Console.WriteLine("AnnualCharge :" + cardDetails.GetAnnualCharge());
                    }
                    else
                    {
                        Console.Write("Invalid Card Type");
                    }
                    Console.ReadLine();
                }

            }

            public interface CreditCard
            {
                string GetCardType();
                int GetCreditLimit();
                int GetAnnualCharge();
            }

            class MoneyBack : CreditCard
            {
                public string GetCardType()
                {
                    return "MoneyBack";
                }
                public int GetCreditLimit()
                {
                    return 15000;
                }
                public int GetAnnualCharge()
                {
                    return 500;
                }
            }

            public class Titanium : CreditCard
            {
                public string GetCardType()
                {
                    return "Titanium Edge";
                }
                public int GetCreditLimit()
                {
                    return 25000;
                }
                public int GetAnnualCharge()
                {
                    return 1500;
                }
            }

            public class Platinum : CreditCard
            {
                public string GetCardType()
                {
                    return "Platinum Plus";
                }
                public int GetCreditLimit()
                {
                    return 35000;
                }
                public int GetAnnualCharge()
                {
                    return 2000;
                }
            }
        }

    After Factory Design Pattern

        using System;

        namespace FactoryDesignPattern
        {
            public class MainApp
            {
                static void Main(string[] args)
                {
                    CreditCard cardDetails = CreditCardFactory.GetCreditCard("Platinum");

                    if (cardDetails != null)
                    {
                        Console.WriteLine("CardType : " + cardDetails.GetCardType());
                        Console.WriteLine("CreditLimit : " + cardDetails.GetCreditLimit());
                        Console.WriteLine("AnnualCharge :" + cardDetails.GetAnnualCharge());
                    }
                    else
                    {
                        Console.Write("Invalid Card Type");
                    }
                    Console.ReadLine();
                }
            }

            class CreditCardFactory
            {
                public static CreditCard GetCreditCard(string cardType)
                {
                    CreditCard cardDetails = null;
                    if (cardType == "MoneyBack")
                    {
                        cardDetails = new MoneyBack();
                    }
                    else if (cardType == "Titanium")
                    {
                        cardDetails = new Titanium();
                    }
                    else if (cardType == "Platinum")
                    {
                        cardDetails = new Platinum();
                    }
                    return cardDetails;
                }
            }

            public interface CreditCard
            {
                string GetCardType();
                int GetCreditLimit();
                int GetAnnualCharge();
            }

            class MoneyBack : CreditCard
            {
                public string GetCardType()
                {
                    return "MoneyBack";
                }
                public int GetCreditLimit()
                {
                    return 15000;
                }
                public int GetAnnualCharge()
                {
                    return 500;
                }
            }

            public class Titanium : CreditCard
            {
                public string GetCardType()
                {
                    return "Titanium Edge";
                }
                public int GetCreditLimit()
                {
                    return 25000;
                }
                public int GetAnnualCharge()
                {
                    return 1500;
                }
            }

            public class Platinum : CreditCard
            {
                public string GetCardType()
                {
                    return "Platinum Plus";
                }
                public int GetCreditLimit()
                {
                    return 35000;
                }
                public int GetAnnualCharge()
                {
                    return 2000;
                }
            }
        }

    </details>

    **[⬆ Back to Top](#table-of-contents)**

3.  ### Factory Method Design Pattern

    Intent

    > Define an interface or abstract class for creating an object, but let the subclasses decide which class to instantiate. The Factory method lets a class defer instantiation it uses to subclasses.

    Let us simplify the above definition. The Factory Method Design Pattern is used, when we need to create the object (i.e. instance of the a class) without exposing the object creation logic to the client.

    Advantages

    - Factory Method Pattern allows the sub-classes to choose the type of objects to create.
    - It promotes the loose-coupling by eliminating the need to bind application-specific classes into the code. That means the code interacts solely with the resultant interface or abstract class, so that it will work with any classes that implement that interface or that extends that abstract class.

    We need to choose the Factory Method Design Pattern, when

    - A class doesn't know what sub-classes will be required to create
    - A class wants that its sub-classes specify the objects to be created.
    - The parent classes choose the creation of objects to its sub-classes.  
    <br>
    <details>
    <summary><b>Factory Method Design Pattern realword example (Notification)</b></summary>
    <br>

    <div  style="text-align: center;">
         <img src="https://github.com/saifaustcse/software-design-patterns/blob/main/images/factory-method-notification-brief.PNG?raw=true" width="600" height="300">
    <div>

    Run the following C# console application in visual studio or visual studio code, also you can run code in [online](https://code.sololearn.com/#cs)

        using System;

        namespace FactoryMethodDesignPattern
        {
            public class MainApp
            {
                static void Main()
                {
                    INotification notification = new SMSNotificationFactory().CreateObject();

                    if (notification != null)
                    {
                        notification.NotifyUser();
                    }
                    else
                    {
                        Console.Write("Invalid notification");
                    }
                    Console.ReadLine();
                }
            }


            public interface INotification
            {
                void NotifyUser();
            }

            public class SMSNotification : INotification
            {
                public void NotifyUser()
                {
                    // TODO Auto-generated method stub
                    Console.WriteLine("Sending an SMS notification");
                }
            }

            public class EmailNotification : INotification
            {
                public void NotifyUser()
                {
                    // TODO Auto-generated method stub
                    Console.WriteLine("Sending an EMAIL notification");
                }
            }

            public class PushNotification : INotification
            {
                public void NotifyUser()
                {
                    // TODO Auto-generated method stub
                    Console.WriteLine("Sending a push notification");
                }
            }

            public abstract class NotificationFactory
            {
                protected abstract INotification GetObject();
                public INotification CreateObject()
                {
                    return this.GetObject();
                }
            }

            public class SMSNotificationFactory : NotificationFactory
            {
                protected override INotification GetObject()
                {
                    SMSNotification notification = new SMSNotification();
                    return notification;
                }
            }


            public class EmailNotificationFactory : NotificationFactory
            {
                protected override INotification GetObject()
                {
                    EmailNotification notification = new EmailNotification();
                    return notification;
                }
            }


            public class PushNotificationFactory : NotificationFactory
            {
                protected override INotification GetObject()
                {
                    PushNotification notification = new PushNotification();
                    return notification;
                }
            }
        }

    </details>

    <details>
    <summary><b>Factory Method Pattern realword example (Credit Card)</b></summary>
    <br>

    Run the following C# console application in visual studio or visual studio code, also you can run code in [online](https://code.sololearn.com/#cs)

        using System;

        namespace FactoryDesignPattern
        {
            public class MainApp
            {
                static void Main(string[] args)
                {

                    CreditCard creditCard = new PlatinumFactory().CreateProduct();
                    if (creditCard != null)
                    {
                        Console.WriteLine("Card Type : " + creditCard.GetCardType());
                        Console.WriteLine("Credit Limit : " + creditCard.GetCreditLimit());
                        Console.WriteLine("Annual Charge :" + creditCard.GetAnnualCharge());
                    }
                    else
                    {
                        Console.Write("Invalid Card Type");
                    }
                    Console.WriteLine("--------------");
                    creditCard = new MoneyBackFactory().CreateProduct();
                    if (creditCard != null)
                    {
                        Console.WriteLine("Card Type : " + creditCard.GetCardType());
                        Console.WriteLine("Credit Limit : " + creditCard.GetCreditLimit());
                        Console.WriteLine("Annual Charge :" + creditCard.GetAnnualCharge());
                    }
                    else
                    {
                        Console.Write("Invalid Card Type");
                    }
                    Console.ReadLine();
                }
            }

            public interface CreditCard
            {
                string GetCardType();
                int GetCreditLimit();
                int GetAnnualCharge();
            }

            class MoneyBack : CreditCard
            {
                public string GetCardType()
                {
                    return "MoneyBack";
                }
                public int GetCreditLimit()
                {
                    return 15000;
                }
                public int GetAnnualCharge()
                {
                    return 500;
                }
            }

            public class Titanium : CreditCard
            {
                public string GetCardType()
                {
                    return "Titanium Edge";
                }
                public int GetCreditLimit()
                {
                    return 25000;
                }
                public int GetAnnualCharge()
                {
                    return 1500;
                }
            }

            public class Platinum : CreditCard
            {
                public string GetCardType()
                {
                    return "Platinum Plus";
                }
                public int GetCreditLimit()
                {
                    return 35000;
                }
                public int GetAnnualCharge()
                {
                    return 2000;
                }
            }

            public abstract class CreditCardFactory
            {
                protected abstract CreditCard MakeProduct();
                public CreditCard CreateProduct()
                {
                    return this.MakeProduct();
                }
            }

            public class MoneyBackFactory : CreditCardFactory
            {
                protected override CreditCard MakeProduct()
                {
                    CreditCard product = new MoneyBack();
                    return product;
                }
            }

            public class PlatinumFactory : CreditCardFactory
            {
                protected override CreditCard MakeProduct()
                {
                    CreditCard product = new Platinum();
                    return product;
                }
            }

            public class TitaniumFactory : CreditCardFactory
            {
                protected override CreditCard MakeProduct()
                {
                    CreditCard product = new Titanium();
                    return product;
                }
            }
        }

    </details>

    **[⬆ Back to Top](#table-of-contents)**

4.  ### Abstract Factory Design Pattern

    Intent

    > Encapsulate a group of individual factories that have a common theme without specifying their concrete classes.

    In simple words we can say, the Abstract Factory is a super factory that creates other factories. This Factory is also called Factory of Factories.

    Advantages

    - Abstract Factory Pattern isolates the client code from concrete (implementation) classes.
    - It eases the exchanging of object families.
    - It promotes consistency among objects.

    We need to choose the Abstract Factory Design Pattern, when

    - The system needs to be independent of how its object are created, composed, and represented.
    - The family of related objects has to be used together, then this constraint needs to be enforced.
    - We want to provide a library of objects that does not show implementations and only reveals interfaces.
    - The system needs to be configured with one of a multiple family of objects.

    <br>
    <details>
    <summary><b>Abstract Factory Design Pattern realword example ()</b></summary>
    <br>

    Run the following C# console application in visual studio or visual studio code, also you can run code in [online](https://code.sololearn.com/#cs)

        using System;

        namespace AbsFactoryMethodDesignPattern
        {

        }

    </details>

    <details>
    <summary><b>Abstract Factory Design Pattern realword example ()</b></summary>

    Run the following C# console application in visual studio or visual studio code, also you can run code in [online](https://code.sololearn.com/#cs)

        using System;

        namespace FactoryDesignPattern
        {
        }

    </details>

    **[⬆ Back to Top](#table-of-contents)**

5.  ### Builder Design Pattern

    Intent

    > Separate the construction of a complex object from its representation so that the same construction process can create different representations.
    > The Process of constructing a complex object should be generic so that the same construction process can be used to create different representations of the same complex object.

    In simple words we can say, the Builder Design Pattern is all about separating the construction process from its representation. When the construction process of your object is very complex then only you need to use to Builder Design Pattern

    Advantages

    - It provides clear separation between the construction and representation of an object.
    - It provides better control over construction process.
    - It supports to change the internal representation of objects.

    We need to choose the Builder Design Pattern, when

    - We want to make a complex object by specifying only its type and content. The built object is constructed from the details of its construction.
    - We decouple the process of building a complex object from the parts that make up the object.
    - We want to isolate the code for construction and representation.

    <br>
    <details>
    <summary><b>Builder Design Pattern real word example (Report Builder)</b></summary>
    <br>

    Run the following C# console application in visual studio or visual studio code, also you can run code in [online](https://code.sololearn.com/#cs)

        using System;

        namespace BuilderDesignPattern
        {
            class Program
            {
                static void Main()
                {

                    //// Calling process in details
                    //Report report;
                    //ReportDirector reportDirector = new ReportDirector();
                    //PDFReport pdfReport = new PDFReport();
                    //report = reportDirector.MakeReport(pdfReport);
                    //report.DisplayReport();

                    //Calling process in brief
                    ReportDirector reportDirector = new ReportDirector();
                    reportDirector.MakeReport(new PDFReport()).DisplayReport();
                    Console.WriteLine("--------------------------------");
                    reportDirector.MakeReport(new ExcelReport()).DisplayReport();
                    Console.ReadKey();
                }
            }

            public class Report
            {
                public string ReportType { get; set; }
                public string ReportHeader { get; set; }
                public string ReportFooter { get; set; }
                public string ReportContent { get; set; }
                public void DisplayReport()
                {
                    Console.WriteLine("Report Type :" + ReportType);
                    Console.WriteLine("Header :" + ReportHeader);
                    Console.WriteLine("Content :" + ReportContent);
                    Console.WriteLine("Footer :" + ReportFooter);
                }
            }

            public abstract class ReportBuilder
            {
                protected Report reportObject;
                public abstract void SetReportType();
                public abstract void SetReportHeader();
                public abstract void SetReportContent();
                public abstract void SetReportFooter();
                public void CreateNewReport()
                {
                    reportObject = new Report();
                }
                public Report GetReport()
                {
                    return reportObject;
                }
            }

            class ExcelReport : ReportBuilder
            {
                public override void SetReportContent()
                {
                    reportObject.ReportContent = "Excel Content Section";
                }
                public override void SetReportFooter()
                {
                    reportObject.ReportFooter = "Excel Footer";
                }
                public override void SetReportHeader()
                {
                    reportObject.ReportHeader = "Excel Header";
                }
                public override void SetReportType()
                {
                    reportObject.ReportType = "Excel";
                }
            }

            public class PDFReport : ReportBuilder
            {
                public override void SetReportContent()
                {
                    reportObject.ReportContent = "PDF Content Section";
                }
                public override void SetReportFooter()
                {
                    reportObject.ReportFooter = "PDF Footer";
                }
                public override void SetReportHeader()
                {
                    reportObject.ReportHeader = "PDF Header";
                }
                public override void SetReportType()
                {
                    reportObject.ReportType = "PDF";
                }
            }

            public class ReportDirector
            {
                public Report MakeReport(ReportBuilder reportBuilder)
                {
                    reportBuilder.CreateNewReport();
                    reportBuilder.SetReportType();
                    reportBuilder.SetReportHeader();
                    reportBuilder.SetReportContent();
                    reportBuilder.SetReportFooter();
                    return reportBuilder.GetReport();
                }
            }
        }

    </details>

    <details>
    <summary><b>Builder Design Pattern real word example (Beverage)</b></summary>
    <br>

    Run the following C# console application in visual studio or visual studio code, also you can run code in [online](https://code.sololearn.com/#cs)

        using System;

        namespace BuilderDesignPattern
        {
            public class MainApp
            {
                public static void Main()
                {
                    Beverage beverage;
                    BeverageDirector beverageDirector = new BeverageDirector();

                    TeaBuider tea = new TeaBuider();
                    beverage = beverageDirector.MakeBeverage(tea);
                    Console.WriteLine(beverage.ShowBeverage());
                    CoffeeBuilder coffee = new CoffeeBuilder();
                    beverage = beverageDirector.MakeBeverage(coffee);
                    Console.WriteLine(beverage.ShowBeverage());
                    Console.ReadKey();
                }
            }

            public class Beverage
            {
                public int Water { get; set; }
                public int Milk { get; set; }
                public int Sugar { get; set; }
                public int PowderQuantity { get; set; }
                public string BeverageName { get; set; }

                public string ShowBeverage()
                {
                    return String.Format("Hot {0} " +
                        "[{1} ml of water " +
                        "{2} ml of milk " +
                        "{3} gm of sugar " +
                        "{4} gm of {5}]\n",
                        BeverageName, Water, Milk, Sugar, PowderQuantity, BeverageName);
                }
            }

            public abstract class BeverageBuilder
            {
                protected Beverage beverage;

                public void CreateBeverage()
                {
                    beverage = new Beverage();
                }
                public Beverage GetBeverage()
                {
                    return beverage;
                }

                public abstract void SetBeverageType();
                public abstract void SetWater();
                public abstract void SetMilk();
                public abstract void SetSugar();
                public abstract void SetPowderQuantity();
            }


            public class CoffeeBuilder : BeverageBuilder
            {
                public override void SetWater()
                {
                    Console.WriteLine("Step 1 : Boiling water");
                    GetBeverage().Water = 40;
                }
                public override void SetMilk()
                {
                    Console.WriteLine("Step 2 : Adding milk");
                    GetBeverage().Milk = 50;
                }
                public override void SetSugar()
                {
                    Console.WriteLine("Step 3 : Adding Sugar");
                    GetBeverage().Sugar = 10;
                }
                public override void SetPowderQuantity()
                {
                    Console.WriteLine("Step 4 : Adding 15 Grams of coffee powder");
                    GetBeverage().PowderQuantity = 15;
                }
                public override void SetBeverageType()
                {
                    Console.WriteLine("Coffee");
                    GetBeverage().BeverageName = "Coffee";
                }
            }

            public class TeaBuider : BeverageBuilder
            {
                public override void SetWater()
                {
                    Console.WriteLine("Step 1 : Boiling water");
                    GetBeverage().Water = 50;
                }
                public override void SetMilk()
                {
                    Console.WriteLine("Step 2 : Adding milk");
                    GetBeverage().Milk = 60;
                }
                public override void SetSugar()
                {
                    Console.WriteLine("Step 3 : Adding Sugar");
                    GetBeverage().Sugar = 15;
                }
                public override void SetPowderQuantity()
                {
                    Console.WriteLine("Step 4 : Adding 20 Grams of coffee powder");
                    GetBeverage().PowderQuantity = 20;
                }
                public override void SetBeverageType()
                {
                    Console.WriteLine("Tea");
                    GetBeverage().BeverageName = "Tea";
                }
            }

            public class BeverageDirector
            {
                public Beverage MakeBeverage(BeverageBuilder beverageBuilder)
                {
                    beverageBuilder.CreateBeverage();
                    beverageBuilder.SetBeverageType();
                    beverageBuilder.SetWater();
                    beverageBuilder.SetMilk();
                    beverageBuilder.SetSugar();
                    beverageBuilder.SetPowderQuantity();

                    return beverageBuilder.GetBeverage();
                }
            }
        }

    </details>

    <details>
    <summary><b>Builder Design Pattern real word example (House)</b></summary>
    <br>

    Run the following C# console application in visual studio or visual studio code, also you can run code in [online](https://code.sololearn.com/#cs)

        using System;

        namespace BuilderDesignPattern
        {
            class Program
            {
                static void Main()
                {
                    CivilEngineer engineer = new CivilEngineer(new IglooHouseBuilder());
                    engineer.ConstructHouse();
                    House house = engineer.GetHouse();
                    Console.WriteLine("Igloo House Builder");
                    Console.WriteLine("--------------------");
                    Console.WriteLine("Basement: " + house.basement);
                    Console.WriteLine("Structure: " + house.structure);
                    Console.WriteLine("Roof: " + house.roof);
                    Console.WriteLine("Interior: " + house.interior);

                    Console.ReadKey();
                }
            }

            interface HousePlan
            {
                void SetBasement(String basement);
                void SetStructure(String structure);
                void SetRoof(String roof);
                void SetInterior(String interior);
            }

            class House : HousePlan
            {
                public String basement { get; private set; }
                public String structure { get; private set; }
                public String roof { get; private set; }
                public String interior { get; private set; }

                public void SetBasement(String basement)
                {
                    this.basement = basement;
                }

                public void SetStructure(String structure)
                {
                    this.structure = structure;
                }

                public void SetRoof(String roof)
                {
                    this.roof = roof;
                }

                public void SetInterior(String interior)
                {
                    this.interior = interior;
                }
            }


            interface HouseBuilder
            {
                void BuildBasement();
                void BuildStructure();
                void BulidRoof();
                void BuildInterior();
                House GetHouse();
            }

            class IglooHouseBuilder : HouseBuilder
            {
                private House house;

                public IglooHouseBuilder()
                {
                    this.house = new House();
                }

                public void BuildBasement()
                {
                    house.SetBasement("Ice Bars");
                }

                public void BuildStructure()
                {
                    house.SetStructure("Ice Blocks");
                }

                public void BuildInterior()
                {
                    house.SetInterior("Ice Carvings");
                }

                public void BulidRoof()
                {
                    house.SetRoof("Ice Dome");
                }

                public House GetHouse()
                {
                    return this.house;
                }
            }

            class TipiHouseBuilder : HouseBuilder
            {
                private House house;

                public TipiHouseBuilder()
                {
                    this.house = new House();
                }

                public void BuildBasement()
                {
                    house.SetBasement("Wooden Poles");
                }

                public void BuildStructure()
                {
                    house.SetStructure("Wood and Ice");
                }

                public void BuildInterior()
                {
                    house.SetInterior("Fire Wood");
                }

                public void BulidRoof()
                {
                    house.SetRoof("Wood, caribou and seal skins");
                }

                public House GetHouse()
                {
                    return this.house;
                }
            }

            class CivilEngineer
            {

                private HouseBuilder houseBuilder;

                public CivilEngineer(HouseBuilder houseBuilder)
                {
                    this.houseBuilder = houseBuilder;
                }

                public House GetHouse()
                {
                    return this.houseBuilder.GetHouse();
                }

                public void ConstructHouse()
                {
                    this.houseBuilder.BuildBasement();
                    this.houseBuilder.BuildStructure();
                    this.houseBuilder.BulidRoof();
                    this.houseBuilder.BuildInterior();
                }
            }
        }

    </details>

    <details>
    <summary><b>Builder Design Pattern real word example (Vehicle)</b></summary>
    <br>

    Run the following C# console application in visual studio or visual studio code, also you can run code in [online](https://code.sololearn.com/#cs)

        using System;
        using System.Collections.Generic;

        namespace BuilderDesignPattern
        {
        public class MainApp
        {

                public static void Main()
                {
                    VehicleBuilder builder;

                    // Create shop with vehicle builders

                    Shop shop = new Shop();

                    // Construct and display vehicles

                    builder = new ScooterBuilder();
                    shop.Construct(builder);
                    builder.Vehicle.Show();

                    builder = new CarBuilder();
                    shop.Construct(builder);
                    builder.Vehicle.Show();

                    builder = new MotorCycleBuilder();
                    shop.Construct(builder);
                    builder.Vehicle.Show();

                    // Wait for user

                    Console.ReadKey();
                }
            }

            class Shop
            {
                // Builder uses a complex series of steps

                public void Construct(VehicleBuilder vehicleBuilder)
                {
                    vehicleBuilder.BuildFrame();
                    vehicleBuilder.BuildEngine();
                    vehicleBuilder.BuildWheels();
                    vehicleBuilder.BuildDoors();
                }
            }


            abstract class VehicleBuilder

            {
                protected Vehicle vehicle;

                // Gets vehicle instance

                public Vehicle Vehicle
                {
                    get { return vehicle; }
                }

                // Abstract build methods

                public abstract void BuildFrame();
                public abstract void BuildEngine();
                public abstract void BuildWheels();
                public abstract void BuildDoors();
            }

            class MotorCycleBuilder : VehicleBuilder

            {
                public MotorCycleBuilder()
                {
                    vehicle = new Vehicle("MotorCycle");
                }

                public override void BuildFrame()
                {
                    vehicle["frame"] = "MotorCycle Frame";
                }

                public override void BuildEngine()
                {
                    vehicle["engine"] = "500 cc";
                }

                public override void BuildWheels()
                {
                    vehicle["wheels"] = "2";
                }

                public override void BuildDoors()
                {
                    vehicle["doors"] = "0";
                }
            }


            class CarBuilder : VehicleBuilder

            {
                public CarBuilder()
                {
                    vehicle = new Vehicle("Car");
                }

                public override void BuildFrame()
                {
                    vehicle["frame"] = "Car Frame";
                }

                public override void BuildEngine()
                {
                    vehicle["engine"] = "2500 cc";
                }

                public override void BuildWheels()
                {
                    vehicle["wheels"] = "4";
                }

                public override void BuildDoors()
                {
                    vehicle["doors"] = "4";
                }
            }

            class ScooterBuilder : VehicleBuilder

            {
                public ScooterBuilder()
                {
                    vehicle = new Vehicle("Scooter");
                }

                public override void BuildFrame()
                {
                    vehicle["frame"] = "Scooter Frame";
                }

                public override void BuildEngine()
                {
                    vehicle["engine"] = "50 cc";
                }

                public override void BuildWheels()
                {
                    vehicle["wheels"] = "2";
                }

                public override void BuildDoors()
                {
                    vehicle["doors"] = "0";
                }
            }


            class Vehicle
            {
                private string _vehicleType;
                private Dictionary<string, string> _parts =
                new Dictionary<string, string>();

                // Constructor

                public Vehicle(string vehicleType)
                {
                    this._vehicleType = vehicleType;
                }

                // Indexer

                public string this[string key]
                {
                    get { return _parts[key]; }
                    set { _parts[key] = value; }
                }

                public void Show()
                {
                    Console.WriteLine("\n---------------------------");
                    Console.WriteLine("Vehicle Type: {0}", _vehicleType);
                    Console.WriteLine(" Frame : {0}", _parts["frame"]);
                    Console.WriteLine(" Engine : {0}", _parts["engine"]);
                    Console.WriteLine(" #Wheels: {0}", _parts["wheels"]);
                    Console.WriteLine(" #Doors : {0}", _parts["doors"]);
                }
            }
        }

    </details>

    **[⬆ Back to Top](#table-of-contents)**

6.  ### Fluent Interface Design Pattern

    Intent

    > Bind properties of an object by implementing method chaining without having to re-specify the object name each time.

    The idea behind a fluent interface is that one can apply multiple properties to an object by connecting them with dots implemented by method cascading (concretely method chaining)

    C# uses fluent programming extensively in LINQ to build queries using the standard query operators. The implementation is based on extension methods

    Fluent code is much more readable and allows to vary a product’s internal representation

    What is Method Chaining?

    > Method chaining is a common technique where each method returns an object and all these methods can be chained together to form a single statement.

    Advantages

    - It

    We need to choose the Flyweight Design Pattern, when

    - Txt.

    <br>
    <details>
    <summary><b>Fluent Interface Design Pattern realword example (Employee)</b></summary>
    <br>

    Run the following C# console application in visual studio or visual studio code, also you can run code in [online](https://code.sololearn.com/#cs)

        using System;

        namespace FluentInterfaceDesignPattern
        {
            class Program
            {
                static void Main()
                {
                    FluentEmployee obj = new FluentEmployee();
                    obj.NameOfTheEmployee("Saiful Islam")
                            .Born("10/27/1991")
                            .WorkingOn("Software Engineer")
                            .StaysAt("Dahka-Bangladesh");

                    Employee emp=obj.GetEmploye();

                    Console.WriteLine("Name: " + emp.FullName);
                    Console.WriteLine("DateOfBirth: " + emp.DateOfBirth);
                    Console.WriteLine("Department: " + emp.Department);
                    Console.WriteLine("Address: " + emp.Address);
                    Console.Read();
                }
            }

            public class Employee
            {
                public string FullName { get; set; }
                public DateTime DateOfBirth { get; set; }
                public string Department { get; set; }
                public string Address { get; set; }
            }

            public class FluentEmployee
            {
                private Employee employee = new Employee();
                public FluentEmployee NameOfTheEmployee(string FullName)
                {
                    employee.FullName = FullName;
                    return this;
                }
                public FluentEmployee Born(string DateOfBirth)
                {
                    employee.DateOfBirth = Convert.ToDateTime(DateOfBirth);
                    return this;
                }
                public FluentEmployee WorkingOn(string Department)
                {
                    employee.Department = Department;
                    return this;
                }
                public FluentEmployee StaysAt(string Address)
                {
                    employee.Address = Address;
                    return this;
                }
                public Employee GetEmploye()
                {
                    return employee;
                }
            }
        }

    </details>

    **[⬆ Back to Top](#table-of-contents)**

7.  ### Prototype Design Pattern

    Intent

    > Create object based on an existing object through cloning.

    To simplify the above definition, we can say that, the Prototype Design Pattern gives us a way to create new objects from the existing instance of the object. That means it clone the existing object with its data into a new object. If we do any changes to the cloned object (i.e. new object) then it does not affect the original object.

    Advantages

    - It reduces the need of sub-classing.
    - It hides complexities of creating objects.
    - The clients can get new objects without knowing which type of object it will be.
    - It lets you add or remove objects at runtime

    We need to choose the Fluent Design Pattern, when

    - The classes are instantiated at runtime.
    - The cost of creating an object is expensive or complicated.
    - we want to keep the number of classes in an application minimum.
    - The client application needs to be unaware of object creation and representation.

    <br>
    <details>
    <summary><b>Prototype Design Pattern realword example (Employee)</b></summary>
    <br>

    Run the following C# console application in visual studio or visual studio code, also you can run code in [online](https://code.sololearn.com/#cs)

        using System;
        namespace PrototypeDesignPattern
        {
            class Program
            {
                static void Main()
                {
                    Employee emp1 = new Employee();
                    emp1.Name = "Hossain";
                    emp1.Department = "Accounts";
                    Employee emp2 = emp1;
                    emp2.Name = "Saiful";
                    emp2.Department = "Software";
                    Console.WriteLine("Emplpyee 1: ");
                    Console.WriteLine("Name: " + emp1.Name + ", Department: " + emp1.Department);
                    Console.WriteLine("Emplpyee 2: ");
                    Console.WriteLine("Name: " + emp2.Name + ", Department: " + emp2.Department);
                    Console.Read();
                }
            }
            public class Employee
            {
                public string Name { get; set; }
                public string Department { get; set; }
            }
        }

    After Prototype Design Pattern

        using System;
        namespace PrototypeDesignPattern
        {
            class Program
            {
                static void Main(string[] args)
                {

                    Employee emp1 = new Employee();
                    emp1.Name = "Hossain";
                    emp1.Department = "Software";

                    Employee emp2 = emp1.GetClone();
                    emp2.Name = "Saiful";

                    Console.WriteLine("Emplpyee 1: ");
                    Console.WriteLine("Name: " + emp1.Name + ", Department: " + emp1.Department);
                    Console.WriteLine("Emplpyee 2: ");
                    Console.WriteLine("Name: " + emp2.Name + ", Department: " + emp2.Department);
                    Console.Read();
                }
            }
            public class Employee
            {
                public string Name { get; set; }
                public string Department { get; set; }

                public Employee GetClone()
                {
                    return (Employee)this.MemberwiseClone();
                }
            }
        }

    </details>

    **[⬆ Back to Top](#table-of-contents)**

8.  ### Singleton-Design-Pattern

    Intent

    > Restricts the instantiation of a class to one object.

    Singleton Design Pattern ensures that only one object of a particular class is ever created.This is useful when exactly one object is needed to coordinate actions across the system.

    Advantages

    - Saves memory because object is not created at each request. Only single instance is reused again and again.

    Disadvantages

    - Unit testing is very difficult because it introduces a global state into an application.
    - It reduces the potential for parallelism within a program because to access the singleton instance in a multi-threaded environment, you need to serialize the object by using locking

    Singleton pattern is mostly used in multi-threaded and database applications. It is used in logging, caching, thread pools, configuration settings etc.

    - Service Proxies: As we know invoking a Service API is an extensive operation in an application. The process that taking most of the time is creating the Service client in order to invoke the service API. If you create the Service proxy as Singleton then it will improve the performance of your application.

    - Facades: You can also create Database connections as Singleton which can improve the performance of the application.

    - Logs: In an application, performing the I/O operation on a file is an expensive operation. If you create your Logger as Singleton then it will improve the performance of the I/O operation.

    - Data sharing: If you have any constant values or configuration values then you can keep these values in Singleton So that these can be read by other components of the application.

    - Caching: As we know fetching the data from a database is a time-consuming process. In your application, you can cache the master and configuration in memory which will avoid the DB calls. In such situations, the Singleton class can be used to handle the caching with thread synchronization in an efficient manner which drastically improves the performance of the application.

    <br>
    <details>
    <summary><b>Singleton Design Pattern realword example (Employee)</b></summary>
    <br>

    Run the following C# console application in visual studio or visual studio code, also you can run code in [online](https://code.sololearn.com/#cs)

        using System;
        namespace SingletonDemo
        {
            class Program
            {
                static void Main(string[] args)
                {
                    Singleton fromTeachaer = Singleton.GetInstance;
                    fromTeachaer.PrintDetails("From Teacher");
                    Singleton fromStudent = Singleton.GetInstance;
                    fromStudent.PrintDetails("From Student");
                    Console.ReadLine();
                }
            }

            public sealed class Singleton
            {
                private static int counter = 0;
                private static Singleton instance = null;
                public static Singleton GetInstance
                {
                    get
                    {
                        if (instance == null)
                            instance = new Singleton();
                        return instance;
                    }
                }

                private Singleton()
                {
                    counter++;
                    Console.WriteLine("Counter Value " + counter.ToString());
                }
                public void PrintDetails(string message)
                {
                    Console.WriteLine(message);
                }
            }
        }

    </details>

    **[⬆ Back to Top](#table-of-contents)**

9.  ### Adapter-Design-Pattern

    Intent

    > Allows the interface of an existing class to be used from another interface. It is often used to make existing classes work with others without modifying their source code.

    Advantages

    - Adapter Pattern helps two incompatible interfaces to work together.
    - It is often used to make existing classes work with others without modifying their source code.
    - It improves reusability of existing functionality.

    We need to choose the Adapter Design Pattern, when

    - A class needs to be reused that does not have an interface that a client requires.
    - A system needs to use classes of another system that is incompatible with it.
    - Allow communication between a new and already existing system that is independent of each other.

    <br>
    <details>
    <summary><b>Adapter Design Pattern Pattern realword example (Employee)</b></summary>
    <br>

    **Object Adapter Design Pattern realword example (Employee)**

    Run the following C# console application in visual studio or visual studio code, also you can run code in [online](https://code.sololearn.com/#cs)

        using System;
        using System.Collections.Generic;

        namespace AdapterDesignPattern
        {
            class Program
            {
                static void Main()
                {
                    string[,] employeesArray = new string[5, 4]
                    {
                        {"101","John","SE","10000"},
                        {"102","Smith","SE","20000"},
                        {"103","Dev","SSE","30000"},
                        {"104","Pam","SE","40000"},
                        {"105","Sara","SSE","50000"}
                    };

                    ITarget target = new EmployeeAdapter();
                    Console.WriteLine("HR system passes employee string array to Adapter\n");
                    target.ProcessCompanySalary(employeesArray);
                    Console.Read();
                }
            }

            public class Employee
            {
                public int ID { get; set; }
                public string Name { get; set; }
                public string Designation { get; set; }
                public decimal Salary { get; set; }
                public Employee(int id, string name, string designation, decimal salary)
                {
                    ID = id;
                    Name = name;
                    Designation = designation;
                    Salary = salary;
                }
            }
            public class ThirdPartyBillingSystem
            {
                //ThirdPartyBillingSystem accepts employees information as a List to process each employee salary
                public void ProcessSalary(List<Employee> listEmployee)
                {
                    foreach (Employee employee in listEmployee)
                    {
                        Console.WriteLine("Rs." + employee.Salary + " Salary Credited to " + employee.Name + " Account");
                    }
                }
            }

            public interface ITarget
            {
                void ProcessCompanySalary(string[,] employeesArray);
            }

            public class EmployeeAdapter : ITarget
            {
                ThirdPartyBillingSystem thirdPartyBillingSystem = new ThirdPartyBillingSystem();

                public void ProcessCompanySalary(string[,] employeesArray)
                {
                    string Id = null;
                    string Name = null;
                    string Designation = null;
                    string Salary = null;
                    List<Employee> listEmployee = new List<Employee>();
                    for (int i = 0; i < employeesArray.GetLength(0); i++)
                    {
                        for (int j = 0; j < employeesArray.GetLength(1); j++)
                        {
                            if (j == 0)
                            {
                                Id = employeesArray[i, j];
                            }
                            else if (j == 1)
                            {
                                Name = employeesArray[i, j];
                            }
                            else if (j == 1)
                            {
                                Designation = employeesArray[i, j];
                            }
                            else
                            {
                                Salary = employeesArray[i, j];
                            }
                        }
                        listEmployee.Add(new Employee(Convert.ToInt32(Id), Name, Designation, Convert.ToDecimal(Salary)));
                    }
                    Console.WriteLine("Adapter converted Array of Employee to List of Employee");
                    Console.WriteLine("Then delegate to the ThirdPartyBillingSystem for processing the employee salary\n");
                    thirdPartyBillingSystem.ProcessSalary(listEmployee);
                }
            }
        }

    <br>

    **Class Adapter Design Pattern realword example (Employee)**
    <br>
    Run the following C# console application in visual studio or visual studio code, also you can run code in [online](https://code.sololearn.com/#cs)

        using System;
        using System.Collections.Generic;

        namespace AdapterDesignPattern
        {
            class Program
            {
                static void Main()
                {
                    string[,] employeesArray = new string[5, 4]
                    {
                        {"101","John","SE","10000"},
                        {"102","Smith","SE","20000"},
                        {"103","Dev","SSE","30000"},
                        {"104","Pam","SE","40000"},
                        {"105","Sara","SSE","50000"}
                    };

                    ITarget target = new EmployeeAdapter();
                    Console.WriteLine("HR system passes employee string array to Adapter\n");
                    target.ProcessCompanySalary(employeesArray);
                    Console.Read();
                }
            }

            public class Employee
            {
                public int ID { get; set; }
                public string Name { get; set; }
                public string Designation { get; set; }
                public decimal Salary { get; set; }
                public Employee(int id, string name, string designation, decimal salary)
                {
                    ID = id;
                    Name = name;
                    Designation = designation;
                    Salary = salary;
                }
            }
            public class ThirdPartyBillingSystem
            {
                //ThirdPartyBillingSystem accepts employees information as a List to process each employee salary
                public void ProcessSalary(List<Employee> listEmployee)
                {
                    foreach (Employee employee in listEmployee)
                    {
                        Console.WriteLine("Rs." + employee.Salary + " Salary Credited to " + employee.Name + " Account");
                    }
                }
            }

            public interface ITarget
            {
                void ProcessCompanySalary(string[,] employeesArray);
            }

            public class EmployeeAdapter : ThirdPartyBillingSystem, ITarget
            {
                public void ProcessCompanySalary(string[,] employeesArray)
                {
                    string Id = null;
                    string Name = null;
                    string Designation = null;
                    string Salary = null;
                    List<Employee> listEmployee = new List<Employee>();
                    for (int i = 0; i < employeesArray.GetLength(0); i++)
                    {
                        for (int j = 0; j < employeesArray.GetLength(1); j++)
                        {
                            if (j == 0)
                            {
                                Id = employeesArray[i, j];
                            }
                            else if (j == 1)
                            {
                                Name = employeesArray[i, j];
                            }
                            else if (j == 1)
                            {
                                Designation = employeesArray[i, j];
                            }
                            else
                            {
                                Salary = employeesArray[i, j];
                            }
                        }
                        listEmployee.Add(new Employee(Convert.ToInt32(Id), Name, Designation, Convert.ToDecimal(Salary)));
                    }
                    Console.WriteLine("Adapter converted Array of Employee to List of Employee");
                    Console.WriteLine("Then delegate to the ThirdPartyBillingSystem for processing the employee salary\n");
                    ProcessSalary(listEmployee);
                }
            }
        }

    </details>

    **[⬆ Back to Top](#table-of-contents)**

10. ### Bridge Design Pattern

    Intent

    > Decouples an abstraction from its implementation so that the two can vary independently.

    Advantages

    - This pattern is used to separate an abstraction from its implementation so that both can be modified independently.
    - This pattern involves an interface which acts as a bridge between the abstraction class and implementer classes.
    - By decoupling an abstraction, With Bridge pattern both types of classes can be modified without affecting to each other.

    We need to use the Bridge Design Pattern, when

    - We want to avoid a tight coupling binding between an abstraction and its implementation.
    - We need both the abstractions and their implementations should be extensible by sub subclasses.
    - The changes in the implementation of an abstraction should have no impact on clients.
    - When we want to share an implementation among multiple objects
    - We want the selection or switching of the implementation is at runtime rather than design time.
    - Last but not the least when we want to hide the implementation of an abstraction completely from clients.

    <br>
    <details>
    <summary><b>Bridge Design Pattern Pattern realword example (shape)</b></summary>
    <br>

    <div  style="text-align: center;">
            <img src="https://github.com/saifaustcse/software-design-patterns/blob/main/images/before-bridge-design.png?raw=true" width="600" height="300">
    <div>

    <div  style="text-align: center;">
            <img src="https://github.com/saifaustcse/software-design-patterns/blob/main/images/after-bridge-design.png?raw=true" width="600" height="300">
    <div>

            using System;

            namespace BridgeDesignPattern
            {
                class Program
                {
                    static void Main(string[] args)
                    {
                        Shape redCircle = new Circle(100, 100, 10, new RedCircle());
                        Shape greenCircle = new Circle(100, 100, 10, new GreenCircle());

                        redCircle.draw();
                        greenCircle.draw();

                        Console.ReadKey();
                    }
                }

                public abstract class Shape
                {
                    protected DrawAPI drawAPI;

                    protected Shape(DrawAPI drawAPI)
                    {
                        this.drawAPI = drawAPI;
                    }
                    public abstract void draw();
                }

                public class Circle : Shape {
                private int x, y, radius;

                public Circle(int x, int y, int radius, DrawAPI drawAPI):base (drawAPI) {
                this.x = x;
                this.y = y;
                this.radius = radius;
                }

                public override void draw() {
                    drawAPI.drawCircle(radius,x,y);
                }
                }

                public class GreenCircle : DrawAPI {
                    public void drawCircle(int radius, int x, int y) {
                        Console.WriteLine("Drawing Circle[ color: green, radius: " + radius + ", x: " + x + ", " + y + "]");
                    }
                }

                public class RedCircle: DrawAPI {
                    public void drawCircle(int radius, int x, int y) {
                        Console.WriteLine("Drawing Circle[ color: red, radius: " + radius + ", x: " + x + ", " + y + "]");
                    }
                }

                public interface DrawAPI {
                void drawCircle(int radius, int x, int y);
                }
            }

    </details>

    <details>
    <summary><b>Bridge Design Pattern Pattern realword example (Payment method)</b></summary>
    <br>

            using System;

            namespace BridgeDesignPattern
            {

                class Program
                {
                    static void Main(string[] args)
                    {
                        Payment order = new CardPayment();
                        order._IPaymentSystem = new CitiPaymentSystem();
                        order.MakePayment();
                        order._IPaymentSystem = new IDBIPaymentSystem();
                        order.MakePayment();

                        order = new NetBankingPayment();
                        order._IPaymentSystem = new CitiPaymentSystem();
                        order.MakePayment();
                        order._IPaymentSystem = new IDBIPaymentSystem();
                        order.MakePayment();

                        Console.ReadKey();
                    }
                }


                public interface IPaymentSystem
                {
                    void ProcessPayment(string paymentSystem);
                }

                public class CitiPaymentSystem : IPaymentSystem
                {
                    public void ProcessPayment(string paymentSystem)
                    {
                        Console.WriteLine("Using CitiBank gateway for  " + paymentSystem);
                    }
                }

                public class IDBIPaymentSystem : IPaymentSystem
                {
                    public void ProcessPayment(string paymentSystem)
                    {
                        Console.WriteLine("Using IDBIBank gateway for  " + paymentSystem);
                    }
                }

                public abstract class Payment
                {
                    public IPaymentSystem _IPaymentSystem;
                    public abstract void MakePayment();
                }

                public class CardPayment : Payment
                {
                    public override void MakePayment()
                    {
                        _IPaymentSystem.ProcessPayment("Card Payment");
                    }
                }

                public class NetBankingPayment : Payment
                {
                    public override void MakePayment()
                    {
                        _IPaymentSystem.ProcessPayment("NetBanking Payment");
                    }
                }
            }

    </details>

    <details>
    <summary><b>Bridge Design Pattern Pattern realword example (Notification)</b></summary>
    <br>

            using System;

            namespace BridgeDesignPattern
            {
                class Program
                {
                    public static void Main()
                    {
                        try
                        {
                            Console.WriteLine("Select the Message Type 1. For longmessage or 2. For shortmessage");
                            int MessageType = Convert.ToInt32(Console.ReadLine());
                            Console.WriteLine("Please enter the message that you want to send");
                            string Message = Console.ReadLine();
                            if (MessageType == 1)
                            {
                                AbstractMessage longMessage = new LongMessage(new EmailMessageSender());
                                longMessage.SendMessage(Message);
                            }
                            else
                            {
                                AbstractMessage shortMessage = new ShortMessage(new SmsMessageSender());
                                shortMessage.SendMessage(Message);
                            }

                            Console.ReadKey();
                        }
                        catch (Exception e)
                        {
                            Console.WriteLine(e);
                        }
                    }

                    public interface IMessageSender
                    {
                        void SendMessage(string Message);
                    }

                    public class SmsMessageSender : IMessageSender
                    {
                        public void SendMessage(string Message)
                        {
                            Console.WriteLine("'" + Message + "'   : This Message has been sent using SMS");
                        }
                    }

                    public class EmailMessageSender : IMessageSender
                    {
                        public void SendMessage(string Message)
                        {
                            Console.WriteLine("'" + Message + "'   : This Message has been sent using Email");
                        }
                    }

                    public abstract class AbstractMessage
                    {
                        protected IMessageSender messageSender;
                        public abstract void SendMessage(string Message);
                    }

                    public class ShortMessage : AbstractMessage
                    {
                        public ShortMessage(IMessageSender messageSender)
                        {
                            this.messageSender = messageSender;
                        }
                        public override void SendMessage(string Message)
                        {
                            if (Message.Length <= 10)
                            {
                                messageSender.SendMessage(Message);
                            }
                            else
                            {
                                Console.WriteLine("Unable to send the message as length > 10 characters");
                            }
                        }
                    }

                    public class LongMessage : AbstractMessage
                    {
                        public LongMessage(IMessageSender messageSendor)
                        {
                            this.messageSender = messageSendor;
                        }
                        public override void SendMessage(string Message)
                        {
                            messageSender.SendMessage(Message);
                        }
                    }
                }
            }

    </details>

    <details>
    <summary><b>Bridge Design Pattern Pattern realword example (Remote Control)</b></summary>
    <br>

    Run the following C# console application in visual studio or visual studio code, also you can run code in [online](https://code.sololearn.com/#cs)

        using System;

        namespace BridgeDesignPattern
        {
            class Program
            {
                public static void Main()
                {
                    try
                    {
                        SonyRemoteControl sonyRemoteControl = new SonyRemoteControl(new SonyLedTv());
                        sonyRemoteControl.SwitchOn();
                        sonyRemoteControl.SetChannel(101);
                        sonyRemoteControl.SwitchOff();

                        Console.WriteLine();
                        SamsungRemoteControl samsungRemoteControl = new SamsungRemoteControl(new SamsungLedTv());
                        samsungRemoteControl.SwitchOn();
                        samsungRemoteControl.SetChannel(202);
                        samsungRemoteControl.SwitchOff();
                        Console.ReadKey();
                    }
                    catch (Exception e)
                    {
                        Console.WriteLine(e);
                    }
                }

                public interface LEDTV
                {
                    void SwitchOn();
                    void SwitchOff();
                    void SetChannel(int channelNumber);
                }

                public class SamsungLedTv : LEDTV
                {
                    public void SwitchOn()
                    {
                        Console.WriteLine("Turning ON : Samsung TV");
                    }
                    public void SwitchOff()
                    {
                        Console.WriteLine("Turning OFF : Samsung TV");
                    }
                    public void SetChannel(int channelNumber)
                    {
                        Console.WriteLine("Setting channel Number " + channelNumber + " on Samsung TV");
                    }
                }

                public class SonyLedTv : LEDTV
                {
                    public void SwitchOn()
                    {
                        Console.WriteLine("Turning ON : Sony TV");
                    }
                    public void SwitchOff()
                    {
                        Console.WriteLine("Turning OFF : Sony TV");
                    }
                    public void SetChannel(int channelNumber)
                    {
                        Console.WriteLine("Setting channel Number " + channelNumber + " on Sony TV");
                    }
                }

                public abstract class AbstractRemoteControl
                {
                    protected LEDTV ledTv;
                    protected AbstractRemoteControl(LEDTV ledTv)
                    {
                        this.ledTv = ledTv;
                    }
                    public abstract void SwitchOn();
                    public abstract void SwitchOff();
                    public abstract void SetChannel(int channelNumber);
                }

                public class SamsungRemoteControl : AbstractRemoteControl
                {
                    public SamsungRemoteControl(LEDTV ledTv) : base(ledTv)
                    {
                    }

                    public override void SwitchOn()
                    {
                        ledTv.SwitchOn();
                    }
                    public override void SwitchOff()
                    {
                        ledTv.SwitchOff();
                    }
                    public override void SetChannel(int channelNumber)
                    {
                        ledTv.SetChannel(channelNumber);
                    }
                }

                public class SonyRemoteControl : AbstractRemoteControl
                {
                    public SonyRemoteControl(LEDTV ledTv) : base(ledTv)
                    {
                    }
                    public override void SwitchOn()
                    {
                        ledTv.SwitchOn();
                    }
                    public override void SwitchOff()
                    {
                        ledTv.SwitchOff();
                    }
                    public override void SetChannel(int channelNumber)
                    {
                        ledTv.SetChannel(channelNumber);
                    }
                }
            }
        }

    </details>

    **[⬆ Back to Top](#table-of-contents)**

11. ### Composite Design Pattern

    Intent

    > Compose objects into tree structure to represent part-whole hierarchies. Composite lets client treat individual objects and compositions of objects uniformly

    This means, the composite pattern describes a group of objects that is treated the same way as a single instance of the same type of object.

    Advantages

    - It defines class hierarchies that contain primitive and complex objects.
    - It makes easier to you to add new kinds of components.
    - It provides flexibility of structure with manageable class or interface.

    We need to use the Composite Design Pattern, when

    - Represent part-whole hierarchies of objects.
    - Clients to ignore the difference between compositions of objects and individual objects.

    <br>
    <details>
    <summary><b>Composite Design Pattern Pattern realword example (Computer)</b></summary>
    <br>

    Run the following C# console application in visual studio or visual studio code, also you can run code in [online](https://code.sololearn.com/#cs)

        using System;
        using System.Collections.Generic;

        namespace CompositeDesignPattern
        {
            class Program
            {
                public static void Main()
                {
                    try
                    {
                        //Creating Leaf Objects
                        IComponent hardDisk = new Leaf("Hard Disk", 2000);
                        IComponent ram = new Leaf("RAM", 3000);
                        IComponent cpu = new Leaf("CPU", 2000);
                        IComponent mouse = new Leaf("Mouse", 2000);
                        IComponent keyboard = new Leaf("Keyboard", 2000);
                        //Creating composite objects
                        Composite motherBoard = new Composite("Peripherals");
                        Composite cabinet = new Composite("Cabinet");
                        Composite peripherals = new Composite("Peripherals");
                        Composite computer = new Composite("Computer");
                        //Creating tree structure
                        //Ading CPU and RAM in Mother board
                        motherBoard.AddComponent(cpu);
                        motherBoard.AddComponent(ram);
                        //Ading mother board and hard disk in Cabinet
                        cabinet.AddComponent(motherBoard);
                        cabinet.AddComponent(hardDisk);
                        //Ading mouse and keyborad in peripherals
                        peripherals.AddComponent(mouse);
                        peripherals.AddComponent(keyboard);
                        //Ading cabinet and peripherals in computer
                        computer.AddComponent(cabinet);
                        computer.AddComponent(peripherals);
                        //To display the Price of Computer
                        computer.DisplayPrice();
                        Console.WriteLine();
                        //To display the Price of Keyboard
                        keyboard.DisplayPrice();
                        Console.WriteLine();
                        //To display the Price of Cabinet
                        cabinet.DisplayPrice();

                        Console.ReadKey();
                    }
                    catch (Exception e)
                    {
                        Console.WriteLine(e);
                    }
                }

                public interface IComponent
                {
                    void DisplayPrice();
                }

                public class Leaf : IComponent
                {
                    public int Price { get; set; }
                    public string Name { get; set; }
                    public Leaf(string name, int price)
                    {
                        this.Price = price;
                        this.Name = name;
                    }

                    public void DisplayPrice()
                    {
                        Console.WriteLine(Name + " : " + Price);
                    }
                }

                public class Composite : IComponent
                {
                    public string Name { get; set; }
                    List<IComponent> components = new List<IComponent>();
                    public Composite(string name)
                    {
                        this.Name = name;
                    }
                    public void AddComponent(IComponent component)
                    {
                        components.Add(component);
                    }

                    public void DisplayPrice()
                    {
                        Console.WriteLine(Name);
                        foreach (var item in components)
                        {
                            item.DisplayPrice();
                        }
                    }
                }
            }
        }

    </details>

    <details>
    <summary><b>Composite Design Pattern realword example (Emaployee)</b></summary>
    <br>

    Run the following C# console application in visual studio or visual studio code, also you can run code in [online](https://code.sololearn.com/#cs)

        using System;
        using System.Collections.Generic;

        namespace CompositeDesignPattern
        {
            class Program
            {
                public static void Main()
                {
                    //Arrange Employees, Organization and add employees
                    var developer = new Developer("John", 5000);
                    var designer = new Designer("Arya", 5000);

                    var organization = new Organization();
                    organization.AddEmployee(developer);
                    organization.AddEmployee(designer);

                    Console.WriteLine("Net Salary of Employees in Organization is ${0}", organization.GetNetSalaries());
                    Console.Read();
                }
            }

            interface IEmployee
            {
                float GetSalary();
                string GetRole();
                string GetName();
            }


            class Developer : IEmployee
            {
                private string mName;
                private float mSalary;

                public Developer(string name, float salary)
                {
                    this.mName = name;
                    this.mSalary = salary;
                }

                public float GetSalary()
                {
                    return this.mSalary;
                }

                public string GetRole()
                {
                    return "Developer";
                }

                public string GetName()
                {
                    return this.mName;
                }
            }

            class Designer : IEmployee
            {
                private string mName;
                private float mSalary;

                public Designer(string name, float salary)
                {
                    this.mName = name;
                    this.mSalary = salary;
                }

                public float GetSalary()
                {
                    return this.mSalary;
                }

                public string GetRole()
                {
                    return "Designer";
                }

                public string GetName()
                {
                    return this.mName;
                }
            }

            class Organization
            {
                protected List<IEmployee> employees;

                public Organization()
                {
                    employees = new List<IEmployee>();
                }

                public void AddEmployee(IEmployee employee)
                {
                    employees.Add(employee);
                }

                public float GetNetSalaries()
                {
                    float netSalary = 0;

                    foreach (var e in employees)
                    {
                        netSalary += e.GetSalary();
                    }
                    return netSalary;
                }
            }
        }

    </details>

    **[⬆ Back to Top](#table-of-contents)**

12. ### Decorator Design Pattern

    Intent

    > Allows to add new functionalities dynamically to an existing object, without affecting the behavior of other objects from the same class.

    In other words, The Decorator Pattern uses composition instead of inheritance to extend the functionality of an object at runtime.

    Advantages

    - It provides greater flexibility than static inheritance.
    - It enhances the extensibility of the object, because changes are made by coding new classes.
    - It simplifies the coding by allowing you to develop a series of functionality from targeted classes instead of coding all of the behavior into the object.

    We need to use the Decorator Design Pattern, when

    - We want to add new functionalities to existing objects dynamically without affecting the behavior of other objects from the same class.
    - A class definition may be hidden or otherwise unavailable for subclasses.

    <br>
    <details>
    <summary><b>Decorator Design Pattern Pattern realword example (Car)</b></summary>
    <br>

    Run the following C# console application in visual studio or visual studio code, also you can run code in [online](https://code.sololearn.com/#cs)

        using System;
        using System.Collections.Generic;

        namespace DecoratorDesignPattern
        {
            class Program
            {
                public static void Main()
                {
                    ICar car = new Suzuki();
                    CarDecorator decorator = new OfferPrice(car);
                    Console.WriteLine(string.Format("Make :{0}  Price:{1} " +
                        "DiscountPrice : {2}"
                        , decorator.Make, decorator.GetPrice().ToString(),
                        decorator.GetDiscountedPrice().ToString()));
                    Console.ReadLine();
                    Console.Read();
                }
            }

            public interface ICar
            {
                string Make { get; }
                double GetPrice();
            }

            public sealed class Hyndai : ICar
            {
                public string Make
                {
                    get { return "HatchBack"; }
                }
                public double GetPrice()
                {
                    return 800000;
                }
            }


            public sealed class Suzuki : ICar
            {
                public string Make
                {
                    get { return "Sedan"; }
                }
                public double GetPrice()
                {
                    return 1000000;
                }
            }


            public abstract class CarDecorator : ICar
            {
                private ICar car;
                public CarDecorator(ICar Car)
                {
                    car = Car;
                }
                public string Make { get { return car.Make; } }

                public double GetPrice()
                {
                    return car.GetPrice();
                }
                public abstract double GetDiscountedPrice();
            }

            public class OfferPrice : CarDecorator
            {
                public OfferPrice(ICar car) : base(car)
                {
                }
                public override double GetDiscountedPrice()
                {
                    return .8 * base.GetPrice();
                }
            }
        }

    </details>

    <details>
    <summary><b>Decorator Design Pattern Pattern realword example (Car)</b></summary>
    <br>

    Run the following C# console application in visual studio or visual studio code, also you can run code in [online](https://code.sololearn.com/#cs)

        using System;
        using System.Collections.Generic;

        namespace DecoratorDesignPattern
        {
            class Program
            {
                public static void Main()
                {
                    try
                    {
                        ICar bmwCar1 = new BMWCar();
                        bmwCar1.ManufactureCar();
                        Console.WriteLine(bmwCar1 + "\n");
                        DieselCarDecorator carWithDieselEngine = new DieselCarDecorator(bmwCar1);
                        carWithDieselEngine.ManufactureCar();
                        Console.WriteLine();
                        ICar bmwCar2 = new BMWCar();
                        PetrolCarDecorator carWithPetrolEngine = new PetrolCarDecorator(bmwCar2);
                        carWithPetrolEngine.ManufactureCar();
                        Console.ReadKey();

                        Console.ReadKey();
                    }
                    catch (Exception e)
                    {
                        Console.WriteLine(e);
                    }
                }

                public interface ICar
                {
                    ICar ManufactureCar();
                }

                public class BMWCar : ICar
                {
                    private string CarName = "BMW";
                    public string CarBody { get; set; }
                    public string CarDoor { get; set; }
                    public string CarWheels { get; set; }
                    public string CarGlass { get; set; }
                    public string Engine { get; set; }
                    public override string ToString()
                    {
                        return "BMWCar [CarName=" + CarName + ", CarBody=" + CarBody + ", CarDoor=" + CarDoor + ", CarWheels="
                                        + CarWheels + ", CarGlass=" + CarGlass + ", Engine=" + Engine + "]";
                    }
                    public ICar ManufactureCar()
                    {
                        CarBody = "carbon fiber material";
                        CarDoor = "4 car doors";
                        CarWheels = "6 car glasses";
                        CarGlass = "4 MRF wheels";
                        return this;
                    }
                }

                public abstract class CarDecorator : ICar
                {
                    protected ICar car;
                    public CarDecorator(ICar car)
                    {
                        this.car = car;
                    }
                    public virtual ICar ManufactureCar()
                    {
                        return car.ManufactureCar();
                    }
                }

                public class DieselCarDecorator : CarDecorator
                {
                    public DieselCarDecorator(ICar car) : base(car)
                    {
                    }
                    public override ICar ManufactureCar()
                    {
                        car.ManufactureCar();
                        AddEngine(car);
                        return car;
                    }
                    public void AddEngine(ICar car)
                    {
                        if (car is BMWCar)
                        {
                            BMWCar BMWCar = (BMWCar)car;
                            BMWCar.Engine = "Diesel Engine";
                            Console.WriteLine("DieselCarDecorator added Diesel Engine to the Car : " + car);
                        }
                    }
                }
                class PetrolCarDecorator : CarDecorator
                {
                    public PetrolCarDecorator(ICar car) : base(car)
                    {
                    }
                    public override ICar ManufactureCar()
                    {
                        car.ManufactureCar();
                        car.ManufactureCar();
                        AddEngine(car);
                        return car;
                    }
                    public void AddEngine(ICar car)
                    {
                        if (car is BMWCar)
                        {
                            BMWCar BMWCar = (BMWCar)car;
                            BMWCar.Engine = "Petrol Engine";
                            Console.WriteLine("PetrolCarDecorator added Petrol Engine to the Car : " + car);
                        }
                    }
                }
            }
        }

    </details>

    <details>
    <summary><b>Decorator Design Pattern Pattern realword example (Pizza)</b></summary>
    <br>

    Run the following C# console application in visual studio or visual studio code, also you can run code in [online](https://code.sololearn.com/#cs)

        using System;
        using System.Collections.Generic;

        namespace DecoratorDesignPattern
        {
            class Program
            {
                public static void Main()
                {
                    try
                    {
                        PlainPizza plainPizzaObj = new PlainPizza();
                        string plainPizza = plainPizzaObj.MakePizza();
                        Console.WriteLine(plainPizza);
                        PizzaDecorator chickenPizzaDecorator = new ChickenPizzaDecorator(plainPizzaObj);
                        string chickenPizza = chickenPizzaDecorator.MakePizza();
                        Console.WriteLine("\n'" + chickenPizza + "' using ChickenPizzaDecorator");
                        VegPizzaDecorator vegPizzaDecorator = new VegPizzaDecorator(plainPizzaObj);
                        string vegPizza = vegPizzaDecorator.MakePizza();
                        Console.WriteLine("\n'" + vegPizza + "' using VegPizzaDecorator");

                        Console.ReadKey();
                    }
                    catch (Exception e)
                    {
                        Console.WriteLine(e);
                    }
                }

                public interface Pizza
                {
                    string MakePizza();
                }

                public class PlainPizza : Pizza
                {
                    public string MakePizza()
                    {
                        return "Plain Pizza";
                    }
                }

                public abstract class PizzaDecorator : Pizza
                {
                    protected Pizza pizza;
                    public PizzaDecorator(Pizza pizza)
                    {
                        this.pizza = pizza;
                    }
                    public virtual string MakePizza()
                    {
                        return pizza.MakePizza();
                    }
                }

                public class ChickenPizzaDecorator : PizzaDecorator
                {
                    public ChickenPizzaDecorator(Pizza pizza) : base(pizza)
                    {
                    }
                    public override string MakePizza()
                    {
                        return pizza.MakePizza() + AddChicken();
                    }
                    private string AddChicken()
                    {
                        return ", Chicken added";
                    }
                }

                public class VegPizzaDecorator : PizzaDecorator
                {
                    public VegPizzaDecorator(Pizza pizza) : base(pizza)
                    {
                    }
                    public override string MakePizza()
                    {
                        return pizza.MakePizza() + AddVegetables();
                    }
                    private string AddVegetables()
                    {
                        return ", Vegetables added";
                    }
                }
            }
        }

    </details>

    <details>
    <summary><b>Decorator Design Pattern Pattern realword example (Coffee)</b></summary>
    <br>

    Run the following C# console application in visual studio or visual studio code, also you can run code in [online](https://code.sololearn.com/#cs)

        using System;
        using System.Collections.Generic;

        namespace DecoratorDesignPattern
        {
            class Program
            {
                public static void Main()
                {
                    var myCoffee = new SimpleCoffee();
                    Console.WriteLine("********************");
                    Console.WriteLine(myCoffee.GetCost()); // $ 5.00
                    Console.WriteLine(myCoffee.GetDescription()); // Simple Coffee

                    var milkCoffee = new MilkCoffee(myCoffee);
                    Console.WriteLine("********************");
                    Console.WriteLine(milkCoffee.GetCost()); // $ 6.00
                    Console.WriteLine(milkCoffee.GetDescription()); // Simple Coffee, milk

                    var whipCoffee = new WhipCoffee(milkCoffee);
                    Console.WriteLine("********************");
                    Console.WriteLine(whipCoffee.GetCost()); // $ 7.00
                    Console.WriteLine(whipCoffee.GetDescription()); // Simple Coffee, milk, whip

                    var vanillaCoffee = new VanillaCoffee(whipCoffee);
                    Console.WriteLine("********************");
                    Console.WriteLine(vanillaCoffee.GetCost()); // $ 8.00
                    Console.WriteLine(vanillaCoffee.GetDescription()); // Simple Coffee, milk, whip, vanilla
                    Console.Read();
                }
            }

            interface ICoffee
            {
                int GetCost();
                string GetDescription();
            }

            class SimpleCoffee : ICoffee
            {
                public int GetCost()
                {
                    return 5;
                }

                public string GetDescription()
                {
                    return "Simple Coffee";
                }
            }

            class MilkCoffee : ICoffee
            {
                private readonly ICoffee mCoffee;

                public MilkCoffee(ICoffee coffee)
                {
                    if (coffee == null)
                    {
                        throw new ArgumentNullException("coffee", "coffee should not be null");
                    }
                    else
                    {
                        mCoffee = coffee;
                    }
                }
                public int GetCost()
                {
                    return mCoffee.GetCost() + 1;
                }

                public string GetDescription()
                {
                    return String.Concat(mCoffee.GetDescription(), ", milk");
                }
            }

            class WhipCoffee : ICoffee
            {
                private readonly ICoffee wCoffee;

                public WhipCoffee(ICoffee coffee)
                {
                    if (coffee == null)
                    {
                        throw new ArgumentNullException("coffee", "coffee should not be null");
                    }
                    else
                    {
                        wCoffee = coffee;
                    }
                }
                public int GetCost()
                {
                    return wCoffee.GetCost() + 1;
                }

                public string GetDescription()
                {
                    return String.Concat(wCoffee.GetDescription(), ", whip");
                }
            }

            class VanillaCoffee : ICoffee
            {
                private readonly ICoffee vCoffee;

                public VanillaCoffee(ICoffee coffee)
                {
                    if (coffee == null)
                    {
                        throw new ArgumentNullException("coffee", "coffee should not be null");
                    }
                    else
                    {
                        vCoffee = coffee;
                    }
                }
                public int GetCost()
                {
                    return vCoffee.GetCost() + 1;
                }

                public string GetDescription()
                {
                    return String.Concat(vCoffee.GetDescription(), ", vanilla");
                }
            }
        }

    </details>

    **[⬆ Back to Top](#table-of-contents)**

13. ### Facade Design Pattern

    **What does Facade mean?**

    A false appearance that makes someone or something seem more pleasant or better than they really are: He kept his hostility hidden behind a friendly

    Intent

    > Provide a unified and simplified interface to a set of interfaces in a subsystem, therefore it hides the complexities of the subsystem from the client

    Advantages

    - It shields the clients from the complexities of the sub-system components.
    - It promotes loose coupling between subsystems and its clients.

    We need to choose the Facade Design Pattern, when

    - We want to provide simple interface to a complex sub-system.
    - Several dependencies exist between clients and the implementation classes of an abstraction.

    <br>
    <details>
    <summary><b>Facade Design Pattern Pattern realword example (Employee)</b></summary>
    <br>

    Run the following C# console application in visual studio or visual studio code, also you can run code in [online](https://code.sololearn.com/#cs)

        using System;

        namespace FacadeDesignPattern
        {
            class Program
            {
                public static void Main()
                {
                    try
                    {
                        Order order = new Order();
                        order.PlaceOrder();
                        Console.ReadKey();
                    }
                    catch (Exception e)
                    {
                        Console.WriteLine(e);
                    }
                }

                public class Product
                {
                    public void GetProductDetails()
                    {
                        Console.WriteLine("Fetching the Product Details");
                    }
                }

                public class Payment
                {
                    public void MakePayment()
                    {
                        Console.WriteLine("Payment Done Successfully");
                    }
                }

                public class Invoice
                {
                    public void Sendinvoice()
                    {
                        Console.WriteLine("Invoice Send Successfully");
                    }
                }

                public class Order
                {
                    public void PlaceOrder()
                    {
                        Console.WriteLine("Place Order Started");
                        Product product = new Product();
                        product.GetProductDetails();
                        Payment payment = new Payment();
                        payment.MakePayment();
                        Invoice invoice = new Invoice();
                        invoice.Sendinvoice();
                        Console.WriteLine("Order Placed Successfully");
                    }
                }
            }
        }

    </details>

    **[⬆ Back to Top](#table-of-contents)**

14. ### Flyweight Design Pattern

    Intent

    > Reduce the number of objects creation and minimize memory usages and increase performance by

    reusing already existing similar objects

    Advantages

    - It reduces the number of objects.
    - It reduces the amount of memory and storage devices required if the objects are persisted

    We need to choose the Flyweight Design Pattern, when

    - An application uses number of objects
    - The storage cost is high because of the quantity of objects.
    - The application does not depend on object identity.

    <br>
    <details>
    <summary><b>Flyweight Design Pattern Pattern realword example (Shape)</b></summary>
    <br>

    Run the following C# console application in visual studio or visual studio code, also you can run code in [online](https://code.sololearn.com/#cs)

        using System;
        using System.Collections.Generic;

        namespace FlyweightDesignPattern
        {
            class Program
            {
                public static void Main()
                {
                    try
                    {
                        Console.WriteLine("\n Red color Circles ");
                        for (int i = 0; i < 3; i++)
                        {
                            Circle circle = (Circle)ShapeFactory.GetShape("circle");
                            circle.SetColor("Red");
                            circle.Draw();
                        }
                        Console.WriteLine("\n Green color Circles ");
                        for (int i = 0; i < 3; i++)
                        {
                            Circle circle = (Circle)ShapeFactory.GetShape("circle");
                            circle.SetColor("Green");
                            circle.Draw();
                        }
                        Console.WriteLine("\n Blue color Circles");
                        for (int i = 0; i < 3; ++i)
                        {
                            Circle circle = (Circle)ShapeFactory.GetShape("circle");
                            circle.SetColor("Green");
                            circle.Draw();
                        }
                        Console.WriteLine("\n Orange color Circles");
                        for (int i = 0; i < 3; ++i)
                        {
                            Circle circle = (Circle)ShapeFactory.GetShape("circle");
                            circle.SetColor("Orange");
                            circle.Draw();
                        }
                        Console.WriteLine("\n Black color Circles");
                        for (int i = 0; i < 3; ++i)
                        {
                            Circle circle = (Circle)ShapeFactory.GetShape("circle");
                            circle.SetColor("Black");
                            circle.Draw();
                        }

                        Console.ReadKey();
                    }
                    catch (Exception e)
                    {
                        Console.WriteLine(e);
                    }
                }

                public interface Shape
                {
                    void Draw();
                }

                public class Circle : Shape
                {
                    public string Color { get; set; }
                    private int XCor = 10;
                    private int YCor = 20;
                    private int Radius = 30;

                    public void SetColor(string Color)
                    {
                        this.Color = Color;
                    }
                    public void Draw()
                    {
                        Console.WriteLine(" Circle: Draw() [Color : " + Color + ", X Cor : " + XCor + ", YCor :" + YCor + ", Radius :"
                                + Radius);
                    }
                }

                public class ShapeFactory
                {
                    private static Dictionary<string, Shape> shapeMap = new Dictionary<string, Shape>();
                    public static Shape GetShape(string shapeType)
                    {
                        Shape shape = null;
                        if (shapeType.Equals("circle", StringComparison.InvariantCultureIgnoreCase))
                        {
                            if (shapeMap.TryGetValue("circle", out shape))
                            {
                            }
                            else
                            {
                                shape = new Circle();
                                shapeMap.Add("circle", shape);
                                Console.WriteLine(" Creating circle object with out any color in shapefactory \n");
                            }
                        }
                        return shape;
                    }
                }
            }
        }

    </details>

    **[⬆ Back to Top](#table-of-contents)**

15. ### Proxy Design Pattern

    **What does Proxy mean?**

    A agency, function, or office of a deputy who acts as a substitute for another

    Intent

    > Provide a substitute or placeholder for another object to control access to it.

    Advantages

    - It provides the protection to the original object from the outside world.

    We need to choose the Flyweight Design Pattern, when

    - Adding security access to an existing object. The proxy will determine if the client can access the object of interest.
    - Simplifying the API of a complex object. The proxy can provide a simple API so that the client code does not have to deal with the complexity of the object of interest.
    - Providing interfaces for remote resources such as web service or REST resources.
    - Coordinating expensive operations on remote resources by asking the remote resources to start the operation as soon as possible before accessing the resources.
    - Adding a thread-safe feature to an existing class without changing the existing class code.

    <br>
    <details>
    <summary><b>Proxy Design Pattern Pattern realword example (Employee)</b></summary>
    <br>

    Run the following C# console application in visual studio or visual studio code, also you can run code in [online](https://code.sololearn.com/#cs)

        using System;
        using System.Collections.Generic;

        namespace ProxyDesignPattern
        {
            class Program
            {
                public static void Main()
                {
                    try
                    {
                        Console.WriteLine("Client passing employee with Role Developer to folderproxy");
                        Employee emp1 = new Employee("Anurag", "Anurag123", "Developer");
                        SharedFolderProxy folderProxy1 = new SharedFolderProxy(emp1);
                        folderProxy1.PerformRWOperations();
                        Console.WriteLine();
                        Console.WriteLine("Client passing employee with Role Manager to folderproxy");
                        Employee emp2 = new Employee("Pranaya", "Pranaya123", "Manager");
                        SharedFolderProxy folderProxy2 = new SharedFolderProxy(emp2);
                        folderProxy2.PerformRWOperations();

                        Console.ReadKey();
                    }
                    catch (Exception e)
                    {
                        Console.WriteLine(e);
                    }
                }

                public class Employee
                {
                    public string Username { get; set; }
                    public string Password { get; set; }
                    public string Role { get; set; }
                    public Employee(string username, string password, string role)
                    {
                        Username = username;
                        Password = password;
                        Role = role;
                    }
                }

                public interface ISharedFolder
                {
                    void PerformRWOperations();
                }

                public class SharedFolder : ISharedFolder
                {
                    public void PerformRWOperations()
                    {
                        Console.WriteLine("Performing Read Write operation on the Shared Folder");
                    }
                }

                class SharedFolderProxy : ISharedFolder
                {
                    private ISharedFolder folder;
                    private Employee employee;
                    public SharedFolderProxy(Employee emp)
                    {
                        employee = emp;
                    }
                    public void PerformRWOperations()
                    {
                        if (employee.Role.ToUpper() == "CEO" || employee.Role.ToUpper() == "MANAGER")
                        {
                            folder = new SharedFolder();
                            Console.WriteLine("Shared Folder Proxy makes call to the RealFolder 'PerformRWOperations method'");
                            folder.PerformRWOperations();
                        }
                        else
                        {
                            Console.WriteLine("Shared Folder proxy says 'You don't have permission to access this folder'");
                        }
                    }
                }
            }
        }

    </details>

    <details>
    <summary><b>Proxy Design Pattern Pattern realword example (Tiger)</b></summary>
    <br>

    Run the following C# console application in visual studio or visual studio code, also you can run code in [online](https://code.sololearn.com/#cs)

        using System;
        using System.Collections.Generic;

        namespace ProxyDesignPattern
        {
            class Program
            {
                public static void Main()
                {
                    try
                    {
                        IImage Image1 = new ProxyImage("Tiger Image");

                        Console.WriteLine("Image1 calling DisplayImage first time :");
                        Image1.DisplayImage(); // loading necessary
                        Console.WriteLine("Image1 calling DisplayImage second time :");
                        Image1.DisplayImage(); // loading unnecessary
                        Console.WriteLine("Image1 calling DisplayImage third time :");
                        Image1.DisplayImage(); // loading unnecessary
                        Console.WriteLine();
                        IImage Image2 = new ProxyImage("Lion Image");
                        Console.WriteLine("Image2 calling DisplayImage first time :");
                        Image2.DisplayImage(); // loading necessary
                        Console.WriteLine("Image2 calling DisplayImage second time :");
                        Image2.DisplayImage(); // loading unnecessary
                        Console.ReadKey();

                    }
                    catch (Exception e)
                    {
                        Console.WriteLine(e);
                    }
                }

                public interface IImage
                {
                    void DisplayImage();
                }
                public class RealImage : IImage
                {
                    private string Filename { get; set; }
                    public RealImage(string filename)
                    {
                        Filename = filename;
                        LoadImageFromDisk();
                    }
                    public void LoadImageFromDisk()
                    {
                        Console.WriteLine("Loading Image : " + Filename);
                    }
                    public void DisplayImage()
                    {
                        Console.WriteLine("Displaying Image : " + Filename);
                    }
                }
                public class ProxyImage : IImage
                {
                    private RealImage realImage = null;
                    private string Filename { get; set; }
                    public ProxyImage(string filename)
                    {
                        Filename = filename;
                    }
                    public void DisplayImage()
                    {
                        if (realImage == null)
                        {
                            realImage = new RealImage(Filename);
                        }
                        realImage.DisplayImage();
                    }
                }
            }
        }

    </details>

    **[⬆ Back to Top](#table-of-contents)**

16. ### References

    I have followed many articles but among them, the following articles are really helpful. Those articles helped me a lot and also encourage me to write this article according to my understanding.

    - [dotnettutorials](https://dotnettutorials.net/course/dot-net-design-patterns/) Design Patterns in C# With Real-Time Examples
    - [refactoring](https://refactoring.guru/design-patterns) Design Patterns
    - [sourcemaking](https://sourcemaking.com/design_patterns) Design Patterns
    - [dofactory](https://www.dofactory.com/net/design-patterns)
    - [Kudvenkat](https://csharp-video-tutorials.blogspot.com/2017/06/design-patterns-tutorial-for-beginners.html)
    - [github](https://github.com/exceptionnotfound/DesignPatterns)
    - [github](https://github.com/anupavanm/csharp-design-patterns-for-humans) Design patterns for humans (C#)
    - [github](https://github.com/sohamkamani/javascript-design-patterns-for-humans) Design patterns for humans (javascript)
    - [github](https://github.com/kamranahmedse/design-patterns-for-humans) Design patterns for humans (PHP)
    - [tutorialspoint](https://www.tutorialspoint.com/design_pattern/index.htm) Design Patterns in Java Tutorial
    - [javatpoint](https://www.javatpoint.com/design-patterns-in-java) Design Patterns
    - [github](https://github.com/DovAmir/awesome-design-patterns)
    - [geeksforgeeks](https://www.geeksforgeeks.org/factory-method-design-pattern-in-java) Factory method design pattern in Java
    - [geeksforgeeks](https://www.geeksforgeeks.org/builder-design-pattern/) Builder Design Pattern
    - [geeksforgeeks](http://www.advancesharp.com/blog/1230/singleton-design-pattern-in-c-with-real-examples) Singleton design pattern in c# with real examples
    - [stackoverflow](https://stackoverflow.com/questions/13029261/design-patterns-factory-vs-factory-method-vs-abstract-factory) Design Patterns: Factory vs Factory method vs Abstract Factory
    - [stackoverflow](https://stackoverflow.com/questions/4209791/design-patterns-abstract-factory-vs-factory-method) Design Patterns: Abstract Factory vs Factory Method

    DI

    - [codeproject](https://www.codeproject.com/Articles/1059870/Use-Dependency-Injector-Ninject-to-dynamically-cho)
    - [c-sharpcorner](https://www.c-sharpcorner.com/article/how-to-implement-dependency-injection-in-mvc-project/)
    - [dotnettricks](https://www.dotnettricks.com/learn/dependencyinjection/dependency-injection-in-aspnet-mvc-4-using-unity-ioc-container)

    **[⬆ Back to Top](#table-of-contents)**

## Contribution

If you want to contribute to this project to make it more helpful for other Angular developers, your help is very welcome!

Just file an issue, better yet: submit a PR! 🙂

## License

[![License: CC BY-NC-SA 4.0](https://img.shields.io/badge/License-CC%20BY--NC--SA%204.0-lightgrey.svg)](https://creativecommons.org/licenses/by-nc-sa/4.0/)
