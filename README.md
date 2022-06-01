# Lambda Triggers (LT)
#### Lead(s): Joe Swantek

### Overview:

### Requirements:
The Lamba Trigger system will use token-based authentication, such as the OAuth, so programmers can wire up complex workflows and lambda functions can push configuration changes to nodes via the Edge Scheduler.  

### Use Cases:
#### User writes a To-Edge trigger:
* A Scientist gathers and fuses several data streams together, some from external data sources such as weather predictions, and some from Beehive into an external, independently managed code.
* Based on the computation, the code connects to the Edge Scheduler and presents an auth token
* The code then triggers a “to-Edge” configuration change via an API
* The Edge Scheduler then pushes down the configuration modification to the nodes
#### Node triggers a Lambda function in the Cloud:
* A node sends data to Beehive
* A plugin running on Beehive, processes the raw sensor data and may trigger a Lambda function.  For example, when wind velocities exceed a threshold
* A Lambda function executes on Chameleon.  It could be a large parallel computation or weather forecast.   The output could initiative another To-Edge action.

### Milestones:
* Publish design document, including prototype APIs
* Demonstrate "From-Edge" values initiating a lambda function execution in the cloud
* Deploy auth-token configuration management to the network
* Release V1.0 of the SLT suite of tools
