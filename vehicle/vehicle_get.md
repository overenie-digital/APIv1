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
            "license_plate": "MA834AE",
            "vin": "449364",
            "date_of_first_evidence_local": "1640041200",
            "manufacturer": "BABETTA",
            "model": "BABETTA 210",
            "engine_volume_ccm": "49",
            "power_kw": "1",
            "fuel": "1",
            "fuel_text": "benz\u00edn",
            "number_of_doors": null,
            "number_of_seats": "1",
            "year_of_production": null,
            "body_type": "MOPED",
            "vehicle_type": "10",
            "vehicle_type_text": "moped",
            "weight": "145",
            "color": "\u010cerven\u00e1",
            "license_plate_history": [
                "MA834AE"
            ],
            "vehicles_with_license_plate": [
                {
                    "vin": "449364",
                    "manufacturer": "BABETTA",
                    "model": "BABETTA 210",
                    "vehicle_type": "10",
                    "vehicle_type_text": "moped"
                },
                {
                    "vin": "TMBZZZ1U9W2118371",
                    "manufacturer": "\u0160KODA",
                    "model": "Octavia",
                    "vehicle_type": false,
                    "vehicle_type_text": false
                }
            ],
            "overenie_db_vehicle_time_added": "1669815677",
            "overenie_db_vehicle_time_updated": "1672770168",
            "overenie_db_license_plate_time_added": "1669815677",
            "overenie_db_license_plate_time_updated": "1672770168"
        },
        {
            "license_plate": "MA834AE",
            "vin": "TMBZZZ1U9W2118371",
            "date_of_first_evidence_local": "883609200",
            "manufacturer": "\u0160KODA",
            "model": "Octavia",
            "engine_volume_ccm": "1598",
            "power_kw": "55",
            "fuel": "1",
            "fuel_text": "benz\u00edn",
            "number_of_doors": null,
            "number_of_seats": "5",
            "year_of_production": null,
            "body_type": null,
            "vehicle_type": null,
            "vehicle_type_text": null,
            "weight": "1670",
            "color": "zelen\u00c1 metal\u00cdza",
            "license_plate_history": [
                "MA834AE"
            ],
            "vehicles_with_license_plate": [
                {
                    "vin": "449364",
                    "manufacturer": "BABETTA",
                    "model": "BABETTA 210",
                    "vehicle_type": "10",
                    "vehicle_type_text": "moped"
                },
                {
                    "vin": "TMBZZZ1U9W2118371",
                    "manufacturer": "\u0160KODA",
                    "model": "Octavia",
                    "vehicle_type": false,
                    "vehicle_type_text": false
                }
            ],
            "overenie_db_vehicle_time_added": "1595752684",
            "overenie_db_vehicle_time_updated": "1595752684",
            "overenie_db_license_plate_time_added": "1669815687",
            "overenie_db_license_plate_time_updated": "1669815687"
        }
    ],
    "success": true,
    "errors": [],
    "messages": [],
    "time": 1718220925,
    "response_time": 616.010009765625
}
```

### Príklad 2

Evidenčné číslo AA001AA bolo umiestnené na viacerých vozidlách, pre výber jedného výsledku konkrétneho vozidla, požiadavku upresníme parametrom keyword2 s VIN číslom vozidla.

```
curl -X GET \
     -H "Accept: application/json" \
     -H "Version: 1.0" \
     -H "Authorization: Bearer VAS_API_KLUC" \
     -d '{"AA001AA":"MA834AE","keyword":"VF3GC9HWC96169767", "type":"license_plate"}' \
     "https://overenie.digital/api/vehicle"
```

#### Výsledok

``` json
{
    "result": [
        {
            "license_plate": "AA001AA",
            "vin": "VF3GC9HWC96169767",
            "date_of_first_evidence_local": "1134082800",
            "manufacturer": "PEUGEOT",
            "model": "PARTNER",
            "engine_volume_ccm": "1560",
            "power_kw": "55",
            "fuel": "2",
            "fuel_text": "nafta",
            "number_of_doors": "3",
            "number_of_seats": "2",
            "year_of_production": "2005",
            "body_type": "VAN",
            "vehicle_type": "1",
            "vehicle_type_text": "osobn\u00e9 vozidlo",
            "weight": "1930",
            "color": "biela",
            "license_plate_history": [
                "MOSKVIC",
                "AA777AA",
                "PK474FP",
                "PK021FR",
                "AA001AA",
                "BL335JP",
                "PK859DS",
                "SC570BH"
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
    "time": 1718220902,
    "response_time": 630.110107421875
}
```

### Príklad 3

Výber vozidla podľa VIN čísla.

```
curl -X GET \
     -H "Accept: application/json" \
     -H "Version: 1.0" \
     -H "Authorization: Bearer VAS_API_KLUC" \
     -d '{"keyword":"VF3GC9HWC96169767", "type":"vin"}' \
     "https://overenie.digital/api/vehicle"
```

#### Výsledok

``` json
{
    "result": [
        {
            "license_plate": "SC570BH",
            "vin": "VF3GC9HWC96169767",
            "date_of_first_evidence_local": "1134082800",
            "manufacturer": "PEUGEOT",
            "model": "PARTNER",
            "engine_volume_ccm": "1560",
            "power_kw": "55",
            "fuel": "2",
            "fuel_text": "nafta",
            "number_of_doors": "3",
            "number_of_seats": "2",
            "year_of_production": "2005",
            "body_type": "VAN",
            "vehicle_type": "1",
            "vehicle_type_text": "osobn\u00e9 vozidlo",
            "weight": "1930",
            "color": "biela",
            "license_plate_history": [
                "MOSKVIC",
                "AA777AA",
                "PK474FP",
                "PK021FR",
                "AA001AA",
                "BL335JP",
                "PK859DS",
                "SC570BH"
            ],
            "vehicles_with_license_plate": [
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
            "overenie_db_license_plate_time_added": "1660133100",
            "overenie_db_license_plate_time_updated": "1660133100"
        }
    ],
    "success": true,
    "errors": [],
    "messages": [],
    "time": 1718220880,
    "response_time": 1934.5400390625
}
```
