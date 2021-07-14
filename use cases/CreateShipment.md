# Create Shipment

This transaction stores the details of a shipment (consignment) in the system.
There are mainly two possible data sources:   
* The ship-from party can push the data in preparation of the loading process 
* The logistics service provider can extract the data from a transport order received earlier    

Data set:
Field | Value  
------|------   
Shipment ID: | 2KODA05303020210003 (in this example a globally unique ID assigned by ship-from is used)  
Ship-from ID: | A05303 (Odette ID A053, Sub-entity 03)   
Ship-from address: | 71 Great Peter Street, London, SW1P 2BN, GB
Loading location: | Dock 15
Ship-to ID: | 987654321 (D.U.N.S. number)  
Ship-to address: | Behrenstraße 35, Berlin, 10117, DE   
Unloading location: | Abladestelle 23   
Gross weight: | 15000 kg
Gross volume: | 18 m3
Number of TLU: | 10 (1.2 x 1.0 x 1.5 m each) 
TLU-ID: | 6J (master label) ODA05303000000001..ODA05303000000010    
    
It is assumed that the receiving system checks internally, whether or not the TLU records exist in the system already.    
If yes, the ConsignmentIDs (and potentially other data) have to be checked/updated, if not, the records have to be created by the system itself.    
    

 ```

curl -X 'PUT' \
  'https://virtserver.swaggerhub.com/JoergWaltherOdette/vda_odette_ttt/1.0.0/consignments/2KODA05303020210003' \
  -H 'accept: application/json' \
  -H 'Content-Type: application/json' \
  -d '{
  "ID": {
    "content": "2KODA05303020210003"
  },
  "ConsignorAssignedID": {
    "content": "2KODA05303020210003"
  },
  "GrossWeightMeasure": {
    "content": 15000,
    "unitCode": "KGM"
  },
  "GrossVolumeMeasure": {
    "content": 18,
    "unitCode": "MTQ"
  },
  "ConsignmentItemQuantity": {
    "content": 10
  },
  "StatusCode": {
    "content": "NO_STATUS"
  },
  "SpecifiedDeliveryTerms": {
    "DeliveryTypeCode": {
      "content": "EXW"
    },
    "Description": {
      "content": "Ex work London"
    },
  "IncludedConsignmentItem": [
    {
      "ID": {
        "content": "6JODA05303000000001"
      },
      "SequenceNumeric": {
        "content": 1
      },
      "GrossWeightMeasure": {
        "content": 0,
        "unitCode": "KGM"
      },
      "NetWeightMeasure": {
        "content": 1500,
        "unitCode": "KGM"
      },
      "GrossVolumeMeasure": {
        "content": 1.8,
        "unitCode": "MTQ"
      },
      "PackageType": {
        "content": "string",
        "languageID": "aa"
      },
      "ConsignmentID": {
        "content": "string"
      },
      "StatusCode": {
        "content": "NO_STATUS"
      },
      "LinearDimension": {
        "WidthMeasure": {
          "content": 100,
          "unitCode": "CMT"
        },
        "LengthMeasure": {
          "content": 120,
          "unitCode": "CMT"
        },
        "HeightMeasure": {
          "content": 150,
          "unitCode": "CMT"
        },
      },
      "OriginCountry": {
        "ID": {
          "content": "GB"
        },
      },
      "LogisticsLabelShippingMarks": [
        {
          "LogisticsLabel": {
            "ID": {
              "content": "6JODA05303000000001"
            },
            "LayoutTypeCode": {
              "content": "GTL3"
            },
            "SizeCode": {
              "content": "A5"
            },
          }
        }
      ],
    }
  ],
  "ConsignmentParty": {
    "ID": {
      "content": "string",
      "schemeAgencyID": "10"
    },
    "Name": {
      "content": "string",
      "languageID": "aa"
    },
    "RoleCode": {
      "content": "CA"
    },
    "PostalAddress": {
      "PostcodeCode": {
        "content": "string"
      },
      "StreetName": {
        "content": "string"
      },
      "CityName": {
        "content": "string"
      },
      "CountryID": {
        "content": "AD"
      },
      "CountryName": {
        "content": "string"
      },
      "CountrySub-DivisionName": {
        "content": "string"
      }
    },
    "UniversalCommunication": [
      {
        "ChannelCode": {
          "content": "AL"
        },
        "CompleteNumber": {
          "content": "string",
          "languageID": "aa"
        }
      }
    ]
  },
  "LogisticsLocation": {
    "ID": {
      "content": "string"
    },
    "Name": {
      "content": "string",
      "languageID": "aa"
    },
    "TypeCode": {
      "content": "9"
    },
    "CountryID": {
      "content": "AD"
    },
    "CountrySub-DivisionID": {
      "content": "string"
    },
    "PhysicalGeographicalCoordinate": {
      "AltitudeMeasure": {
        "content": 0,
        "unitCode": "MTR"
      },
      "LatitudeMeasure": {
        "content": 0,
        "unitCode": "DD"
      },
      "LongitudeMeasure": {
        "content": 0,
        "unitCode": "DD"
      },
      "LatitudeDirectionIndicator": {
        "content": "string"
      },
      "LongitudeDirectionIndicator": {
        "content": "string"
      },
      "SystemID": {
        "content": "string"
      }
    }
  },
  "HandlingInstructions": {
    "Description": {
      "content": "string",
      "languageID": "aa"
    },
    "DescriptionCode": {
      "content": "string"
    },
    "MaximumStackabilityWeightApplicableMeasure": {
      "content": 0,
      "unitCode": "KGM"
    },
    "MaximumStackabilityApplicableQuantity": {
      "content": 0
    },
    "MaximumStorageHumidityApplicableMeasure": {
      "content": 0,
      "unitCode": "P1"
    },
    "MinimumStorageHumidityApplicableMeasure": {
      "content": 0,
      "unitCode": "P1"
    },
    "InstructedTemperature": [
      {
        "MaximumValueMeasure": {
          "content": 0,
          "unitCode": "CEL"
        },
        "MinimumValueMeasure": {
          "content": 0,
          "unitCode": "CEL"
        },
        "TypeCode": {
          "content": "STORAGE"
        }
      }
    ]
  }
}'
```
