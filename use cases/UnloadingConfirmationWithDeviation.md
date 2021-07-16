# Unloading/Receipt by Ship-to party with deviation

Use-case|Unloading confirmation / receipt with deviation
--------|-----------------------------------------------
Proposed by| VDA PG API
Proposed on| 11.09.2020
Description| The ship-to party confirms the receipt of a shipment with missing THUs
Actors|Ship-to
Pre-condition| Shipment is registered in the system and has been unloaded from means of transport
Post-condition| Shipment and THU status changed to "RECEIVED" respectively "MISSING"


Note:

First, the ship-to party uses a POST command without a parameter on path .../transport-events to generate an empty object in the target system.
```
url -X 'POST' \
  'https://api.sample.com/vda_odette_ttt/V1/transport-events' \
  -H 'accept: */*' \
  -H 'X-API-KEY: adsas' \
  -d ''
```  
  The server returns the unique ID of the TransportEvent object:
```
{
  "ReturnedID": {
    "content": "7dfd1688-8398-46d9-ab6f-742422eff929"
  }
}
```
The ship-to party then uses a PUT command with the ID as parameter and sends the data of the event:
```
curl -X 'PUT' \
  'https://api.sample.com/vda_odette_ttt/V1/transport-events/7dfd1688-8398-46d9-ab6f-742422eff929' \
  -H 'accept: application/json' \
  -H 'X-API-KEY: adsas' \
  -H 'Content-Type: application/json' \
  -d '{
 "ID": {"content": "7dfd1688-8398-46d9-ab6f-742422eff929"},
 "TypeCode": {"content": "ACTUAL"},
 "OccurenceDateTime": {"content": "2021-07-03T17:35:00Z"},
 "OccurrenceLocation": {
  "ID": {"content": "Abladestelle 23"},
  "TypeCode": {"content": "11"}, // Unoading location 52.51595494548417, 13.393288898331475
  "PhysicalGeographicalCoordinate": {
   "LatitudeMeasure": {"content": 52.51595494548417, "unitCode": "DD"},
   "LongitudeMeasure": {"content": 13.393288898331475,"unitCode": "DD"},
   "LatitudeDirectionIndicator": {"content": "N"},
   "LongitudeDirectionIndicator": {"content": "E"}}},
 "ReportingParty": {
  "ID": {"content": "A05303"},
  "Name": {"content": "Vereinigte Fahrzeugwerke Berlin"},
  "RoleCode": {"content": "ST"}},     
 "ReferencedTransportMovement": {
   "UsedTransportMeans": {
   "TypeCode": {"content": "T01"   },
   "Type": {"content": "Eurotrailer H 2.6, W 2.48, L 13.6 tarpauline or box", "languageID": "en"},
   "ID": {"content": "SW5 3PX"}}},
 "ReferencedConsignment": [{
   "ID": {"content": "2KODA05303020210003"},
   "ConsignmentItemQuantity": { "content": 9},
   "StatusCode": { "content": "UNLOADING_COMPLETED"},
   "IncludedConsignmentItem": [
    { "ID": { "content": "ODA05303000000001" }},
    { "ID": { "content": "ODA05303000000002" }},   
    { "ID": { "content": "ODA05303000000004" }},
    { "ID": { "content": "ODA05303000000005" }},
    { "ID": { "content": "ODA05303000000006" }},
    { "ID": { "content": "ODA05303000000007" }},
    { "ID": { "content": "ODA05303000000008" }},
    { "ID": { "content": "ODA05303000000009" }},
    { "ID": { "content": "ODA05303000000010" }}]}],
  "ReferencedConsignmentItem": [
    { "ID": { "content": "ODA05303000000003"}, "StatusCode": {"content": "MISSING"}}]
}
```

