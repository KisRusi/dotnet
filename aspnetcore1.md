## Source of methods called by CreateHostBuilder
https://github.com/dotnet/extensions/blob/v3.1.2/src/Hosting/Hosting/src/Host.cs
https://github.com/dotnet/aspnetcore/blob/v3.1.2/src/DefaultBuilder/src/GenericHostBuilderExtensions.cs
https://github.com/dotnet/aspnetcore/blob/v3.1.2/src/DefaultBuilder/src/WebHost.cs

## Appsetting.json w DummySettings

```javascript
{
  "Logging": {
    "LogLevel": {
      "Default": "Warning"
    }
  },
  "AllowedHosts": "*",
  "DummySettings": {
    "DefaultString": "My Value",
    "DefaultInt": 23,
    "SuperSecret":  "Spoiler Alert!!!"
  }
}
```
## DummySettings class

```csharp
public class DummySettings
{
    public string DefaultString { get; set; }

    public int DefaultInt { get; set; }

    public string SuperSecret { get; set; }
}
```
## Get DummySettings injected into DummyController
```csharp
private DummySettings options;

public DummyController(IOptions<DummySettings> options)
{
    this.options=options.Value;
}
```

## DummySettings.Get getting data from IOption
```csharp
[HttpGet("{id}", Name = "Get")]
public string Get(int id)
{
    return id % 2 == 0 ? options.DefaultString : options.DefaultInt.ToString();
}
```


## secrets.json
```javascript
{
  "DummySettings": {
    "DefaultString": "My Value",
    "DefaultInt": 23,
    "SuperSecret": "SECRET"
  }
}
```
