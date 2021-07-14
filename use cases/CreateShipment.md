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
    "content": "string"
  },
  "ConsignorAssignedID": {
    "content": "string"
  },
  "ConsigneeAssignedID": {
    "content": "string"
  },
  "CustomsID": {
    "content": "string"
  },
  "CarrierAssignedID": {
    "content": "string"
  },
  "FreightForwarderAssignedID": {
    "content": "string"
  },
  "TradedParcelID": {
    "content": "string"
  },
  "LoadingSequenceNumeric": {
    "content": 0
  },
  "GrossWeightMeasure": {
    "content": 0,
    "unitCode": "KGM"
  },
  "NetWeightMeasure": {
    "content": 0,
    "unitCode": "KGM"
  },
  "GrossVolumeMeasure": {
    "content": 0,
    "unitCode": "CMQ"
  },
  "LoadingLengthMeasure": {
    "content": 0,
    "unitCode": "CMT"
  },
  "ChargeableWeightMeasure": {
    "content": 0,
    "unitCode": "KGM"
  },
  "ConsignmentItemQuantity": {
    "content": 0
  },
  "StatusCode": {
    "content": "NO_STATUS"
  },
  "AssociatedDocument": [
    {
      "ID": {
        "content": "string"
      },
      "ReferenceTypeCode": {
        "content": "AAA"
      },
      "LanguageID": {
        "content": "aa"
      },
      "FormattedIssueDateTime": {
        "content": "string"
      },
      "SubordinateLineID": {
        "content": "string"
      },
      "AttachedBinaryFile": [
        {
          "ID": {
            "content": "string"
          },
          "Title": {
            "content": "string",
            "languageID": "aa"
          },
          "FileName": {
            "content": "string"
          },
          "URIID": {
            "content": "string"
          },
          "MIMECode": {
            "content": "application/pdf"
          },
          "EncodingCode": {
            "content": "1"
          },
          "CharacterSetCode": {
            "content": "3"
          },
          "IncludedBinaryObject": {
            "content": "string"
          },
          "Access": {
            "content": "string",
            "languageID": "aa"
          },
          "Description": {
            "content": "string",
            "languageID": "aa"
          },
          "SizeMeasure": {
            "content": 0,
            "unitCode": "4L"
          }
        }
      ]
    }
  ],
  "UtilizedTransportEquipment": [
    {
      "ID": {
        "content": "string"
      },
      "CategoryCode": {
        "content": "AE"
      }
    }
  ],
  "SpecifiedTransportMovement": [
    {
      "StageCode": {
        "content": "12",
        "listAgencyID": "6"
      },
      "ModeCode": {
        "content": "0"
      },
      "ID": {
        "content": "string"
      }
    }
  ],
  "SpecifiedDeliveryTerms": {
    "DeliveryTypeCode": {
      "content": "1"
    },
    "Description": {
      "content": "string"
    },
    "PartialDeliveryAllowedIndicator": {
      "content": "string"
    },
    "RelevantLocation": {
      "ID": {
        "content": "string"
      },
      "Name": {
        "content": "string",
        "languageID": "aa"
      }
    }
  },
  "SpecifiedReference": [
    {
      "TypeCode": {
        "content": "AAA"
      },
      "ID": {
        "content": "string"
      }
    }
  ],
  "IncludedConsignmentItem": [
    {
      "ID": {
        "content": "string"
      },
      "SequenceNumeric": {
        "content": 0
      },
      "TypeCode": {
        "content": "ZZZ"
      },
      "GrossWeightMeasure": {
        "content": 0,
        "unitCode": "KGM"
      },
      "NetWeightMeasure": {
        "content": 0,
        "unitCode": "KGM"
      },
      "GrossVolumeMeasure": {
        "content": 0,
        "unitCode": "CMQ"
      },
      "PackageType": {
        "content": "string",
        "languageID": "aa"
      },
      "ConsignmentID": {
        "content": "string"
      },
      "StatusCode": {
        "content": "ACCEPTANCE_REFUSED_BY_SHIP_TO"
      },
      "LinearDimension": {
        "WidthMeasure": {
          "content": 0,
          "unitCode": "CMT"
        },
        "LengthMeasure": {
          "content": 0,
          "unitCode": "CMT"
        },
        "HeightMeasure": {
          "content": 0,
          "unitCode": "CMT"
        },
        "DiameterMeasure": {
          "content": 0,
          "unitCode": "CMT"
        }
      },
      "OriginCountry": {
        "ID": {
          "content": "AD"
        },
        "Name": {
          "content": "string",
          "languageID": "aa"
        }
      },
      "RelatedEvent": [
        {
          "ID": {
            "content": "string"
          }
        }
      ],
      "LogisticsLabelShippingMarks": [
        {
          "Marking": {
            "content": "string",
            "languageID": "aa"
          },
          "LogisticsLabel": {
            "ID": {
              "content": "string"
            },
            "LayoutTypeCode": {
              "content": "ETI9"
            },
            "SizeCode": {
              "content": "A5"
            },
            "TechnologyCode": {
              "content": "BARCODE"
            }
          }
        }
      ],
      "HandlingInstructions": {
        "Description": {
          "content": "string",
          "languageID": "aa"
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
    }
  ],
  "RelatedEvent": [
    {
      "ID": {
        "content": "string"
      }
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
