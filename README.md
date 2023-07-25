# CSharp-Project-ContosoPizza

This mini project is to learn how to build MVC architecture in .NET framework with C#.

Despite comments added by my own for learning purpose and ease of reference, the whole set of materials belongs to Microsoft.

If you are interested in learning C#, please visit the following link for more details :) Thanks!

[Create a web API with ASP.NET Core controllers](https://learn.microsoft.com/en-us/training/modules/build-web-api-aspnet-core/)

Step 1 - basic setup:
In .NET CLI, `mkdir` to create a new folder, `cd` into it, and run `dotnet new webapi -f net6.0` to create a boilerplate.

Step 2 - basic setup:
Run `dotnet run` to build from the boilerplate, you should be able to see 2 ports are used, one starts with 7 and one 5, for both HTTPS and HTTP.

Open the path (`https://localhost:{PORT}/weatherforecast`) in browser to check if it is accessible. If not, ensure the CAs (certificate authorities) in browser are setup.

Step 3 - basic setup:
Run `dotnet tool install -g Microsoft.dotnet-httprepl` to install globally Httprepl, a lightweighted CLI tool for making requests to RESTful APIs.

Step 4 - basic setup:
Run `httprepl https://localhost:{PORT}` to connect to the path (ensure the server is still listening in another terminal).

**
Httprepl:
run `ls` to list out all possible requests.
run `cd` to navigate to particular endpoint.
run `get` or `post` or any other methods available to make the request.
run `exit` to leave.
**

Step 5 - setup Model (for simplicity, here will be just local in-memory caching service):
Create a new folder called "Models" - if not using .NET Core MVC template.
Create a file inside the folder, here it is called "Pizza".
Create a namespace for this file, here it is called "ContosoPizza.Models", and
a public class below, which contains the following public fields:

- public int Id {get; set;}
- pubilc string? Name {get; set;}
- public bool IsGlutenFree {get;set;}

Step 6 - setup Service
Create a new folder called "Services".
Create a file inside the folder, here it is called "PizzaService".

**
Services/PizzaServices.cs

using the Model we just created on top
don't forget to create a namespace for the file
create a public static class in which

2 private properties - initialID & ListOfPizzas with getter;

Constructor holding 2 default pizzas

5 public actions/methods:
- GetAll() return ListOfPizza
- Get(int id) => [Instance].FirstOrDefault(p => p.id == id) 

[[Enumerable].FirstOrDefault(Func)](https://learn.microsoft.com/en-us/dotnet/api/system.linq.enumerable.firstordefault?view=net-7.0)
Returns the first element of a sequence, or a default value if no element is found.

- Add(Pizza pizza) => add pizza to ListOfPizza, return void
- Delete(int id) => get pizza by Get(int id), if its null, return, else [Instance].Remove(pizza)
[[List].Remove(item)](https://learn.microsoft.com/en-us/dotnet/api/system.collections.generic.list-1.remove?view=net-7.0)
- Update(Pizza pizza) => get the index of that pizza by List.FindIndex(Func), if -1 return, else assign the existing pizza id with new pizza content.

**
