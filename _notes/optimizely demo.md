---
title: How to use Optimizely to implement feature flag
---

### Third POC to find the right tool to implement feature flags 

It's a small demo of how to use Optimizely in an ASP.NET Core application.

In this note we will have:

✔️ The most basic example how to use Optimizely in an ASP.NET Core application ;

✔️ How to configure the experiences in the Optimizely dashboard;

First, we need to install the splitIO Nuget package:

´´´
Install-Package Optimizely.SDK
´´´

To test this tool we need to have a demo account, so we can create an API key and have an interface to manage the feature flags. 
To create the demo we used the link [https://www.optimizely.com/free-feature-flagging/]. It can take some days while the optimize team analyses your proposal to have a demo account.

Having the demo account we can create a flag in the menu:

 <img src="images/Optimizely.jpg"> 

The API key is available after we create our account on your Settings page. With this key, we can instantiate the `Optimizely` object using the `OptimizelyFactory`. We have to create a user, it is used to ensure that every user will have always the same feature flag configuration or the same ABTesting experience.

´´´ c#
namespace OptimizelyDemo.Controllers
{
    [ApiController]
    [Route("[controller]")]
    public class OptimizelyDemoController : ControllerBase
    {
        private readonly Optimizely optimizely;


        private readonly ILogger<OptimizelyDemoController> _logger;

        public OptimizelyDemoController()
        {
            optimizely = OptimizelyFactory.NewDefaultInstance(_key);
        }

        [HttpGet]
        public bool Get()
        {
            OptimizelyUserContext user = optimizely.CreateUserContext("user123", new UserAttributes());
            OptimizelyDecision decision = user.Decide("test");
            var enabledBraches = decision.Variables.GetValue<Dictionary<string, object>>("branches");

            if(enabledBraches.Values.Contains("branch1"))
            {
                return decision.Enabled;
            }

            return false;
        }
    }
}

´´´

To get the feature flag we just need to use the extension method `decide` from the user previously created. If we want to specify something else associated with the experience we can use the Variables associated with the experience. 

Each feature flag can have variations, with this we can define variables and groups of users or targets where a specific feature flag will be implemented.

<img src="images/Optimizely2.jpg"> 

Optimizely is an ABTesting tool that provides the possibility to create feature flag toggles in an easy way. Of course, every ABTesting tool can be turned into a Feature flag tool.

[[How to use splitIO to implement feature flag]]