

## Visits
| Verb | Endpoint | Returns |
|-|-|-|-|
| GET | /api/visits | List of visits (limit 50) |

```
// TODO: add part parameter
{
  "id": 1,
  "bird": {
    "id": "011017121E",
    "bandCombo": "#O/wg"
  },
  "feeder": {
    "id": "HMST",
    "name": "Homestead" 
  },
  "timestamp": 1506782685
}
```

## Birds
| Verb | Endpoint | Returns |
|-|-|-|
| GET | /api/birds | Dictionary of birds, keyed by id (rfid) |
| GET | /api/birds/:id | The bird |

```
TODO: netEnter, netExit, and release are the same most of the time. Maybe only keep release.

// proposed format

{
  "id": "011016A269",
  "bandCombo": "g0/Y#",
  "biometrics": {
    "species": "RBNU",
    "sex": "female",
    "tail": 37,
    "wingChord": 66,
    "longestSecondary": 54,
    "bill": {
      "depth": 3.5,
      "width": 3.4,
      "length": 10.3
    },
    "bib": 0,
    "cap": 0,
    "tarsus": 16.5,
    "weight": 10.2,
    "tissueSample": "feather"
  },
  "details": {
    "captureSite": "Carpenter Net",
    "bandNumber":" 2830-56001",
    "bagWeight": 12.3,
    "bagAndBirdWeight": 22.5,
    "notes": "hallux 8.8",
    "weather": "Clear, 55F",
    "banders": "Lindsay, Szarmach"
  },
  "timestamps": {
    "log": 1507579380,
    "capture": 1507296600, 
    "netEnter": 1507262400,
    "netExit": 1507262400,
    "release": 1507262400
  }
}
```

## Feeders
| Verb | Endpoint | Returns |
|-|-|-|
| GET | /api/feeders | Dictionary of feeders, keyed by id |
| GET | /api/feeders/:id | The feeder |

```
{
  "id": "HMST",
  "name": "Homestead",
  "location": {
    "latitude": 46.55458,
    "longitude": -87.433253
  }
}
```

notes:

start MySQL:
sudo /etc/init.d/mysql start
mysql -u root -p

mysql dbname < chickadees.sql
OR
mysql -u root -p jpcp_dev < chickadees.sql
OR
mysql -u root -p jpcp_dev < src/migration/initial-create.sql



##setting up the database for development
make sure this project isn't currently running
mysql -u root -p
create database jpcp_dev;
mysql -u root -p jpcp_dev < src/migration/chickadees.sql (NOT TRACKED)
npm run migrate:up
