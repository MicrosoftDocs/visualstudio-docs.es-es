---
title: 'CA3075: Procesamiento no seguro de DTD'
ms.date: 03/18/2019
ms.topic: reference
ms.assetid: 65798d66-7a30-4359-b064-61a8660c1eed
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6de817e3aaecbdd1c89cc2174e91126ea39d99d7
ms.sourcegitcommit: 4d9c54f689416bf1dc4ace058919592482d02e36
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/19/2019
ms.locfileid: "58194624"
---
# <a name="ca3075-insecure-dtd-processing"></a>CA3075: Procesamiento no seguro de DTD

|||
|-|-|
|TypeName|InsecureDTDProcessing|
|Identificador de comprobación|CA3075|
|Categoría|Microsoft.Security|
|Cambio problemático|No trascendental|

## <a name="cause"></a>Motivo

Si usa instancias de <xref:System.Xml.XmlReaderSettings.DtdProcessing%2A> no seguras o hace referencia a orígenes de entidades externas, el analizador podría aceptar entradas que no sean de confianza y revelar información confidencial a atacantes.

## <a name="rule-description"></a>Descripción de la regla

Una *definición de tipo de documento (DTD)* es una de las dos formas que tiene un analizador XML para determinar la validez de un documento, como se define en el  [lenguaje de marcado extensible (XML) 1.0 de World Wide Web Consortium (W3C)](http://www.w3.org/TR/2008/REC-xml-20081126/). Esta regla busca propiedades e instancias que se aceptan los datos de confianza para advertir a los desarrolladores de las posibles [la divulgación de información](/dotnet/framework/wcf/feature-details/information-disclosure) amenazas o [denegación de servicio (DoS)](/dotnet/framework/wcf/feature-details/denial-of-service) ataques. Esta regla se desencadena cuando:

- DtdProcessing está habilitado en la instancia <xref:System.Xml.XmlReader> , que resuelve entidades XML externas mediante <xref:System.Xml.XmlUrlResolver>.

- Se ha establecido la propiedad <xref:System.Xml.XmlNode.InnerXml%2A> del XML.

- <xref:System.Xml.XmlReaderSettings.DtdProcessing%2A> propiedad está establecida en el análisis.

- No es de confianza se procesa la entrada mediante <xref:System.Xml.XmlResolver> en lugar de <xref:System.Xml.XmlSecureResolver>.

- El <xref:System.Xml.XmlReader.Create%2A?displayProperty=nameWithType> método se invoca con una <xref:System.Xml.XmlReaderSettings> instancia o ninguna en absoluto.

- <xref:System.Xml.XmlReader> se crea con los valores predeterminados no seguros o valores.

En cada uno de estos casos, el resultado es el mismo: el contenido ya sea el sistema o la red recursos compartidos de archivos desde el equipo donde se procesa el XML se expondrá al atacante, o el procesamiento de DTD puede usarse como un vector de denegación de servicio.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones

- Detecte y procese todas las excepciones XmlTextReader correctamente para evitar la divulgación de información de ruta de acceso.

- Use el <xref:System.Xml.XmlSecureResolver> para restringir los recursos que puede obtener acceso XmlTextReader.

- Establezca la propiedad <xref:System.Xml.XmlReader> en <xref:System.Xml.XmlResolver> null **para evitar que**abra ningún recurso externo.

- Asegúrese de que el <xref:System.Data.DataViewManager.DataViewSettingCollectionString%2A?displayProperty=nameWithType> se asigna la propiedad de un origen de confianza.

**.NET 3.5 y versiones anteriores**

- Deshabilite el procesamiento de DTD si trabaja con orígenes de confianza estableciendo el <xref:System.Xml.XmlReaderSettings.ProhibitDtd%2A> propiedad **true**.

- La clase XmlTextReader tiene una petición de herencia de plena confianza.

**.NET 4 y versiones posteriores**

- Evite habilitar DtdProcessing si trabaja con orígenes de confianza estableciendo el <xref:System.Xml.XmlReaderSettings.DtdProcessing%2A?displayProperty=nameWithType> propiedad **prohibir** o **omitir**.

- Asegúrese de que el método Load() tome una instancia XmlReader en todos los casos InnerXml.

> [!NOTE]
> Esta regla podría notificar falsos positivos en algunas instancias XmlSecureResolver válidas.

## <a name="when-to-suppress-warnings"></a>Cuándo Suprimir advertencias

A menos que esté seguro de que la entrada es de un origen de confianza, no suprima ninguna regla de esta advertencia.

## <a name="pseudo-code-examples"></a>Ejemplos de pseudocódigo

### <a name="violation"></a>Infracción

```csharp
using System.IO;
using System.Xml.Schema;

class TestClass
{
    public XmlSchema Test
    {
        get
        {
            var src = "";
            TextReader tr = new StreamReader(src);
            XmlSchema schema = XmlSchema.Read(tr, null); // warn
            return schema;
        }
    }
}
```

### <a name="solution"></a>Soluciones

```csharp
using System.IO;
using System.Xml;
using System.Xml.Schema;

class TestClass
{
    public XmlSchema Test
    {
        get
        {
            var src = "";
            TextReader tr = new StreamReader(src);
            XmlTextReader reader = new XmlTextReader(tr) { DtdProcessing = DtdProcessing.Prohibit };
            XmlSchema schema = XmlSchema.Read(reader , null);
            return schema;
        }
    }
}
```

### <a name="violation"></a>Infracción

```csharp
using System.Xml;

namespace TestNamespace
{
    public class TestClass
    {
        public XmlReaderSettings settings = new XmlReaderSettings();
        public void TestMethod(string path)
        {
            var reader = XmlReader.Create(path, settings);  // warn
        }
    }
}
```

### <a name="solution"></a>Soluciones

```csharp
using System.Xml;

namespace TestNamespace
{
    public class TestClass
    {
        public XmlReaderSettings settings = new XmlReaderSettings()
        {
            DtdProcessing = DtdProcessing.Prohibit
        };

        public void TestMethod(string path)
        {
            var reader = XmlReader.Create(path, settings);
        }
    }
}
```

### <a name="violations"></a>Infracciones

```csharp
using System.Xml;

namespace TestNamespace
{
    public class DoNotUseSetInnerXml
    {
        public void TestMethod(string xml)
        {
            XmlDocument doc = new XmlDocument() { XmlResolver = null };
            doc.InnerXml = xml; // warn
        }
    }
}
```

```csharp
using System.Xml;

namespace TestNamespace
{
    public class DoNotUseLoadXml
    {
        public void TestMethod(string xml)
        {
            XmlDocument doc = new XmlDocument(){ XmlResolver = null };
            doc.LoadXml(xml); // warn
        }
    }
}
```

### <a name="solution"></a>Soluciones

```csharp
using System.Xml;

public static void TestMethod(string xml)
{
    XmlDocument doc = new XmlDocument() { XmlResolver = null };
    System.IO.StringReader sreader = new System.IO.StringReader(xml);
    XmlReader reader = XmlReader.Create(sreader, new XmlReaderSettings() { XmlResolver = null });
    doc.Load(reader);
}
```

### <a name="violation"></a>Infracción

```csharp
using System.IO;
using System.Xml;
using System.Xml.Serialization;

namespace TestNamespace
{
    public class UseXmlReaderForDeserialize
    {
        public void TestMethod(Stream stream)
        {
            XmlSerializer serializer = new XmlSerializer(typeof(UseXmlReaderForDeserialize));
            serializer.Deserialize(stream); // warn
        }
    }
}
```

### <a name="solution"></a>Soluciones

```csharp
using System.IO;
using System.Xml;
using System.Xml.Serialization;

namespace TestNamespace
{
    public class UseXmlReaderForDeserialize
    {
        public void TestMethod(Stream stream)
        {
            XmlSerializer serializer = new XmlSerializer(typeof(UseXmlReaderForDeserialize));
            XmlReader reader = XmlReader.Create(stream, new XmlReaderSettings() { XmlResolver = null });
            serializer.Deserialize(reader );
        }
    }
}
```

### <a name="violation"></a>Infracción

```csharp
using System.Xml;
using System.Xml.XPath;

namespace TestNamespace
{
    public class UseXmlReaderForXPathDocument
    {
        public void TestMethod(string path)
        {
            XPathDocument doc = new XPathDocument(path); // warn
        }
    }
}
```

### <a name="solution"></a>Soluciones

```csharp
using System.Xml;
using System.Xml.XPath;

namespace TestNamespace
{
    public class UseXmlReaderForXPathDocument
    {
        public void TestMethod(string path)
        {
            XmlReader reader = XmlReader.Create(path, new XmlReaderSettings() { XmlResolver = null });
            XPathDocument doc = new XPathDocument(reader);
        }
    }
}
```

### <a name="violation"></a>Infracción

```csharp
using System.Xml;

namespace TestNamespace
{
    class TestClass
    {
        public XmlDocument doc = new XmlDocument() { XmlResolver = new XmlUrlResolver() };
    }
}
```

### <a name="solution"></a>Soluciones

```csharp
using System.Xml;

namespace TestNamespace
{
    class TestClass
    {
        public XmlDocument doc = new XmlDocument() { XmlResolver = null }; // or set to a XmlSecureResolver instance
    }
}
```

### <a name="violations"></a>Infracciones

```csharp
using System.Xml;

namespace TestNamespace
{
    class TestClass
    {
        private static void TestMethod()
        {
            var reader = XmlTextReader.Create(""doc.xml""); //warn
        }
    }
}
```

```csharp
using System.Xml;

namespace TestNamespace
{
    public class TestClass
    {
        public void TestMethod(string path)
        {
            try {
                XmlTextReader reader = new XmlTextReader(path); // warn
            }
            catch { throw ; }
            finally {}
        }
    }
}
```

### <a name="solution"></a>Soluciones

```csharp
using System.Xml;

namespace TestNamespace
{
    public class TestClass
    {
        public void TestMethod(string path)
        {
            XmlReaderSettings settings = new XmlReaderSettings() { XmlResolver = null };
            XmlReader reader = XmlReader.Create(path, settings);
        }
    }
}
```
