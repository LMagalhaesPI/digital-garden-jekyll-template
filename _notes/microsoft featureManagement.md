---
title: How to use Microsoft.FeatureManagement to implement feature flag
---

### First POC to find the right tool to implement feature flags 🤪

It's a small example of how to use a feature flag in an ASP.NET Core application with the open-source library Microsoft.FeatureManagement.

In this note you will learn:
✔️ The most basic example with the most simple config;
✔️ An example with a custom filter;

## The most basic example to put your project working

First, we need to install the NuGet package Microsoft.FeatureManagement.AspNetCore. Using the default settings we can configure the feature flags in the *appsettings.json* file.

```json
{
  "Logging": {
    "LogLevel": {
      "Default": "Information",
      "Microsoft": "Warning",
      "Microsoft.Hosting.Lifetime": "Information"
    }
  },
  "AllowedHosts": "*",
  "FeatureManagement": {
    "TestFeatureFlag": true
  }
}

```

To use the default configuration location, call the AddFeatureManagement method of the `IServiceCollection` passed into the 
`ConfigureServices` method of the `Startup` class:

```c#

        public void ConfigureServices(IServiceCollection services)
        {
            services.AddControllers();
            services.AddFeatureManagement();
        }
```

In the controller/service/ wherever do you want to use it you just need to inject the `IFeatureManager` in the class:

```c#
namespace FileConfigsTest.Controllers
{

    using System.Threading.Tasks;
    using Microsoft.AspNetCore.Mvc;
    using Microsoft.Extensions.Logging;
    using Microsoft.FeatureManagement;

    [ApiController]
    [Route("[controller]")]
    public class AmazingFeatureFlagPOCController : ControllerBase
    {
        private readonly IFeatureManager _featureManager;

        public AmazingFeatureFlagPOCController( IFeatureManager featureManager)
        {
            _featureManager = featureManager;
        }

        [HttpGet]
        public async Task<string> Get()
        {
            var featureTest = await _featureManager.IsEnabledAsync("TestFeatureFlag")
                ? "Feature Flag Enable"
                : "Feature Flag Disable";
            return featureTest;
        }
    }
}
```
Done ⚙️⚙️⚙️⚙️

## Working with filters!! 🌫️🌫️

We can add filters and conditions using the *appsettings.json* file:

```json
{
  "Logging": {
    "LogLevel": {
      "Default": "Information",
      "Microsoft": "Warning",
      "Microsoft.Hosting.Lifetime": "Information"
    }
  },
  "AllowedHosts": "*",
  "FeatureManagement": {
    "TestFeatureFlag": {
      "EnabledFor": [
        {
          "Name": "TestFeatureFlagFilterFilter",
          "Parameters": {
            "BranchIds": [2, 3, 4]
          }
        }
      ]
    }
  }
}

```
 Can create a strongly typed settings class to represent the settings:

 ```c#

 namespace FileConfigsTest
{
    public class TestFeatureFlagFilterFilterSettings
    {
        public List<string> BranchIds { get; set; }
    }
}

 ```

 We can create a feature filter that uses information about the current HttpContext to decide whether or not to enable a feature.
 Our filter implementation will implement the interface `IFeatureFilter`:

```c#
 namespace FileConfigsTest
{
    [FilterAlias("TestFeatureFlagFilterFilter")]
    public class TestFeatureFlagFilter : IFeatureFilter
    {
        public Task<bool> EvaluateAsync(FeatureFilterEvaluationContext context)
        {
            TestFeatureFlagFilterFilterSettings settings = context.Parameters.Get<TestFeatureFlagFilterFilterSettings>();

            if (settings.BranchIds.Contains("1"))
            {
                return Task.FromResult(true);
            }
            else return Task.FromResult(false);

        }
    }
}
``` 

Easy peasy !!!!