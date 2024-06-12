# overenie.digital API v1

## API Kľúč

Ak máte záujem o API prístup (kľúč), [kontaktujte nás](https://overenie.digital/kontakt) s krátkym popisom, na aké účely API prístup potrebujete (napr. či ide komerčný projekt alebo neziskový, či budú údaje z API dostupné
verejne a pod.). Viac informácií nájdete na [portáli overenie.digital](https://overenie.digital/api).


## List of functions

Podrobný popis každej funkcie sa nachádza v priečinkoch tohto repozitára.

| Name		     		| Type		| Description	| 
| ----------------		| ---------	| -------------	|
| **vehicle**			| GET 		| Získa základné údaje o vozidle podľa EČV alebo VIN |



## Požiadavka

Požiadavka sa skladá z metódy, headerov, dát a URL adresy.

| Header	     		| Povinný	| Akceptované hodnoty | Popis	| 
| ----------------		| ---------	| -------------		  | -------------	|
| **Accept**			| áno 		| application/json	  | Akceptovaný formát odpovede. |
| **Version**			| áno 		| 1.0				  | Verzia API. |
| **Authorization**		| áno 		| Bearer VAS_API_KLUC | Miesto pre váš API kľúč. |

Požiadavku odosielajte požadovanou metódou (GET/POST/PUT/...) zapísanou pri každej API funkcii a dátami vo formáte JSON.


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
            "license_plate_history": [],
            "vehicles_with_license_plate": [
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
            "license_plate_history": [],
            "vehicles_with_license_plate": [
                {
                    "vin": "449364",
                    "manufacturer": "BABETTA",
                    "model": "BABETTA 210",
                    "vehicle_type": "10",
                    "vehicle_type_text": "moped"
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
    "time": 1718217932,
    "response_time": 845.969970703125
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

## Optional parameters available in all API functions

| Name		     	| Length	| Type		| Default	| Valid values	| Description 	|
| ----------------	| --------	| -----		| ---------	|--------------	| -------------	|
| **json_format**	| 			| string	| min		| min, pretty	| Format of JSON result |