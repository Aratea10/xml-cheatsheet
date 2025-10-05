# 🧩 XML Cheat Sheet (eXtensible Markup Language)
A quick reference guide with essential XML syntax, selectors, properties and best practices for developing structured documents.

---
<br>

## 🔍 Basic Concepts
| CONCEPT | DESCRIPTION |
| ----- | ----- |
| XML | Extensible markup language that allows defining the grammar of specific languages to structure large documents |
| Element | Main component of an XML document. Contains an opening tag, content and closing tag |
| Attribute | Provides additional information about an element. It is placed in the opening tag |
| Well-formed XML document | Document that complies with the basic syntactic rules of XML |
| Valid XML document | Well-formed XML document that also complies with rules defined in a DTD or XML schema |

<br>

## 🏗️ Basic Structure
```xml
<xml version="1.0" encoding="UTF-8">
<root>
  <element attribute="valor">
    <subelement>Content</subelemento>
  </element>
</root>
```

<br>

## 📏 Syntax Rules
| RULE | DESCRIPTION | EXAMPLE |
| ----- | ----------- | ------- |
| XML Declaration | Specifies the XML version and encoding | `<xml version="1.0" encoding="UTF-8">` |
| Single root element | | Valores de atributos | Los valores siempre deben ir entre comillas | `atributo="valor"` |
 | `<raiz>...</raiz>` |
| Nested tags | Elements must be closed in the reverse order to their opening | `<a><b>...</b></a>` |
| Case sensitive | XML distinguishes between uppercase and lowercase | `<Element>` is different from `<element>` |
| Attribute values | Values must always be enclosed in quotation marks | `atributo="valor"` |

<br>

## 🔣 Special Characters
| CHARACTER | ENTITY | DESCRIPTION |
| --- | --- | --- |
| `<` | `<` | Less than |
| `>` `| `>` | Greater than |
| `&` | `&` | Ampersand |
| `"` | `"` | Double quotes |
| `'` | `'` | Single quote |

<br>

---

## 📑 XML Document Types
### 📋 DTD (Document Type Definition)
```xml
<!DOCTYPE root [
  <!ELEMENT root (element+)>
  <!ELEMENT element (#PCDATA)>
  <!ATTLIST element id ID #REQUIRED>
]>
```

<br>

| DTD COMPONENT | DESCRIPTION |
| --- | --- |
| `<!ELEMENT>` | Defines an element and its permitted content |
| `<!ATTLIST>` | Defines the attributes of an element |
| `<!ENTITY>` | Defines entities for reusing text |

<br>

### 📊 XML Schema (XSD)
```xml
<xs:schema xmlns:xs="http://www.w3.org/2001/XMLSchema">
  <xs:element name="root">
    <xs:complexType>
      <xs:sequence>
        <xs:element name="element" type="xs:string"/>
      </xs:sequence>
    </xs:complexType>
  </xs:element>
</xs:schema>
```

<br>

| ADVANTAGES OF XSD OVER DTD | DESCRIPTION |
| ------ | ------ |
| Data types | Allows defining specific data types (integers, decimals, dates, etc.) |
| Namespaces | Support for namespaces |
| Inheritance | Allows extending existing types |
| Expressiveness | Greater capacity for defining complex constraints |

<br>

---

## 🔖 Namespaces
```xml
<document xmlns="http://ejemplo.org/documento"
           xmlns:lib="http://ejemplo.org/biblioteca">
  <title>My Book</title>
  <bo:author>Juan Pérez</bo:author>
</document>
```
Namespaces prevent conflicts between elements with identical names but different meanings.

<br>

---

## 🔄 XML Transformations
### 🛠️ XSLT (eXtensible Stylesheet Language Transformations)
```xml
<xsl:stylesheet version="1.0" xmlns:xsl="http://www.w3.org/1999/XSL/Transform">
  <xsl:template match="/">
    <html>
      <body>
        <h1><xsl:value-of select="/root/titulo"/></h1>
      </body>
    </html>
  </xsl:template>
</xsl:stylesheet>
```
<br>

### 🔍 XPath
| EXPRESSION | DESCRIPTION |
| ----- | ----- |
| /root | Selects the root element |
| //elemento | Selects all "elemento" elements regardless of their location |
| /root/elemento[1] | Selects the first "elemento" child of "root" | 
| /root/elemento[@id='1'] | Selects "elemento" with attribute id='1' |
| /root/*/nombre | Selects all "nombre" elements that are grandchildren of "root" |

<br>

---

## ⚙️ XML Processing
### 🌳 DOM (Document Object Model)
Loads the complete document into memory and creates a tree structure to navigate it.
```JavaScript
// Example in JavaScript
const xmlDoc = parser.parseFromString(xmlString, "text/xml");
const elementos = xmlDoc.getElementsByTagName("elemento");
```

<br>

### 🔄 SAX (Simple API for XML)
Sequential processing based on events, useful for large documents.
```Java
// Example in Java
SAXParserFactory factory = SAXParserFactory.newInstance();
SAXParser saxParser = factory.newSAXParser();
saxParser.parse(new File("datos.xml"), new ManejadorEventos());

```

<br>

---

## 🚀 Common XML Applications
| APPLICATION | DESCRIPTION |
| --- | --- |
| RSS/Atom | XML-based formats for content syndication |
| SOAP | Protocol for information exchange in web services |
| SVG | XML-based vector graphics format |
| XHTML | Version of HTML reformulated as XML |
| MathML | Language for representing mathematical formulas |
| KML | Language for representing geographic data (used in Google Earth) |

<br>

## ✅ Best Practices
- Descriptive names: use element and attribute names that clearly describe their purpose.
- Consistency: maintain consistent structure and conventions throughout the document.
- Comments: document complex sections with comments
- Validation: validate documents against a schema or DTD
- Namespaces: use namespaces to avoid conflicts

<br>

## 📚 Glossary
- **API**: Application Programming Interface. Set of rules and protocols that allow communication between software components.
- **CDATA**: Character Data. Section in an XML document where special characters are not interpreted as markup.
- **DTD**: Document Type Definition. Defines the structure and valid elements for an XML document.
- **DOM**: Document Object Model. Programming interface that represents HTML or XML documents as trees of nodes.
- **Entity**: references that represent special characters or predefined text blocks in XML.
- **Namespace**: mechanism to avoid conflicts between element names in XML.
- **Node**: any object within the structure of an XML document (elements, attributes, text, etc.).
- **SAX**: Simple API for XML. Interface for processing XML documents sequentially.
- **Schema (XSD)**: XML Schema Definition. Describes the structure of an XML document more powerfully than a DTD.
- **XSLT**: eXtensible Stylesheet Language Transformations. Language for transforming XML documents into other formats.
- **XPath**: expression language for selecting specific parts of an XML document.
- **XQuery**: query language designed to extract information from XML documents.