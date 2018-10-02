---
title: 'CA3075: Procesamiento de DTD no seguro | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 65798d66-7a30-4359-b064-61a8660c1eed
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 7c8a7fefe3b39c68040101e73ec678d92a81a875
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/24/2018
ms.locfileid: "47591260"
---
# <a name="ca3075-insecure-dtd-processing"></a>CA3075: procesamiento no seguro de DTD
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [CA3075: procesamiento de DTD no seguro](https://docs.microsoft.com/visualstudio/code-quality/ca3075-insecure-dtd-processing).

|||
|-|-|
|TypeName|InsecureDTDProcessing|
|Identificador de comprobación|CA3075|
|Categoría|Microsoft.Security|
|Cambio problemático|No trascendental|

## <a name="cause"></a>Motivo
 Si usa instancias de <xref:System.Xml.XmlReaderSettings.DtdProcessing%2A> no seguras o hace referencia a orígenes de entidades externas, el analizador podría aceptar entradas que no sean de confianza y revelar información confidencial a atacantes.

## <a name="rule-description"></a>Descripción de la regla
 Un [definición de tipo de documento (DTD)](https://msdn.microsoft.com/library/aa468547.aspx) es uno de dos maneras de un analizador XML para determinar la validez de un documento, tal como se define por la [World Wide Web Consortium (W3C) Extensible Markup Language (XML) 1.0](http://www.w3.org/TR/2008/REC-xml-20081126/). Esta regla busca propiedades e instancias que se aceptan los datos de confianza para advertir a los desarrolladores de las posibles [la divulgación de información](http://msdn.microsoft.com/library/4064c89f-afa6-444a-aa7e-807ef072131c) amenazas, lo que pueden provocar [denegación de servicio (DoS)](http://msdn.microsoft.com/library/dfb150f3-d598-4697-a5e6-6779e4f9b600) ataques. Esta regla se desencadena cuando:

-   DtdProcessing está habilitado en la instancia <xref:System.Xml.XmlReader> , que resuelve entidades XML externas mediante <xref:System.Xml.XmlUrlResolver>.

-   Se ha establecido la propiedad <xref:System.Xml.XmlNode.InnerXml%2A> del XML.

-   <xref:System.Xml.XmlReaderSettings.DtdProcessing%2A> propiedad está establecida en el análisis.

-   Las entradas que no son de confianza se procesan mediante <xref:System.Xml.XmlResolver> en lugar de con <xref:System.Xml.XmlSecureResolver> .

-   XmlReader.<xref:System.Xml.XmlReader.Create%2A> se invoca el método con una <xref:System.Xml.XmlReaderSettings> instancia o ninguna en absoluto.

-   <xref:System.Xml.XmlReader> se crea con los valores predeterminados no seguros o valores.

 En cada uno de estos casos, el resultado es el mismo: el contenido del sistema de archivos o de los recursos compartidos de red del equipo en el que se procesa el XML se expondrá al atacante, y posteriormente se podría usar como vector de denegación de servicio.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones

-   Detecte y procese todas las excepciones XmlTextReader correctamente para evitar la divulgación de información de ruta de acceso.

-   Use el <xref:System.Xml.XmlSecureResolver> para restringir los recursos que puede obtener acceso XmlTextReader.

-   No permitir la <xref:System.Xml.XmlReader> abra ningún recurso externo estableciendo la <xref:System.Xml.XmlResolver> propiedad **null**.

-   Asegúrese de que la propiedad <xref:System.Data.DataViewManager.DataViewSettingCollectionString%2A> de <xref:System.Data.DataViewManager> se asigne desde un origen de confianza.

 .NET 3.5 y versiones anteriores

-   Deshabilite el procesamiento de DTD si trabaja con orígenes de confianza estableciendo el <xref:System.Xml.XmlReaderSettings.ProhibitDtd%2A> propiedad **true** .

-   La clase XmlTextReader tiene una petición de herencia de plena confianza. Consulte [peticiones de herencias](http://msdn.microsoft.com/en-us/28b9adbb-8f08-4f10-b856-dbf59eb932d9) para obtener más información.

 .NET 4 y versiones posteriores

-   Evite habilitar DtdProcessing si trabaja con orígenes de confianza estableciendo la propiedad DtdProcessing en [prohibir u omitir](https://msdn.microsoft.com/library/system.xml.dtdprocessing.aspx)

-   Asegúrese de que el método Load() tome una instancia XmlReader en todos los casos InnerXml.

> [!NOTE]
>  Esta regla podría notificar falsos positivos en algunas instancias XmlSecureResolver válidas. Estamos trabajando para tener este problema resuelto a mediados del año 2016.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
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
    XmlTextReader reader = new XmlTextReader(sreader) { DtdProcessing = DtdProcessing.Prohibit };
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
            XmlTextReader reader = new XmlTextReader(stream) { DtdProcessing = DtdProcessing.Prohibit } ;
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
            XmlTextReader reader = new XmlTextReader(path) { DtdProcessing = DtdProcessing.Prohibit };
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
    public class TestClass
    {
        public void TestMethod(string path)
        {
            XmlReaderSettings settings = new XmlReaderSettings(){ DtdProcessing = DtdProcessing.Parse };
            XmlReader reader = XmlReader.Create(path, settings); // warn
        }
    }
}
```

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
            XmlReaderSettings settings = new XmlReaderSettings(){ DtdProcessing = DtdProcessing.Prohibit };
            XmlReader reader = XmlReader.Create(path, settings);
        }
    }
}
```



