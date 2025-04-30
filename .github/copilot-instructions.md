Use .NET 8 and C# for all code.

Use DDD principals when creating domain-layer entities and value objects, and 
use the FluentResults NuGet package to implement TryCreate methods for them. for
example:
```csharp
public static Result<SomeEntity> TryCreate(string someValue)
{
    if (string.IsNullOrWhiteSpace(someValue))
        return Result.Fail<SomeEntity>("Some value cannot be null or empty.");

    return Result.Ok(new SomeEntity(someValue));
}
``` 

Prefer records for value objects and classes for entities.

Use the following interface for use case interactors
```csharp
/// <summary>
/// Use case interactor interface.
/// </summary>
/// <typeparam name="TRequest">Request type.</typeparam>
/// <typeparam name="TOutput">Output type.</typeparam>
public interface IUseCaseInteractor<TRequest, TOutput>
{
    /// <summary>
    /// Handles the request.
    /// </summary>
    /// <param name="request">Request.</param>
    /// <returns>Output.</returns>
    Task<TOutput> HandleAsync(TRequest request);
}
```
    
Use New-Item to create new folders in PowerShell instead of mkdir so that you
can create multiple folders at once.

Use the following structure when asked to create a new app according to Clean
Architecture principles, where {AppName} is the name of the app. Use the
top-level app folder as your workspace.
{AppName} (folder)  
├── {AppName}.sln  
├── {AppName}.Bootstrapper (folder)  
│   ├── {AppName}.Bootstrapper.csproj (reference {AppName}.Core and {AppName}.Infrastructure)  
├── {AppName}.Core (folder)  
│   ├── {AppName}.Core.csproj  
│   ├── Domain (folder where DDD entities and value objects are defined)  
│   ├── ExternalInterfaces (folder where external interfaces are defined)  
│   ├── UseCases (folder where application use cases are defined)  
│       ├── IUseCaseInteractor.cs  
├── {AppName}.Core.UnitTests (folder)  
│   ├── {AppName}.Core.UnitTests.csproj (reference {AppName}.Core)  
│   ├── Domain (folder where DDD entities and value objects are tested; use subfolders for each entity)  
│   ├── UseCases (folder where application use cases are tested; use)  
├── {AppName}.Infrastructure (folder)  
│   ├── {AppName}.Infrastructure.csproj (reference {AppName}.Infrastructure)  
├── {AppName}.Infrastructure.IntegrationTests (folder)  
│   ├── {AppName}.Infrastructure.IntegrationTests.csproj  
├── {AppName}.WebApi (folder)  
│   ├── {AppName}.WebApi.csproj (reference {AppName}.Core and {AppName}.Bootstrapper)  

Use `dotnet new sln` to create a solution file and add all projects to the
solution.

Use `dotnet new classlib` for new class libararies

Use `dotnet new xunit` for new xUnit test projects

Use `dotnet new webapi -minimal` for new Web API projects

Delete default Class1.cs and UnitTest1.cs files.

Each use case should be defined in its own folder under the UseCases folder, and
each use case should have its own request and response records and a boundary
interface. For example, if the use case is called "CreateUser", the folder
structure would look like this:
|-- UseCases  
|   |-- CreateUser  
|       |-- CreateUserRequest.cs  
|       |-- CreateUserResponse.cs  
|       |-- ICreateUserBoundary.cs  
|       |-- CreateUserInteractor.cs  

Use case boundary interfaces should have a TOutput type parameter and contain
methods for relevant use case events. For example, if the use case is called
"CreateUser", the boundary interface would look like this:
```csharp 
public interface ICreateUserBoundary<TOutput>
{
    public TOutput UserCreated(CreateUserResponse response, TOutput output);
    public TOutput UserAlreadyExists(
        CreateUserResponse response, TOutput output);
}
```

Use xUnit for tests and Moq for mocking external interfaces in use case unit
tests. Follow TDD principals for writing tests; write a failing unit test
before implementing anything. Ensure there's only on assertion per test.

After creating tests, ensure they pass before moving on. Make sure all files are
saved before running the tests.