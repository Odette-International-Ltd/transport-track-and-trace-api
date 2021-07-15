# Use Case Loading Confirmation for Shipment issued by Ship-from

Use-case | Loading confirmation
-----------|---------------------    
Proposed by| VDA PG API   
Proposed on| 11.09.2020
Description| The ship-from-party notifies which shipments TLU has loaded on a means of transport   
Actors| Ship-from, LSP, optional: ship-to, transport ordering party  
Pre-condition| Loading details and transport means ID are known   
Post-condition| Shipment and or Shipment Item status changed to "LOADED"   

Note: 

First, the ship-from party uses a POST command without a parameter on path .../transport-events
to generate an empty object in the target system.
```  
curl -X 'POST' \
  'https://api.sample.com/vda_odette_ttt/V1/transport-events' \
  -H 'accept: */*' \
  -H 'X-API-KEY: adsas' \
  -d ''
```  
The server returns the unique ID of the TransportEvent object:
```  
{
  "ReturnedID": {
    "content": "d9cb4b05-6d4d-420a-a18c-0b3875ee828c"
  }
}
```  
The ship-from party then uses a PUT command with the ID as parameter and sends the data of the event:

```   
curl -X 'PUT' \
  'https://api.sample.com/vda_odette_ttt/V1/transport-events/d9cb4b05-6d4d-420a-a18c-0b3875ee828c' \
  -H 'accept: application/json' \
  -H 'X-API-KEY: adsas' \
  -H 'Content-Type: application/json' \
  -d '{
 "ID": {"content": "d9cb4b05-6d4d-420a-a18c-0b3875ee828c"},
 "TypeCode": {"content": "ACTUAL"},
 "ReportedConditionTypeCode": {"content": "ISSUE_COMPLETED"},
 "OccurenceDateTime": {"content": "2021-07-02T08:35:00Z"},
 "OccurrenceLocation": {
  "ID": {"content": "DOCK 15"},
  "TypeCode": {"content": "9"},
   // Loading location
  "PhysicalGeographicalCoordinate": {
   //51.49674858715566, -0.1313110731869426
   "LatitudeMeasure": {"content": 51.49674858715566, "unitCode": "DD"},
   "LongitudeMeasure": {"content": 0.1313110731869426,"unitCode": "DD"},
   "LatitudeDirectionIndicator": {"content": "N"},
   "LongitudeDirectionIndicator": {"content": "W"}
  }
 },
 "ReferencedTransportMovement": {
  "StageCode": {"content": "12"},//At departure
  "ModeCode": {"content": "3"},  //Road transport
  "UsedTransportMeans": {
   "TypeCode": {"content": "T01"   },
   "Type": {"content": "Eurotrailer H 2.6, W 2.48, L 13.6 tarpauline or box", "languageID": "en"},
   "ID": {"content": "SW5 3PX"}
  }
 },
 "ReferencedConsignment": [
  {
   "ID": {"content": "2KODA05303020210003"},
   "ConsignmentItemQuantity": { "content": 10},
   "StatusCode": { "content": "LOADED"},
   "IncludedConsignmentItem": [
    { "ID": { "content": "ODA05303000000001" }},
    { "ID": { "content": "ODA05303000000002" }},
    { "ID": { "content": "ODA05303000000003" }},
    { "ID": { "content": "ODA05303000000004" }},
    { "ID": { "content": "ODA05303000000005" }},
    { "ID": { "content": "ODA05303000000006" }},
    { "ID": { "content": "ODA05303000000007" }},
    { "ID": { "content": "ODA05303000000008" }},
    { "ID": { "content": "ODA05303000000009" }},
    { "ID": { "content": "ODA05303000000010" }}
   ]
  }
 ]
}
```   
