---
title: "CA3077: procesamiento inseguro en el dise&#241;o de una API, documento XML y lector de texto XML | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 7f33771b-f3c8-4c02-bef6-f581b623c303
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA3077: procesamiento inseguro en el dise&#241;o de una API, documento XML y lector de texto XML
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|InsecureDTDProcessingInAPIDesign|  
|Identificador de comprobación|CA3077|  
|Categoría|Microsoft.Security|  
|Cambio problemático|No trascendental|  
  
## Motivo  
 Al diseñar una API derivada de XMLDocument y XMLTextReader, tenga en cuenta la propiedad <xref:System.Xml.XmlReaderSettings.DtdProcessing%2A>.  El uso de instancias de DTDProcessing inseguras al hacer referencia a orígenes de entidades externas o resolverlos, o la definición de valores inseguros en el lenguaje XML puede provocar la divulgación de información.  
  
## Descripción de la regla  
 Una [definición de tipo de documento \(DTD\)](https://msdn.microsoft.com/en-us/library/aa468547.aspx) es una de las dos formas que tiene un analizador XML para determinar la validez de un documento, como se define en el [lenguaje de marcado extensible \(XML\) 1.0 de World Wide Web Consortium \(W3C\)](http://www.w3.org/TR/2008/REC-xml-20081126/). Esta regla busca propiedades e instancias en las que se aceptan datos que no son de confianza para advertir a los desarrolladores de las posibles amenazas de [Divulgación de información](../Topic/Information%20Disclosure.md), lo que puede provocar ataques por [denegación de servicio \(DoS\)](../Topic/Denial%20of%20Service.md). Esta regla se desencadena cuando:  
  
-   Las clases <xref:System.Xml.XmlDocument> o <xref:System.Xml.XmlTextReader> usan valores de resolución predeterminados para el procesamiento de DTD.  
  
-   No se ha definido ningún constructor para las clases derivadas XmlDocument o XmlTextReader o no se usa ningún valor seguro para <xref:System.Xml.XmlResolver>.  
  
## Cómo corregir infracciones  
  
-   Detecte y procese todas las excepciones XmlTextReader correctamente para evitar la divulgación de información de ruta de acceso.  
  
-   Use  <xref:System.Xml.XmlSecureResolver> en lugar de XmlResolver para restringir los recursos a los que puede obtener acceso XmlTextReader.  
  
## Cuándo suprimir advertencias  
 A menos que esté seguro de que la entrada es de un origen de confianza, no suprima ninguna regla de esta advertencia.  
  
## Ejemplos de pseudocódigo  
  
### Infracción  
  
```c#  
using System;   
using System.Xml;   
  
namespace TestNamespace   
{   
    class TestClass : XmlDocument    
    {   
        public TestClass () {} // warn   
    }   
  
    class TestClass2 : XmlTextReader    
    {       
        public TestClass2() // warn   
        {   
        }   
    }   
}  
```  
  
### Soluciones  
  
```c#  
using System;   
using System.Xml;   
  
namespace TestNamespace   
{   
    class TestClass : XmlDocument    
    {   
        public TestClass ()    
        {   
            XmlResolver = null;   
        }   
    }   
  
    class TestClass2 : XmlTextReader    
    {       
        public TestClass2()    
        {   
               XmlResolver = null;   
        }   
    }   
}  
```