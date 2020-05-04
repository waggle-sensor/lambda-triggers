# Sage Lambda Triggers (SLT)
#### Lead(s): Kate Keahey and [Joe Swantek](mailto:joseph.swantek@northwestern.edu)

### Overview:
Triggered actions are an important part of the Sage architecture.  The SLT provides a framework for two kinds of triggers: From-Edge and To-Edge.  A value or message from a Waggle edge node, delivered to Beehive, can be used to trigger a lambda function -- for example, if high wind velocity is detected, a function could be triggered to determine how to reconfigure sensors or launch a computation or send an alert.  Similarly, an HPC calculation or cloud-based data analysis could trigger an API call to the SES and send a notification to a Waggle edge node -- for example to request scheduling of new edge computations or reposition mobile assets.

### Requirements:
The SLT system will use token-based authentication, such as the OAuth, so programmers can wire up complex workflows and lambda functions can push configuration changes to nodes via the Sage Edge Scheduler.  

### Use Cases:
#### Scientist writes a To-Edge trigger:
* A Scientist gathers and fuses several data streams together, some from external data sources such as weather predictions, and some from Sage Beehive into an external, independently managed code.
* Based on the computation, the code connects to the SES and presents an auth token
* The code then triggers a “to-Edge” configuration change via an API
* The SES then pushes down the configuration modification to the Sage nodes
#### Sage node triggers a Lambda function in the Cloud:
* A Sage node sends data to Beehive
* A plugin running on Beehive, processes the raw sensor data and may trigger a Lambda function.  For example, when wind velocities exceed a threshold
* A Lambda function executes on Chameleon.  It could be a large parallel computation or weather forecast.   The output could initiative another To-Edge action.

### Milestones:
* Publish design document, including prototype APIs
* Demonstrate "From-Edge" values initiating a lambda function execution in the cloud
* Deploy auth-token configuration management to Sage network
* Release V1.0 of the SLT suite of tools
