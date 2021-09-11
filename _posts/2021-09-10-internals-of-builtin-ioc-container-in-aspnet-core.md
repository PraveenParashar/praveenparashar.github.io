---
title: internals-of-builtin-ioc-container-in-aspnet-core
date: 2021-09-11T08:55:20+05:30
author: Praveen Parashar
categories: [Miscellaneous]
tags: [.netCore, Must-Know, Interview]
description: .NetCore , builtin-ioc-container, DI 

---

#### ASP.NET Core: Built-in IoC Container

ASP.NET Core framework includes built-in IoC container for automatic dependency injection. The built-in IoC container is a simple yet effective container. Let's understand how the built-in IoC container works internally.

### The followings are important interfaces and classes for built-in IoC container:

### Interfaces:
IServiceProvider
IServiceCollection


### Classes:
ServiceProvider
ServiceCollection
ServiceDescription
ServiceCollectionServiceExtensions
ServiceCollectionContainerBuilderExtensions

### The following diagram illustrates the relationship between these classes:


## built-in IoC Container


## IServiceCollection
As you know, we can register application services with built-in IoC container in the Configure method of Startup class by using IServiceCollection. IServiceCollection interface is an empty interface. It just inherits IList<servicedescriptor>. See the source code here.

The ServiceCollection class implements IServiceCollection interface. See the ServiceCollection source code here.

So, the services you add in the IServiceCollection type instance, it actually creates an instance of ServiceDescriptor and adds it to the list.

## IServiceProvider
IServiceProvider includes GetService method. The ServiceProvider class implements IServiceProvider interface which returns registered services with the container. We cannot instantiate ServiceProvider class because its constructors are marked with internal access modifier.

## ServiceCollectionServiceExtensions
The ServiceCollectionServiceExtensions class includes extension methods related to service registrations which can be used to add services with lifetime. AddSingleton, AddTransient, AddScoped extension methods defined in this class.

ServiceCollectionContainerBuilderExtensions
ServiceCollectionContainerBuilderExtensions class includes BuildServiceProvider extension method which creates and returns an instance of ServiceProvider.

There are three ways to get an instance of IServiceProvider:

### Using IApplicationBuilder
We can get the services in Configure method using IApplicationBuilder's ApplicationServices property as shown below.
```markdown
public void Configure(IServiceProvider pro, IApplicationBuilder app, IHostingEnvironment env)
{
    var services = app.ApplicationServices;
    var logger = services.GetService<ILog>() }

   .... 
}
```


### Using HttpContext
```markdown 
var services = HttpContext.RequestServices;
var log = (ILog)services.GetService(typeof(ILog));
Using IServiceCollection
public void ConfigureServices(IServiceCollection services)
{
    var serviceProvider = services.BuildServiceProvider();

}
```


REFERENCE LINK-
<a href="https://www.tutorialsteacher.com/core/internals-of-builtin-ioc-container-in-aspnet-core" title="builtin-ioc-container-in-aspnet-core">here</a>