# 🧩 Chuleta de XML (eXtensible Markup Language)
Una guía rápida de referencia con la sintaxis esencial de XML, selectores, propiedades y buenas prácticas para el desarrollo de documentos estructurados.

---
<br>

## 🔍 Conceptos Básicos
| CONCEPTO | DESCRIPCIÓN |
| ----- | ----- |
| XML | Lenguaje de marcado extensible que permite definir la gramática de lenguajes específicos para estructurar grandes documentos |
| Elemento | Componente principal de un documento XML. Contiene una etiqueta de apertura, contenido y etiqueta de cierre |
| Atributo | Proporciona información adicional sobre un elemento. Se coloca en la etiqueta de apertura |
| Documento XML bien formado | Documento que cumple las reglas sintácticas básicas de XML |
| Documento XML válido | Documento XML bien formado que además cumple con las reglas definidas en un DTD o esquema XML |

<br>


## 🏗️ Estructura Básica
```xml
<xml version="1.0" encoding="UTF-8">
<root>
  <elemento atributo="valor">
    <subelemento>Contenido</subelemento>
  </elemento>
</root>
```
## 📏 Reglas Sintácticas
| REGLA | DESCRIPCIÓN | EJEMPLO |
| ----- | ----------- | ------- |
| Declaración XML | Especifica la versión XML y codificación | `<xml version="1.0" encoding="UTF-8">` |
| Elemento raíz único | Todo documento debe tener un único elemento raíz | `<raiz>...</raiz>` |
| Etiquetas anidadas | Los elementos deben cerrarse en orden inverso a su apertura | `<a><b>...</b></a>` |
| Sensible a mayúsculas | XML distingue entre mayúsculas y minúsculas | `<Elemento>` es diferente de `<elemento>` |
| Valores de atributos | Los valores siempre deben ir entre comillas | `atributo="valor"` |

<br>

## 🔣 Caracteres Especiales
| CARÁCTER | ENTIDAD | DESCRIPCIÓN |
| --- | --- | --- |
| `<` | `<` | Menor que |
| `>` `| `>` | Mayor que |
| `&` | `&` | Ampersand |
| `"` | `"` | Comillas dobles |
| `'` | `'` | Comilla simple |

<br>

---

## 📑 Tipos de Documentos XML
### 📋 DTD (Document Type Definition)
```xml
<!DOCTYPE root [
  <!ELEMENT root (elemento+)>
  <!ELEMENT elemento (#PCDATA)>
  <!ATTLIST elemento id ID #REQUIRED>
]>
```

| COMPONENTE DTD | DESCRIPCIÓN |
| --- | --- |
| `<!ELEMENT>` | Define un elemento y su contenido permitido |
| `<!ATTLIST>` | Define los atributos de un elemento |
| `<!ENTITY>` | Define entidades para reutilizar texto |

<br>

### 📊 XML Schema (XSD)
```xml
<xs:schema xmlns:xs="http://www.w3.org/2001/XMLSchema">
  <xs:element name="root">
    <xs:complexType>
      <xs:sequence>
        <xs:element name="elemento" type="xs:string"/>
      </xs:sequence>
    </xs:complexType>
  </xs:element>
</xs:schema>
```

| VENTAJAS DE XSD SOBRE DTD | DESCRIPCIÓN |
| ------ | ------ |
| Tipos de datos | Permite definir tipos de datos específicos (enteros, decimales, fechas, etc.) |
| Namespaces | Soporte para espacios de nombres |
| Herencia | Permite extender tipos existentes |
| Expresividad | Mayor capacidad para definir restricciones complejas |

<br>

---

## 🔖 Espacios de Nombres (Namespaces)
```xml
<documento xmlns="http://ejemplo.org/documento"
           xmlns:lib="http://ejemplo.org/biblioteca">
  <titulo>Mi Libro</titulo>
  <lib:autor>Juan Pérez</lib:autor>
</documento>
```
Los espacios de nombres evitan conflictos entre elementos con nombres idénticos pero significados diferentes.

<br>

---

## 🔄 Transformaciones XML
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
| EXPRESIÓN | DESCRIPCIÓN |
| ----- | ----- |
| /root | Selecciona el elemento raíz |
| //elemento | Selecciona todos los elementos "elemento" sin importar su ubicación |
| /root/elemento[1] | Selecciona el primer "elemento" hijo de "root" | 
| /root/elemento[@id='1'] | Selecciona "elemento" con atributo id='1' |
| /root/*/nombre | Selecciona todos los elementos "nombre" que son nietos de "root" |

<br>

---

## ⚙️ Procesamiento de XML
### 🌳 DOM (Document Object Model)
Carga el documento completo en memoria y crea una estructura de árbol para navegarlo.
```JavaScript
// Ejemplo en JavaScript
const xmlDoc = parser.parseFromString(xmlString, "text/xml");
const elementos = xmlDoc.getElementsByTagName("elemento");
```

### 🔄 SAX (Simple API for XML)
Procesamiento secuencial basado en eventos, útil para documentos grandes.
```Java
// Ejemplo en Java
SAXParserFactory factory = SAXParserFactory.newInstance();
SAXParser saxParser = factory.newSAXParser();
saxParser.parse(new File("datos.xml"), new ManejadorEventos());

```

<br>

---

## 🚀 Aplicaciones Comunes de XML
| APLICACIÓN | DESCRIPCIÓN |
| --- | --- |
| RSS/Atom | Formatos basados en XML para sindicación de contenidos |
| SOAP | Protocolo de intercambio de información en servicios web |
| SVG | Formato de gráficos vectoriales basado en XML |
| XHTML | Versión de HTML reformulada como XML |
| MathML | Lenguaje para representar fórmulas matemáticas |
| KML | Lenguaje para representar datos geográficos (usado en Google Earth) |

<br>

## ✅ Buenas Prácticas
- Nombres descriptivos: usar nombres de elementos y atributos que describan claramente su propósito.
- Consistencia: mantener una estructura y convenciones consistentes en todo el documento.
- Comentarios: documentar secciones complejas con comentarios.
- Validación: validar documentos contra un esquema o DTD.
- Espacios de nombres: utilizar espacios de nombres para evitar conflictos.

<br>

## 📚 Glosario
- **API**: interfaz de Programación de Aplicaciones. Conjunto de reglas y protocolos que permiten la comunicación entre componentes de software.
- **CDATA**: Character Data. Sección en un documento XML donde los caracteres especiales no son interpretados como marcado.
- **DTD**: Document Type Definition. Define la estructura y los elementos válidos para un documento XML.
- **DOM**: Document Object Model. Interfaz de programación que representa documentos HTML o XML como árboles de nodos.
- **Entidad**: referencias que representan caracteres especiales o bloques de texto predefinidos en XML.
- **Namespace**: espacio de nombres. Mecanismo para evitar conflictos entre nombres de elementos en XML.
- **Nodo** cualquier objeto dentro de la estructura de un documento XML (elementos, atributos, texto, etc.).
- **SAX**: Simple API for XML. Interfaz para procesar documentos XML de manera secuencial.
- **Schema (XSD)**: XML Schema Definition. Describe la estructura de un documento XML de manera más potente que un DTD.
- **XSLT**: eXtensible Stylesheet Language Transformations. Lenguaje para transformar documentos XML en otros formatos.
- **XPath**: lenguaje de expresiones para seleccionar partes específicas de un documento XML.
- **XQuery**: lenguaje de consulta diseñado para extraer información de documentos XML.