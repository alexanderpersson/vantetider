vantetider
==========

Api documentation for vantetider which lists time to operation in sweden. 

[Site url](http://www.vantetider.se/): http://www.vantetider.se/

[Api url](http://www.vantetider.se/api/Ajax/): http://www.vantetider.se/api/Ajax/

The api consist of two (known) methods, one to get the available services linked to a category and the other to list the waiting time and capacity for that service. 

Get services
-----------
/GetServicesByArea/{id}

Where {id} is either:
  1. Visit
  2. Examination
  3. Operation

Response is in json and looks like: 

> {
    "Services": [
        {
            "id": 113,
            "Parent_id": 19,
            "Disabled": false,
            "Uppdaterad": "2012-08-21T13:36:49",
            "Name": "Magsäck - kirurgi (gastroskopi på kirurgisk enhet)",
            "Servicecode": "10502",
            "Dtype": "PhysicalService"
        }, 
        {
            "id": 111,
            "Parent_id": 19,
            "Disabled": false,
            "Uppdaterad": "2012-08-21T13:36:49",
            "Name": "Tjocktarm- medicin (koloskopi på medicinsk enhet)",
            "Servicecode": "10506",
            "Dtype": "PhysicalService"
        }
    ]
}

{id} can also be one of the Parent_id from response to only get items in from the same group.

Get waiting and capacity
-----------

/GetWaitingAndCapacityByService/{servicecode}

Where {servicecode} is the servicecode we got from the first request.

Response is in json and looks like: 

> {
    "aaData": [
        {
            "regionId": 51,
            "unitId": 3147,
            "regionName": "Västra Götalandsregionen",
            "unitName": "NU-sjukvården (NÄL, Uddevalla, Dalsland, Lysekil, Strömstad)",
            "Waiting": "9 - 13 veckor",
            "Capacity": "Nej",
            "Updated": "2014-05-23",
            "Contact": "",
            "Comment": "",
            "URL": "",
            "Email": ""
        },       
        {
            "regionId": 42,
            "unitId": 3065,
            "regionName": "Region Halland",
            "unitName": "Hallands sjukhus Halmstad",
            "Waiting": "9 - 13 veckor",
            "Capacity": "Nej",
            "Updated": "2014-04-01",
            "Contact": "",
            "Comment": "",
            "URL": "",
            "Email": ""
        }
    ]
}

Notice the regionId which is used to group several items together.
          <ul>
            <li>id:27 Blekinge</li>
            <li>id:57 Dalarna</li>
            <li>id:26 Gotland</li>
            <li>id:61 Gävleborg</li>
            <li>id:42 Halland</li>
            <li>id:63 Jämtland</li>
            <li>id:22 Jönköping</li>
            <li>id:24 Kalmar</li>
            <li>id:23 Kronoberg</li>
            <li>id:65 Norrbotten</li>
            <li>id:41 Skåne</li>
            <li>id:10 Stockholm</li>
            <li>id:13 Sörmland</li>
            <li>id:12 Uppsala</li>
            <li>id:54 Värmland</li>
            <li>id:64 Västerbotten</li>
            <li>id:62 Västernorrland</li>
            <li>id:56 Västmanland</li>
            <li>id:51 Västa Götaland</li>
            <li>id:55 Örebro</li>
            <li>id:21 Östergötland</li>
          </ul>
