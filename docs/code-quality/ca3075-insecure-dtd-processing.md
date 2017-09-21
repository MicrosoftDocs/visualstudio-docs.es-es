---
title: "CA3075: procesamiento no seguro de DTD | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 65798d66-7a30-4359-b064-61a8660c1eed
caps.latest.revision: 17
caps.handback.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA3075: procesamiento no seguro de DTD
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|InsecureDTDProcessing|  
|Identificador de comprobación|CA3075|  
|Categoría|Microsoft.Security|  
|Cambio problemático|No trascendental|  
  
## Motivo  
 Si usa instancias de <xref:System.Xml.XmlReaderSettings.DtdProcessing%2A> no seguras o hace referencia a orígenes de entidades externas, el analizador podría aceptar entradas que no sean de confianza y revelar información confidencial a atacantes.  
  
## Descripción de la regla  
 Una [definición de tipo de documento \(DTD\)](https://msdn.microsoft.com/en-us/library/aa468547.aspx) es una de las dos formas que tiene un analizador XML para determinar la validez de un documento, como se define en el [lenguaje de marcado extensible \(XML\) 1.0 de World Wide Web Consortium \(W3C\)](http://www.w3.org/TR/2008/REC-xml-20081126/). Esta regla busca propiedades e instancias en las que se aceptan datos que no son de confianza para advertir a los desarrolladores de las posibles amenazas de [Divulgación de información](../Topic/Information%20Disclosure.md), lo que puede provocar ataques por [denegación de servicio \(DoS\)](../Topic/Denial%20of%20Service.md). Esta regla se desencadena cuando:  
  
-   DtdProcessing está habilitado en la instancia <xref:System.Xml.XmlReader>, que resuelve entidades XML externas mediante <xref:System.Xml.XmlUrlResolver>.  
  
-   Se ha establecido la propiedad <xref:System.Xml.XmlNode.InnerXml%2A> del XML.  
  
-   La propiedad <xref:System.Xml.XmlReaderSettings.DtdProcessing%2A> se ha establecido en Analizar.  
  
-   Las entradas que no son de confianza se procesan mediante <xref:System.Xml.XmlResolver> en lugar de con <xref:System.Xml.XmlSecureResolver>.  
  
-   El método XmlReader.<xref:System.Xml.XmlReader.Create%2A> se invoca con una instancia <xref:System.Xml.XmlReaderSettings> no segura o sin ninguna instancia.  
  
-   <xref:System.Xml.XmlReader> se crea con una configuración o unos valores predeterminados no seguros.  
  
 En cada uno de estos casos, el resultado es el mismo: el contenido del sistema de archivos o de los recursos compartidos de red del equipo en el que se procesa el XML se expondrá al atacante, y posteriormente se podría usar como vector de denegación de servicio.  
  
## Cómo corregir infracciones  
  
-   Detecte y procese todas las excepciones XmlTextReader correctamente para evitar la divulgación de información de ruta de acceso.  
  
-   Use  <xref:System.Xml.XmlSecureResolver> para restringir los recursos a los que puede obtener acceso XmlTextReader.  
  
-   Establezca la propiedad <xref:System.Xml.XmlResolver> en **null** para evitar que <xref:System.Xml.XmlReader> abra ningún recurso externo.  
  
-   Asegúrese de que la propiedad <xref:System.Data.DataViewManager.DataViewSettingCollectionString%2A> de <xref:System.Data.DataViewManager> se asigne desde un origen de confianza.  
  
 .NET 3.5 y versiones anteriores  
  
-   Deshabilite el procesamiento de DTD si trabaja con orígenes que no son de confianza; para ello, establezca la  propiedad <xref:System.Xml.XmlReaderSettings.ProhibitDtd%2A> en  **true**.  
  
-   La clase XmlTextReader tiene una petición de herencia de plena confianza. Consulte  [Inheritance Demands](http://msdn.microsoft.com/es-es/28b9adbb-8f08-4f10-b856-dbf59eb932d9) \(Peticiones de herencia\)  para obtener más información.  
  
 .NET 4 y versiones posteriores  
  
-   Evite habilitar DtdProcessing si trabaja con orígenes que no son de confianza; para ello, establezca la propiedad DtdProcessing en [Prohibir u Omitir](https://msdn.microsoft.com/en-us/library/system.xml.dtdprocessing.aspx).  
  
-   Asegúrese de que el método Load\(\) tome una instancia XmlReader en todos los casos InnerXml.  
  
> [!NOTE]
>  Esta regla podría notificar falsos positivos en algunas instancias XmlSecureResolver válidas. Estamos trabajando para tener este problema resuelto a mediados del año 2016.  
  
## Cuándo suprimir advertencias  
 A menos que esté seguro de que la entrada es de un origen de confianza, no suprima ninguna regla de esta advertencia.  
  
## Ejemplos de pseudocódigo  
  
### Infracción  
  
```c#  
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
  
### Soluciones  
  
```c#  
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
  
### Infracción  
  
```c#  
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
  
### Soluciones  
  
```c#  
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
  
### Infracciones  
  
```c#  
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
  
```c#  
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
  
### Soluciones  
  
```c#  
using System.Xml;   
  
public static void TestMethod(string xml)   
{   
    XmlDocument doc = new XmlDocument() { XmlResolver = null };   
    System.IO.StringReader sreader = new System.IO.StringReader(xml);   
    XmlTextReader reader = new XmlTextReader(sreader) { DtdProcessing = DtdProcessing.Prohibit };   
    doc.Load(reader);   
}  
```  
  
### Infracción  
  
```c#  
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
  
### Soluciones  
  
```c#  
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
  
### Infracción  
  
```c#  
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
  
### Soluciones  
  
```c#  
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
  
### Infracción  
  
```c#  
using System.Xml;   
  
namespace TestNamespace   
{   
    class TestClass   
    {   
        public XmlDocument doc = new XmlDocument() { XmlResolver = new XmlUrlResolver() };   
    }   
}  
```  
  
### Soluciones  
  
```c#  
using System.Xml;   
  
namespace TestNamespace   
{   
    class TestClass   
    {   
        public XmlDocument doc = new XmlDocument() { XmlResolver = null }; // or set to a XmlSecureResolver instance   
    }   
}  
```  
  
### Infracciones  
  
```c#  
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
  
```c#  
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
  
```c#  
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
  
### Soluciones  
  
```c#  
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