# Use-case "Physical Limits Exceeded"

Use-case|Physical limits exceeded
---------------------|---------------------------------
Proposed by |VDA PG API
Proposed on |06.11.2020
Description |During the transport or loading/reloading of goods something happens which is outside physical tolerances (e.g. temperature is too hot, strong shaking, too much light,…). This can lead to damage to the goods. Sensors detected this anomaly and sends out an event as warning.   
Actors | Sensor
Pre-condition | Sensors are on the transport loading unit and configured for the goods in the TLU. They are connected to a mobile sending unit and can transmit their data.


  
  
  
There are probably two main scenarios:
1. The monitoring device stores all recorded information locally and at the end of the transport process (or a transport leg) an involved party analyses the content. If a relevant observation is stored, an event is created by this party.
2. The monitoring device is connected to a app or other software that generates an event immediately once physical limits are exceeded.

In either case the standard procedure to communicate an event applys.A the POST command is used with the /transport-events path without an ID to create an empty event in the target system and receive the unique key for the TransportEvent object.
```
url -X 'POST' \
  'https://api.sample.com/vda_odette_ttt/V1/transport-events' \
  -H 'accept: */*' \
  -H 'X-API-KEY: adsas' \
  -d ''
```  
The server returns the ID
```
{
  "ReturnedID": {
    "content": "447f9180-9aca-4e9c-95a3-b5e1bd3ac55d"
  }
}
```
Then the data set issent with PUT command using the /transport-events/{ident} path.



It is the task of the receiving system to link the event to the referenced shipment and or shipment items. The mobile app has to be able to enrich the physical measure data with these references.

