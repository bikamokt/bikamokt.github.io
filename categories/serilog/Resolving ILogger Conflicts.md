# Resolving ILogger Conflicts with Serilog and Microsoft Logger

## Overview
When using Serilog alongside `Microsoft.Extensions.Logging`, conflicts can arise due to multiple logging providers being registered. This guide helps you configure Serilog properly and avoid conflicts.

## 1. Properly Configuring Serilog
Ensure that Serilog is the primary logging provider by modifying `Program.cs`:

```csharp
using Microsoft.AspNetCore.Builder;
using Microsoft.AspNetCore.Hosting;
using Microsoft.Extensions.DependencyInjection;
using Microsoft.Extensions.Hosting;
using Serilog;

var builder = WebApplication.CreateBuilder(args);

// Remove default logging providers
builder.Logging.ClearProviders();

// Add Serilog
Log.Logger = new LoggerConfiguration()
    .WriteTo.Console()
    .WriteTo.File("logs/log.txt", rollingInterval: RollingInterval.Day)
    .CreateLogger();

builder.Host.UseSerilog(); // Redirect built-in logging to Serilog

var app = builder.Build();

app.MapGet("/", () => "Hello World!");

app.Run();
```

## 2. Ensure Correct Dependency Injection
Inject `ILogger<T>` properly so that Serilog is used:

```csharp
public class MyService
{
    private readonly ILogger<MyService> _logger;

    public MyService(ILogger<MyService> logger)
    {
        _logger = logger;
    }

    public void DoSomething()
    {
        _logger.LogInformation("This is a log message.");
    }
}
```

If Serilog is configured correctly, `ILogger<T>` will automatically use Serilog.

## 3. Remove Microsoft Logger If Not Needed
If you only want Serilog, explicitly remove Microsoft's logging providers:

```csharp
builder.Logging.ClearProviders();
```

## 4. Check `appsettings.json` Configuration (Optional)
Ensure your `appsettings.json` contains the correct Serilog settings:

```json
{
  "Serilog": {
    "Using": ["Serilog.Sinks.Console", "Serilog.Sinks.File"],
    "MinimumLevel": "Information",
    "WriteTo": [
      { "Name": "Console" },
      { "Name": "File", "Args": { "path": "logs/log.txt", "rollingInterval": "Day" } }
    ]
  }
}
```

## 5. Check for Duplicate ILogger Registrations
Avoid adding Microsoft logging explicitly if using Serilog:

### Remove this:
```csharp
builder.Services.AddLogging();
```

### Use only this instead:
```csharp
builder.Host.UseSerilog();
```

## 6. Ensure Required Packages Are Installed
Run the following commands to install necessary packages:

```sh
dotnet add package Serilog.Extensions.Logging
dotnet add package Serilog.AspNetCore
```

## Summary
✅ **Use `builder.Host.UseSerilog();`** to redirect logs to Serilog.  
✅ **Call `builder.Logging.ClearProviders();`** to prevent conflicts.  
✅ **Ensure `ILogger<T>` resolves correctly with dependency injection.**  
✅ **Check `appsettings.json` for proper Serilog configuration.**  

Following these steps will prevent conflicts between Serilog and `Microsoft.Extensions.Logging`, ensuring a smooth logging experience.

---

### **Need Help?**
Feel free to open an issue or contribute to this repository if you have improvements! 🚀

