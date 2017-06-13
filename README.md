# 1. Goals

The CSIRTG Indicator protocol is a simple protocol for describing threat intelligence indicators.

* To enable simple and easy to digest threat intelligence information

# 2. License

This Specification is free software; you can redistribute it and/or modify it under the terms of the GNU Lesser General Public License as published by the Free Software Foundation; either version 3 of the License, or (at your option) any later version.

This Specification is distributed in the hope that it will be useful, but WITHOUT ANY WARRANTY; without even the implied warranty of MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE. See the GNU Lesser General Public License for more details.

You should have received a copy of the GNU Lesser General Public License along with this program; if not, see <http://www.gnu.org/licenses>.

# 3. Change Process

This document is governed by the [Consensus-Oriented Specification System (COSS)](http://www.digistan.org/spec:1/COSS). In addition:

* Comments MUST be logged as [new issues](https://github.com/blog/411-github-issue-tracker).
* Contributions MUST be logged as [new pull-requests](https://help.github.com/articles/creating-a-pull-request).

# 4. Language

The key words "MUST", "MUST NOT", "REQUIRED", "SHALL", "SHALL NOT", "SHOULD", "SHOULD NOT", "RECOMMENDED", "MAY", and "OPTIONAL" in this document are to be interpreted as described in [RFC 2119](http://www.ietf.org/rfc/rfc2119.txt).

# 5. Protocol
## Indicator Class
The Indicator class is the top level class for describing indicator information. For each class, the semantics will be described and the relationship with other classes will be depicted with UML. 

```
+---------------+
| Indicator     |
+---------------+
| REAL version  |<>----------[ indicator      ]
|               |<>----------[ itype          ]
|               |<>----------[ count          ]
|               |<>--------<>[ tags           ]
|               |<>----------[ tlp            ]
|               |<>----------[ uuid           ]
|               |<>----------[ provider       ]
|               |<>----------[ group          ]
|               |<>----------[ description    ]
|               |<>----------[ message        ]
|               |<>----------[ confidence     ]
|               |<>----------[ firsttime      ]
|               |<>----------[ lasttime       ]
|               |<>----------[ reporttime     ]
|               |<>----------[ cc             ]
|               |<>----------[ asn            ]
|               |<>----------[ asn_dsec       ]
|               |<>----------[ longitude      ]
|               |<>----------[ lattitude      ]
|               |<>----------[ timezone       ]
|               |<>----------[ city           ]
|               |<>----------[ region         ]
|               |<>----------[ reference      ]
|               |<>----------[ reference_tlp  ]
|               |<>----------[ portlist       ]
|               |<>----------[ protocol       ]
|               |<>----------[ dest_portlist  ]
|               |<>----------[ mask           ]
|               |<>----------[ rdata          ]
|               |<>----------[ peers          ]
|               |<>--------<>[ additional_data]
+---------------+
```

#####*The aggregate class that constitute Indicator is:*

### indicator
Exactly One. STRING. A free-form string.

### itype
Exactly One. STRING. A free-form string. Usually one of [ipv4|ipv6|url|fqdn|asn|email|sha1|sha256|sha512|md5].

### group
Exactly One. STRING. A free-form string. Denotes a "group" to share the data with (eg: staff.example.com).

### provider
Exactly One. STRING. A free-form string. Denotes the provider FQDN of the data (eg: csirtg.io).

### TLP
Exactly One. STRING. A free-form string representing the TLP used for sharing purposes.

#####*The Indicator class has the following attributes:*

### version
Required. [REAL](#real-numbers). The specification version number to which this class conforms. While the protocol itself conforms to a [semantic versioning](http://semver.org/), implemented, the protocol version should conform to a REAL (float/double) number using "tenths", to the right of the decimal as a placeholder. Examples:

Semver | REAL
-------|-------
```0.0.1```  | ```0.0010```
```1.0.01``` | ```1.0001```
```2.1.2```  | ```2.1020```
```0.01.01```| ```0.0101```

# 6. Examples
## XML

```
<?xml version="1.0" encoding="UTF-8"?>
<Indicator version="0.0001">
    <Indicator>example.com</Indicator>
    <itype>fqdn</itype>
    <tlp>green</tlp>
    <uuid>24423bab-c81f-4819-b9be-c3d9d975a835</uuid>
    ...
</Indicator>
</xml>
```
## JSON

```
"Indicator": {
    "count": 1,
    "indicator": "http://example.com/1.htm",
    "itype": "url",
    "tags": [
        "phishing"
    ],
    "tlp": "green",
    "uuid": "24423bab-c81f-4819-b9be-c3d9d975a835"
    ...
}
```

# 7. References
## Known Implementations

* csirtg-indicator-py - [github.com/csirtgadgets](https://github.com/csirtgadgets/indicator-py)

# 8. References
* CSIRT Gadgets Protocols - [csirtgadgets.org](http://csirtgadgets.org/rfc)
* Licenses for Protocols - [hintjens.com](http://hintjens.com/blog:41)
* Consensus Oriented Specification System - [digistan.org](http://www.digistan.org/)
* ZeroMQ RFC - [rfc.zeromq.org](http://rfc.zeromq.org/
* Freeformatter (xml to xsd, json validation, etc) - [freeformatter.com](http://www.freeformatter.com/)
* JSON Schema Generator [jsonschema.net](http://www.jsonschema.net/)
