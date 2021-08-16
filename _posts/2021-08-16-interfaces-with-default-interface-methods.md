---
title: Creating classes using interfaces with default interface methods
date: 2021-08-16T08:36:20+05:30
author: Praveen Parashar
categories: [C#]
tags: [C#, Advance-concepts, tutorials, interview]
description: Mix functionality in when creating classes using interfaces with default interface methods
---  


  In C# 8.0  you can define an implementation when you declare a member of an interface. This feature provides new capabilities where you can define default implementations for features declared in interfaces. Classes can pick when to override functionality, when to use the default functionality, and when not to declare support for discrete features.  

  Create interfaces with implementations that describe discrete features.
  Create classes that use the default implementations.
  Create classes that override some or all of the default implementations.  

#### Limitations of extension methods 
  
  One way you can implement behavior that appears as part of an interface is to define extension methods that provide the default behavior. Interfaces declare a minimum set of members while providing a greater surface area for any class that implements that interface. For example, the extension methods in Enumerable provide the implementation for any sequence to be the source of a LINQ query.
  

  Extension methods are resolved at compile time, using the declared type of the variable. Classes that implement the interface can provide a better implementation for any extension method. Variable declarations must match the implementing type to enable the compiler to choose that implementation. When the compile-time type matches the interface, method calls resolve to the extension method. Another concern with extension methods is that those methods are accessible wherever the class containing the extension methods is accessible. Classes cannot declare if they should or should not provide features declared in extension methods.

  Starting with C# 8.0, you can declare the default implementations as interface methods. Then, every class automatically uses the default implementation. Any class that can provide a better implementation can override the interface method definition with a better algorithm.

  ```c#
  interface that defines the behavior for all lights
  public interface ILight
  {
      void SwitchOn();
      void SwitchOff();
      bool IsOn();
  }
  A basic overhead light fixture might implement this interface as shown in the following code:

  public class OverheadLight : ILight
  {
      private bool isOn;
      public bool IsOn() => isOn;
      public void SwitchOff() => isOn = false;
      public void SwitchOn() => isOn = true;

      public override string ToString() => $"The light is {(isOn ? "on" : "off")}";
  }
  Next, let's define the interface for a light that can automatically turn off after a timeout:
  10T011public interface ITimerLight : ILight
  {
      Task TurnOnFor(int duration);
  }  

  You could add a basic implementation to the overhead light, but a better solution is to modify this interface definition to provide a virtual default implementation:
    
    public interface ITimerLight : ILight
  {
      public async Task TurnOnFor(int duration)
      {
          Console.WriteLine("Using the default interface method for the ITimerLight.TurnOnFor.");
          SwitchOn();
          await Task.Delay(duration);
          SwitchOff();
          Console.WriteLine("Completed ITimerLight.TurnOnFor sequence.");
      }
  }
  ```

  Reference tutorials:
    <a href="https://docs.microsoft.com/en-us/dotnet/csharp/whats-new/tutorials/mixins-with-default-interface-methods" title="default-interface-methods">default-interface-methods</a>
    