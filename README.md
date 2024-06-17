# overenie.digital API v1

## API Kľúč

Ak máte záujem o API prístup (kľúč), [kontaktujte nás](https://overenie.digital/kontakt) s krátkym popisom, na aké účely API prístup potrebujete (napr. či ide komerčný projekt alebo neziskový, či budú údaje z API dostupné
verejne a pod.). Viac informácií nájdete na [portáli overenie.digital](https://overenie.digital/api).


## Zoznam funkcií

Podrobný popis každej funkcie sa nachádza v priečinkoch tohto repozitára.

| Názov funkcie    		| Metóda	| Popis			| 
| ----------------		| ---------	| -------------	|
| **vehicle**			| GET 		| Získa základné údaje o vozidle podľa EČV alebo VIN |



## Požiadavka

Požiadavka sa skladá z metódy, headerov, dát a URL adresy.

| Header	     		| Povinný	| Akceptované hodnoty | Popis	| 
| ----------------		| ---------	| -------------		  | -------------	|
| **Accept**			| áno 		| application/json	  | Akceptovaný formát odpovede. |
| **Version**			| áno 		| 1.0				  | Verzia API. |
| **Authorization**		| áno 		| Bearer VAS_API_KLUC | Miesto pre váš API kľúč. |

Požiadavku odosielajte požadovanou metódou (GET/POST/PUT/...) zapísanou pri každej API funkcii a parametrami v dátach, vo formáte JSON.


```
curl -X METHOD \
     -H "Accept: AKCEPTOVANY_FORMAT" \
     -H "Version: API_VERZIA" \
     -H "Authorization: Bearer VAS_API_KLUC" \
     -d DATA_V_JSON_FORMATE \
     "https://overenie.digital/api/NAZOV_API_FUNCKIE"
```

## Príklad úspešného API výsledku

### Ukážka požiadavky

```
curl -X GET \
     -H "Accept: application/json" \
     -H "Version: 1.0" \
     -H "Authorization: Bearer VAS_API_KLUC" \
     -d '{"keyword":"MA834AE","type":"license_plate"}' \
     "https://overenie.digital/api/vehicle"
```

### Výsledok

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
    "time": 1718524764,
    "query": {
        "keyword": "AA001AA",
        "keyword2": "",
        "type": "license_plate"
    },
    "response_time": 3.0400390625
}
```

## Príklady chybových API výsledkov

### Chybajúce povinné parametre

``` json
{
    "result": null,
    "success": false,
    "errors": [
        {
            "code": 1001,
            "message": "Empty API key in Authorization header."
        }
    ],
    "messages": [],
    "time": 1718215734
}
```

### Dosiahnutý počet volaní funkcie

``` json
{
    "result": null,
    "success": false,
    "errors": [
        {
            "code": 1007,
            "message": "API exceeds limit of function calls."
        }
    ],
    "messages": [
        "This function has 33 calls for last 24 hours.",
        "Maximum calls of this function is 30 for last 24 hours."
    ],
    "time": 1718215972
}
```

---

## Nepovinné parametre v JSON dátach dostupné v každej funkcii

| Kľúč		     	| Povinný	| Dĺžka	| Typ		| Predvolené| Akceptovaná hodnota | Popis 									| 
| ----------------	| ---------	| -----	| -----		| ---------	|---------------------|----------------------------------------	|
| **json_format**	| nie			| string	| min	| min, pretty	| Formát JSON výsledku. |