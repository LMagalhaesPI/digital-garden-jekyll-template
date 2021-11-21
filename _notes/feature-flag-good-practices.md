---
title: Good practices using feature flags
---

☝🏽 Never reuse a feature flag;<br/>
☝🏽 Create a naming convecting to name the feature flags:<br/>
&emsp;&emsp;Feature name;<br/>
&emsp;&emsp;Team name;<br/>
&emsp;&emsp;Service name;<br/>
&emsp;&emsp;Ticket number;<br/>
<br/>
☝🏽 Code reviews or control and audit access to change any feature flag config;<br/>
☝🏽 Users should always have the same experience;<br/>
☝🏽 Observe and adjust;<br/>
☝🏽 Assign an experation data for each flag:<br/>
&emsp;&emsp;Create a task to remove the feature flag;<br/>
&emsp;&emsp;Remove the feature flag and all the code related with it;<br/>
