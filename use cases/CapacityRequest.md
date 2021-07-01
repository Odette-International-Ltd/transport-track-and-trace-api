# Use Case Transport Capacity Reservation
Use-Case |	Order transport capacity at a specified LSP for a specified contract relation  
---------|--------------------------------------------------------------------------------
Proposed by|	VDA PG API          
Proposed on|	11.09.2020         
Description|	In certain business scenarios it is sufficient to order transport capacity (loading meters, volume, weight) for a transport rather than specify the complete shipment.     
Actors|	Ship-from, LSP, optional: copy to ship-to / transport ordering party        
Pre-condition|	Contractual relationship between the transport ordering party and identified LSP    
Post-condition|	Confirmation      
Functions|	Create, Update, Read    
Process|	Sender: ship-from, Receiver: LSP,	Opt. Receiver: ship-to, transport ordering party    
Alternative|	VDA 4933 T1 & T2 (transport order & confirmation)  resp. Odette pendants     
Motivation |	Automated, accelerated communication    
Frequency|	As necessary   

A requesting party would first use a POST command to get a unique ID for the capacity reservation:    
```
curl -X 'POST' \
  'https://virtserver.swaggerhub.com/JoergWaltherOdette/vda_odette_ttt/1.0.0/transport-capacity-reservations' \
  -H 'accept: application/json' \
  -d ''
  ```   
The server returns the ID in a JSON structure:
```   
{
  "ReturnedID": {
    "content": "d9cb4b05-6d4d-420a-a18c-0b3875ee828c"
  }
}
```
Then the requesting system uses this ID as path parameter to provide the complete data set with a PUT command: 
 
```JSON
curl -X 'PUT' \
  'https://virtserver.swaggerhub.com/JoergWaltherOdette/vda_odette_ttt/1.0.0/transport-capacity-reservations/d9cb4b05-6d4d-420a-a18c-0b3875ee828c' \
  -H 'accept: application/json' \
  -H 'Content-Type: application/json' \
  -d {
  "ID": {
    "content": "d9cb4b05-6d4d-420a-a18c-0b3875ee828c"
  },
  "TransactionStatusCode": {
    "content": "REQUESTED"
  },
  "IssueDateTime": {
    "content": "2021-07-01T15:44:00Z"
  },
  "PositioningDateTime": {
    "content": "2021-07-02T07:30:00Z"
  },
  "TransportMeansTypeCode": {
    "content": "T01",
    "listAgencyID": "6"
  },
  "TransportMeansNumberNumeric": {
    "content": 1
  },
  "GrossWeightMeasure": {
    "content": 15000,
    "unitCode": "KGM"
  },
  "LoadingMetersMeasure": {
    "content": 10,
    "unitCode": "MTR"
  },
  "GrossVolumeMeasure": {
    "content": 20,
    "unitCode": "MTQ"
  },
  "DeliveryTermsCode": {
    "content": "EXW"
  },
  "ContractReferenceID": {
    "content": "string"
  },
  "SpecifiedTradeParty": [
    {
      "ID": {
        "content": "987654321",
        "schemeAgencyID": "16"
      },
      "Name": {
        "content": "Vereinigter Fahrzeugbau Berlin"
      },
      "RoleCode": {
        "content": "ST",
        "listAgencyID": "6"
      },
      "PostalAddress": [
        {
          "PostcodeCode": {
            "content": "10117"
          },
          "StreetName": {
            "content": "Behrenstraße 35"
          },
          "CityName": {
            "content": "Berlin"
          },
          "CountryID": {
            "content": "DE",
            "schemeAgencyID": "5"
          }
        }
      ],
      "UniversalCommunication": [
        {
          "ChannelCode": {
            "content": "TE"
          },
          "CompleteNumber": {
            "content": "0049 39 8978 420"
          }
        }
      ]
    },
    {
      "ID": {
        "content": "444555666",
        "schemeAgencyID": "16"
      },
      "Name": {
        "content": "Automotive Supplier Ltd."
      },
      "RoleCode": {
        "content": "SF",
        "listAgencyID": "6"
      },
      "PostalAddress": [
        {
          "PostcodeCode": {
            "content": "SW1P 2BN"
          },
          "StreetName": {
            "content": "71 Great Peter Street"
          },
          "CityName": {
            "content": "London"
          },
          "CountryID": {
            "content": "GB"
          }
        }
      ],
    }
  ],
  "LogisticsLocation": [
    {
      "ID": {
        "content": "Loading Dock 15"
      },
      "Name": {
        "content": "Dock 15"
      },
      "TypeCode": {
        "content": "9",
        "listAgencyID": "6"
      }
    },
    {
      "ID": {
        "content": "Abladestelle 23"
      },
      "TypeCode": {
        "content": "11",
        "listAgencyID": "6"
      }
    }
  ]
}
```   

