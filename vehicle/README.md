# Vehicle

Zobrazenie detialov o vozidle.

## API Volanie

### URL

```
https://overenie.digital/api/vehicle
```

### Metóda

```
GET
```
### Parametre JSON dát

| Kľúč		     	| Povinný	| Dĺžka	| Typ		| Predvolené| Akceptovaná hodnota | Popis 									| 
| ----------------	| ---------	| -----	| -----		| ---------	|---------------------|----------------------------------------	|	
| **keyword**		| áno 		| 		| string	|			| 					  | Požiadavka na základe typu EČV/VIN
| **keyword2**		| nie 		| 		| string	|			| 					  | Upresňujúca požiadavka, napr. pri parametri keyword s hodnotou EČV možno pomocou parametru keyword2 upresniť VIN, kedy vráti striktný výsledok konkrétnej kombinácie.
| **type**			| áno 		| 		| string	|			| license_plate, vin  | Typ požiadavky, ktorou sa upresní aký typ dát je očakávaný v parametri keyword.

## Výsledok

Hodnota výsledku je vo formáte podľa typu výsledku (string, int, json, ...), v prípade nezistenia danej hodnotu vracia *null* a v prípade, že na danú hodnotu nemá API oprávnenie, vráti *false*.

## Príklady

### Príklad 1

Získanie vozidla na základe EČV. Výsledok vráti dva výskyty EČV v databáze.

```
curl -X GET \
     -H "Accept: application/json" \
     -H "Version: 1.0" \
     -H "Authorization: Bearer VAS_API_KLUC" \
     -d '{"keyword":"MA834AE","type":"license_plate"}' \
     "https://overenie.digital/api/vehicle"
```

#### Výsledok

``` json
{
    "result": [
        {
            "query": {
                "keyword": "AA001AA",
                "keyword2": "",
                "type": "license_plate"
            },
            "vehicle": {
                "license_plate": "AA001AA",
                "vin": "JF1SG5LW47G123964",
                "brand": "SUBARU",
                "model": "FORESTER",
                "first_evidence": null,
                "first_evidence_local": "1184104800",
                "engine_volume_ccm": "1994",
                "power_kw": "116",
                "color": "\u0160ed\u00c1 metal\u00cdza",
                "fuel": "8",
                "fuel_text": "benz\u00edn + LPG",
                "number_of_doors": null,
                "number_of_seats": "4",
                "date_of_production": null,
                "year_of_production": "2007",
                "body_type": null,
                "body_type_text": "VAN",
                "category": null,
                "category_text": null,
                "weight": "1880",
                "weight_max": null,
                "gearbox": null,
                "gearbox_text": null,
                "gearbox_gears": null,
                "rims": null,
                "tires": null
            },
            "license_plates_used": [
                "BL335JP",
                "PN704BM",
                "PU758AT",
                "PK77777",
                "AA001AA"
            ],
            "vehicles_with_license_plate": [
                {
                    "vin": "JF1SG5LW47G123964",
                    "manufacturer": "SUBARU",
                    "model": "FORESTER",
                    "vehicle_type": "1",
                    "vehicle_type_text": "osobn\u00e9 vozidlo"
                },
                {
                    "vin": "VF3GC9HWC96169767",
                    "manufacturer": "PEUGEOT",
                    "model": "PARTNER",
                    "vehicle_type": "1",
                    "vehicle_type_text": "osobn\u00e9 vozidlo"
                }
            ],
            "overenie_db_vehicle_time_added": "1558361011",
            "overenie_db_vehicle_time_updated": "1708355795",
            "overenie_db_license_plate_time_added": "1678434190",
            "overenie_db_license_plate_time_updated": "1708355795"
        },
        {
            "query": {
                "keyword": "AA001AA",
                "keyword2": "",
                "type": "license_plate"
            },
            "vehicle": {
                "license_plate": "AA001AA",
                "vin": "VF3GC9HWC96169767",
                "brand": "PEUGEOT",
                "model": "PARTNER",
                "first_evidence": null,
                "first_evidence_local": "1134082800",
                "engine_volume_ccm": "1560",
                "power_kw": "55",
                "color": "biela",
                "fuel": "2",
                "fuel_text": "nafta",
                "number_of_doors": "3",
                "number_of_seats": "2",
                "date_of_production": null,
                "year_of_production": "2005",
                "body_type": null,
                "body_type_text": "VAN",
                "category": null,
                "category_text": null,
                "weight": "1930",
                "weight_max": null,
                "gearbox": null,
                "gearbox_text": null,
                "gearbox_gears": null,
                "rims": null,
                "tires": null
            },
            "license_plates_used": [
                "PK859DS",
                "SC570BH",
                "AA001AA",
                "AA777AA",
                "PK021FR",
                "BL335JP",
                "PK474FP",
                "MOSKVIC"
            ],
            "vehicles_with_license_plate": [
                {
                    "vin": "JF1SG5LW47G123964",
                    "manufacturer": "SUBARU",
                    "model": "FORESTER",
                    "vehicle_type": "1",
                    "vehicle_type_text": "osobn\u00e9 vozidlo"
                },
                {
                    "vin": "VF3GC9HWC96169767",
                    "manufacturer": "PEUGEOT",
                    "model": "PARTNER",
                    "vehicle_type": "1",
                    "vehicle_type_text": "osobn\u00e9 vozidlo"
                }
            ],
            "overenie_db_vehicle_time_added": "1608284708",
            "overenie_db_vehicle_time_updated": "1708277398",
            "overenie_db_license_plate_time_added": "1674546407",
            "overenie_db_license_plate_time_updated": "1680423277"
        }
    ],
    "success": true,
    "errors": [],
    "messages": [],
    "time": 1718524651,
    "query": {
        "keyword": "AA001AA",
        "keyword2": "",
        "type": "license_plate"
    },
    "response_time": 2.739990234375
}
```

### Príklad 2

Evidenčné číslo AA001AA bolo umiestnené na viacerých vozidlách, pre výber jedného výsledku konkrétneho vozidla, požiadavku upresníme parametrom keyword2 s VIN číslom vozidla.

```
curl -X GET \
     -H "Accept: application/json" \
     -H "Version: 1.0" \
     -H "Authorization: Bearer VAS_API_KLUC" \
     -d '{"keyword":"AA001AA","keyword2":"VF3GC9HWC96169767", "type":"license_plate"}' \
     "https://overenie.digital/api/vehicle"
```

#### Výsledok

``` json
{
    "result": [
        {
            "query": {
                "keyword": "AA001AA",
                "keyword2": "VF3GC9HWC96169767",
                "type": "license_plate"
            },
            "vehicle": {
                "license_plate": "AA001AA",
                "vin": "VF3GC9HWC96169767",
                "brand": "PEUGEOT",
                "model": "PARTNER",
                "first_evidence": null,
                "first_evidence_local": "1134082800",
                "engine_volume_ccm": "1560",
                "power_kw": "55",
                "color": "biela",
                "fuel": "2",
                "fuel_text": "nafta",
                "number_of_doors": "3",
                "number_of_seats": "2",
                "date_of_production": null,
                "year_of_production": "2005",
                "body_type": null,
                "body_type_text": "VAN",
                "category": null,
                "category_text": null,
                "weight": "1930",
                "weight_max": null,
                "gearbox": null,
                "gearbox_text": null,
                "gearbox_gears": null,
                "rims": null,
                "tires": null
            },
            "license_plates_used": [
                "PK859DS",
                "SC570BH",
                "AA001AA",
                "AA777AA",
                "PK021FR",
                "BL335JP",
                "PK474FP",
                "MOSKVIC"
            ],
            "vehicles_with_license_plate": [
                {
                    "vin": "JF1SG5LW47G123964",
                    "manufacturer": "SUBARU",
                    "model": "FORESTER",
                    "vehicle_type": "1",
                    "vehicle_type_text": "osobn\u00e9 vozidlo"
                },
                {
                    "vin": "VF3GC9HWC96169767",
                    "manufacturer": "PEUGEOT",
                    "model": "PARTNER",
                    "vehicle_type": "1",
                    "vehicle_type_text": "osobn\u00e9 vozidlo"
                }
            ],
            "overenie_db_vehicle_time_added": "1608284708",
            "overenie_db_vehicle_time_updated": "1708277398",
            "overenie_db_license_plate_time_added": "1674546407",
            "overenie_db_license_plate_time_updated": "1680423277"
        }
    ],
    "success": true,
    "errors": [],
    "messages": [],
    "time": 1718524671,
    "query": {
        "keyword": "AA001AA",
        "keyword2": "VF3GC9HWC96169767",
        "type": "license_plate"
    },
    "response_time": 4.93994140625
}
```

### Príklad 3

Výber vozidla podľa VIN čísla.

Nakoľko však nedisponujeme informáciou, ktoré EČV v prípade prenosov bolo použité skôr, predvolene sa ako výsledok hodnoty *license_plate* zobrazuje *null*. 

Pomocou parametru *license_plate_show* v JSON dátach s možnými hodnotami *none*, *one* a *all* možno vo výsledku vrátiť hodnotu nulovú, jedno EČV alebo všetky použíté EČV.

```
curl -X GET \
     -H "Accept: application/json" \
     -H "Version: 1.0" \
     -H "Authorization: Bearer VAS_API_KLUC" \
     -d '{"keyword":"VF3GC9HWC96169767", "type":"vin","license_plate_show":"one"}' \
     "https://overenie.digital/api/vehicle"
```

#### Výsledok

``` json
{
    "result": [
        {
            "vehicle": {
                "license_plate": "FERRARI",
                "vin": "ZFF67NHB000181621",
                "brand": "FERRARI",
                "model": "458",
                "first_evidence": "1310076000",
                "first_evidence_local": "1656626400",
                "engine_volume_ccm": "4497",
                "power_kw": "416.0",
                "color": "\u010cerven\u00e1",
                "fuel": "1",
                "fuel_text": "benz\u00edn",
                "number_of_doors": null,
                "number_of_seats": "2",
                "date_of_production": null,
                "year_of_production": "2011",
                "body_type": null,
                "body_type_text": "AD kup\u00e9",
                "category": null,
                "category_text": "M1 - osobn\u00e9 vozidlo, max. 8 miest na sedenie okrem miesta pre vodi\u010da",
                "weight": "1785",
                "weight_max": null,
                "gearbox": null,
                "gearbox_text": null,
                "gearbox_gears": null,
                "rims": null,
                "tires": null
            },
            "license_plates_used": [
                "FERRARI",
                "FERRAR1",
                "AA063CI",
                "REDHELL"
            ],
            "vehicles_with_license_plate": [
                {
                    "vin": "WF0YXXTTGYJA78718",
                    "manufacturer": "FORD",
                    "model": "Transit Custom",
                    "vehicle_type": "1",
                    "vehicle_type_text": "osobn\u00e9 vozidlo"
                },
                {
                    "vin": "ZFF67NHB000181621",
                    "manufacturer": "FERRARI",
                    "model": null,
                    "vehicle_type": "1",
                    "vehicle_type_text": "osobn\u00e9 vozidlo"
                }
            ],
            "overenie_db_vehicle_time_added": "1681997718",
            "overenie_db_vehicle_time_updated": "1716189647",
            "overenie_db_license_plate_time_added": "",
            "overenie_db_license_plate_time_updated": ""
        }
    ],
    "success": true,
    "errors": [],
    "messages": [],
    "time": 1718524076,
    "query": {
        "keyword": "ZFF67NHB000181621",
        "keyword2": "",
        "type": "vin"
    },
    "response_time": 0.639892578125
}
```

#### Parametre v JSON dátach dostupné v tejto funkcii


| Kľúč		     	| Povinný	| Dĺžka	| Typ		| Predvolené| Akceptovaná hodnota | Popis 									| 
| ----------------	| ---------	| -----	| -----		| ---------	|---------------------|----------------------------------------	|
| **license_plate_show**	| nie			| string	| none	| none, one, all	| Vo výsledku vráti hodnotu license_plate ako null, jedno EČV alebo všetky použité EČV. |