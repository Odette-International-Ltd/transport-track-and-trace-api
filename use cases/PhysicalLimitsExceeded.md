#Use-case "Physical Limits Exceeded"

Use-case-------       |Physical limits exceeded
---------------------|---------------------------------
Proposed by|VDA PG API
Proposed on|06.11.2020
Description|During the transport or loading/reloading of goods something happens which is outside physical tolerances (e.g. temperature is too hot, strong shaking, too much light,…). This can lead to damage to the goods. Sensors detected this anomaly and sends out an event as warning.   
Actors | Sensor
Pre-condition| Sensors are on the transport loading unit and configured for the goods in the TLU. They are connected to a mobile sending unit and can transmit their data.

In case the monitored physical limit moves out of acceptable range the mobile app connects to the service providing system and uses the POST command on the /transport-events path without an ID to create an empty event in the target system and receive the unique key for the TransportEvent object.

Then it sends the data with thr PUT command using the /transport-events/{ident} path.

It is the task of the receiving system to link the event to the referenced shipment and or shipment items. The mobile app has to be able to enrich the physical mesure data with these references.


