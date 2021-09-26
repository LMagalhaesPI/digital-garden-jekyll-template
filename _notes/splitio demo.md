---
title: How to use splitIO to implement feature flag
---

### Second POC to find the right tool to implement feature flags 

It's a small demo of how to use split IO in an ASP.NET Core application.

In this spike we have:

✔️ The most basic example how to use Split IO in an ASP.NET Core application;

✔️ How to configure the experiences in the Split IO dashboard;

First, we need to install the splitIO Nuget package:

´´´
Install-Package Splitio -Version 6.3.4
´´´

To test this tool you need to have a dome account so you can create an api key. The API key is available after we create our account on your Organization Settings page, on the APIs tab. With this key we can instantiate the `SplitFactory` and create a client.
We need to use the `.BlockUntilReady(int milliseconds)` method to make sure the SDK is properly loaded before asking for it.

´´´ c#
namespace FeatureFlag_SplitIO.Controllers
{
    using Microsoft.AspNetCore.Mvc;
    using Splitio.Services.Client.Classes;
    using Splitio.Services.Client.Interfaces;


    [ApiController]
    [Route("[controller]")]
    public class FeatureFlagsController
    {
        private ISplitClient splitClient;

        public FeatureFlagsController()
        {
            var config = new ConfigurationOptions();
            var factory = new SplitFactory("api_key", config);
            splitClient = factory.Client();
        }

        [HttpGet]
        public List<FeatureFlag> Get()
        {
            try
            {
                splitClient.BlockUntilReady(10000);
                var featureFlags = splitClient.GetTreatments("9c7fee20-00f5-11ec-abdf-3ac6c77916d6", new List<string>() { "Amazing_Wonderful_Feature" });
                var result = featureFlags.Select(kvp => new FeatureFlag(kvp.Key, kvp.Value)).ToList();
                return result;
            }
            catch (Exception ex)
            {
                return new List<FeatureFlag>();
            }
        }
    }
}
´´´

We can use the method `GetTreatment` to get the feature flags that we defined in our account. Using the treatment and the feature flag name. 