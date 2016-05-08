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
| REAL version  |<>----------[ Indicator      ]
| INT32 id      |<>----------[ TLP            ]
|               |
+---------------+
```

#####*The aggregate class that constitute Indicator is:*

### Indicator
Zero or many. STRING. A free-form string representing the indicator itself.

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

### id
Required. INT32. A unique identifier representing the person.

# 6. Examples
## XML

```
<?xml version="1.0" encoding="UTF-8"?>
<Indicator version="0.0001" id="1">
    <Indicator>example.com</Indicator>
    <TLP>RED</TLP>
</Indicator>
</xml>
```
## JSON

```
"Indicator": [{
    "version": "0.0001",
    "id": 1,
    "Indicator": "example.com",
    "TLP": "RED"
}]
```

# 7. Data Types
## Real Numbers

Real (floating-point) attributes are represented by the REAL data type. Real data MUST be encoded in Base 10.

## Enumerated Types

Enumerated types are represented by the ENUM data type, and consist of an ordered list of acceptable values.  Each value has a representative keyword.  Within the schema, the enumerated type keywords are used as attribute values.

# 8. References
## Known Implementations

* csirtg-indicator-py - [github.com/csirtgadgets](https://github.com/csirtgadgets/csirtg-indicator-py)


## Misc
* CSIRT Gadgets Protocols - [csirtgadgets.org](http://csirtgadgets.org/rfc)
* Licenses for Protocols - [hintjens.com](http://hintjens.com/blog:41)
* Consensus Oriented Specification System - [digistan.org](http://www.digistan.org/)
* ZeroMQ RFC - [rfc.zeromq.org](http://rfc.zeromq.org/
* Freeformatter (xml to xsd, json validation, etc) - [freeformatter.com](http://www.freeformatter.com/)
* JSON Schema Generator [jsonschema.net](http://www.jsonschema.net/)