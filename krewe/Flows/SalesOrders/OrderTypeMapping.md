# Order Type

## What are Order Types?
Order types help Krewe categorize their orders based on a variety of business cases. Some may be related to seasonal events such as Mardi Gras while others simply identify that an order is an Employee Order. These order types eventually help Krewe run analyitcs on their orders and identify issues or measure sale performance.

**From NetSuite Documentation:**
The order type is a category that associates attributes to sales and transfer orders. In NetSuite WMS, you can create an accounting list of multiple order types and associate each outbound sales or transfer order with one order type.

## How they're setup in HotWax
Order types are determined by either by the Shopify Source of the order or the the facility the order is placed from if its a POS sale. Before HotWax, this information was mapped from Shopify Source and Location ID to NetSuite Order Type using a Celigo Script.

In order to map a custom NetSuite value for each Sales Channel, we've effectively added an external ID to that sales channel. Each sales channel in HotWax Commerce is stored in the list of enumerations of the system. Enumerations have a field "Enum Code" which can be used to store an external identification value, this is where we store the NetSuite Order Type to be used during order sync.

For mapping source based on POS facility ID, Krewe will be able to add custom Facility Identifications, allowing them to map custom values to each facility they setup. The identification types will have to be predetermined so that when HotWax syncs the order to NetSuite it is able to check specifically the Sales Channel type of facility identification and include it in the order.

Order Type value for POS channel order will be 6 by default unless there is a facility identification for Order Type in which case the default value will be overridden. 

Facility Identification Type
```
NETSUITE_ORDR_TYPE
```

## All Order Types
| Internal ID | Name                           |
|-------------|--------------------------------|
| 1           | WEB                            |
| 6           | IN-STORE                       |
| 7           | OPENING                        |
| 8           | PRE-ORDER                      |
| 9           | BACKORDER                      |
| 10          | REORDER                        |
| 107         | WARRANTY                       |
| 108         | SAMPLE SALE                    |
| 109         | PRIVATE EVENT                  |
| 110         | MANUFACTURING DEFECT           |
| 111         | GIFTING PULL                   |
| 112         | PR MEDIA                        |
| 113         | EXCHANGE                       |
| 114         | EMPLOYEE ORDER                  |
| 115         | LOST PACKAGE                    |
| 116         | REPLACEMENT                     |
| 117         | CONSIGNMENT                     |
| 118         | KREWE Foundation                |
| 119         | MIS-PICK                        |
| 120         | ACL                             |
| 121         | BLACK FRIDAY/CYBER MONDAY       |
| 122         | Manufacturing Pull              |
| 123         | DONATION                        |
| 124         | CUSTOMER SERVICE                |
| 125         | CORPORATE GIFTING               |
| 126         | LOFT                            |
| 127         | OPTICAL ORDER                   |
| 129         | OUT OF STOCK                    |
| 130         | SHOPIFY DOWN                    |
| 131         | DOA                             |
| 133         | TEST                            |
| 134         | APRIL SALE                      |
| 136         | AMAZON                          |
| 137         | PR CELEBRITY                    |
| 138         | PR INFLUENCER                   |
| 139         | KREWE Anniversary               |
| 140         | USO WARRANTY                    |
| 141         | ORDER ERROR                     |
| 142         | TRUNKSHOW                       |
| 143         | SUPPLY ORDER FOR RETAIL         |
| 144         | ASSOCIATE DAMAGE                 |
| 145         | INSTAGRAM                       |
| 146         | WHOLESALE BLUE LIGHT            |
| 147         | VISION EXPO                     |
| 149         | REMAKE - USO                    |
| 150         | REMAKE - KREWE LAB              |
| 151         | FACEBOOK                        |
| 152         | EVENTING                        |
| 156         | GLOBAL-E                        |
| 157         | STORE CREDIT                    |
| 158         | GIFT EXCHANGE                   |
| 159         | LAB DAMAGE                      |
| 160         | FRAME DAMAGED BY CASE           |
| 161         | TRADESHOW                       |
| 162         | SUPPLY ORDER FOR RETAIL         |
| 163         | SUPPLY                          |
| 164         | MARDI GRAS                      |
| 165         | LOOP EXCHANGE                   |
| 166         | WHOLESALE SAMPLES               |
| 167         | WHOLESALE SAMPLES               |


## Source Data
```
{{#compare source_name '==' 'sell-on-amazon'}}136{{else compare source_name '=='  '2329312'}}145{{else compare source_name '==' '580111'}}151{{else compare source_name '=='  '1498281'}}156{{else compare source_name '==' 'pos'}}{{#compare location_id '=='  '30696177751'}}6{{else compare location_id '==' '30696210519'}}6{{else compare location_id '=='  '62714806359'}}6{{else compare location_id '==' '62714773591'}}6{{else compare location_id '=='  '31137890391'}}6{{else compare location_id '==' '35758243927'}}6{{else compare location_id '=='  '35764404311'}}6{{else compare location_id '==' '35781869655'}}6{{else compare location_id '=='  '35698901079'}}6{{else compare location_id '==' '61327048791'}}6{{else compare location_id '=='  '60903391319'}}6{{else compare location_id '==' '60903424087'}}6{{else compare location_id '=='  '60912140375'}}6{{else compare location_id '==' '60914499671'}}6{{else compare location_id '=='  '62191239255'}}6{{else compare location_id '==' '62571642967'}}6{{else compare location_id '=='  '62743052375'}}152{{else compare location_id '==' '62762614871'}}6{{else compare location_id '=='  '62739513431'}}6{{else compare location_id '==' '34464825431'}}152{{else compare location_id '=='  '62750916695'}}6{{else compare location_id '==' '31157780567'}}6{{else compare location_id '=='  '34465185879'}}152{{else compare location_id '==' '30696341591'}}152{{else compare location_id '=='  '62759370839'}}152{{else compare location_id '==' '62050500695'}}152{{else compare location_id '=='  '62778048599'}}6{{else compare location_id '==' '62288560215'}}152{{else compare location_id '=='  '62776344663'}}152{{else}}{{else}}1{{/compare}}{{else}}1{{/compare}}
```

## Formatted
```
{{#compare source_name '==' 'sell-on-amazon'}}
136
{{else compare source_name '==' '2329312'}}
145
{{else compare source_name '==' '580111'}}
151
{{else compare source_name '==' '1498281'}}
156
{{else compare source_name '==' 'pos'}}
    {{#compare location_id '==' '30696177751'}}
        6
    {{else compare location_id '==' '30696210519'}}
        6
    {{else compare location_id '==' '62714806359'}}
        6
    {{else compare location_id '==' '62714773591'}}
        6
    {{else compare location_id '==' '31137890391'}}
        6
    {{else compare location_id '==' '35758243927'}}
        6
    {{else compare location_id '==' '35764404311'}}
        6
    {{else compare location_id '==' '35781869655'}}
        6
    {{else compare location_id '==' '35698901079'}}
        6
    {{else compare location_id '==' '61327048791'}}
        6
    {{else compare location_id '==' '60903391319'}}
        6
    {{else compare location_id '==' '60903424087'}}
        6
    {{else compare location_id '==' '60912140375'}}
        6
    {{else compare location_id '==' '60914499671'}}
        6
    {{else compare location_id '==' '62191239255'}}
        6
    {{else compare location_id '==' '62571642967'}}
        6
    {{else compare location_id '==' '62743052375'}}
        152
    {{else compare location_id '==' '62762614871'}}
        6
    {{else compare location_id '==' '62739513431'}}
        6
    {{else compare location_id '==' '34464825431'}}
        152
    {{else compare location_id '==' '62750916695'}}
        6
    {{else compare location_id '==' '31157780567'}}
        6
    {{else compare location_id '==' '34465185879'}}
        152
    {{else compare location_id '==' '30696341591'}}
        152
    {{else compare location_id '==' '62759370839'}}
        152
    {{else compare location_id '==' '62050500695'}}
        152
    {{else compare location_id '==' '62778048599'}}
        6
    {{else compare location_id '==' '62288560215'}}
        152
    {{else compare location_id '==' '62776344663'}}
        152
    {{else}}
        1
    {{/compare}}
{{/compare}}
```

## Refactored
```
{
  "source_name": {
    "sell-on-amazon": 136,
    "2329312": 145,
    "580111": 151,
    "1498281": 156,
    "pos": {
      "location_id": {
        "30696177751": 6,
        "30696210519": 6,
        "62714806359": 6,
        "62714773591": 6,
        "31137890391": 6,
        "35758243927": 6,
        "35764404311": 6,
        "35781869655": 6,
        "35698901079": 6,
        "61327048791": 6,
        "60903391319": 6,
        "60903424087": 6,
        "60912140375": 6,
        "60914499671": 6,
        "62191239255": 6,
        "62571642967": 6,
        "62743052375": 152,
        "62762614871": 6,
        "62739513431": 6,
        "34464825431": 152,
        "62750916695": 6,
        "31157780567": 6,
        "34465185879": 152,
        "30696341591": 152,
        "62759370839": 152,
        "62050500695": 152,
        "62778048599": 6,
        "62288560215": 152,
        "62776344663": 152
      }
    }
  }
}
```
