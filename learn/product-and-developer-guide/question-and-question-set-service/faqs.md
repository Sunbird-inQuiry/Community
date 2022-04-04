# FAQs

### 1. What is the recommended way to make a deep copy of a request?

_I want to a make a deep copy of this request before updateHierarchy() call is made. It has to be a deep copy because updateHierarchy() modifies the request during its processing and I no longer can use the original request or a shallow copy once updateHierarchy has finished its execution. What is the recommended way to do this?_

_Note: The goal is to use the same request with all nodes in nodesModified set as isNew=false, and replace all identifiers with appropriate do\_ids and re-run the updateHierarchy()._

In order to make a deep copy of Sunbird Request, you can serialize it and then deserialize back as a Request class object. For serialization and deserialization, you can use exiting files like JsonUtils or ScalaJsonUtils.&#x20;

You can also follow [https://github.com/Sunbird-inQuiry/Community/discussions/6](https://github.com/Sunbird-inQuiry/Community/discussions/6) thread for more details.

