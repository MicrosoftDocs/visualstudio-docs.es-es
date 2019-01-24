---
title: 'CA3077: Procesamiento no seguro en el diseño de una API, documento XML y lector de texto XML'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
ms.assetid: 7f33771b-f3c8-4c02-bef6-f581b623c303
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 33c6aaea4cdc7de1c81338eb4861d56d73cb5909
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53841283"
---
# <a name="ca3077-insecure-processing-in-api-design-xml-document-and-xml-text-reader"></a>CA3077: Procesamiento no seguro en el diseño de una API, documento XML y lector de texto XML

|||
|-|-|
|TypeName|InsecureDTDProcessingInAPIDesign|
|Identificador de comprobación|CA3077|
|Categoría|Microsoft.Security|
|Cambio problemático|No trascendental|

## <a name="cause"></a>Motivo
 Al diseñar una API derivada de XMLDocument y XMLTextReader, tenga en cuenta la propiedad <xref:System.Xml.XmlReaderSettings.DtdProcessing%2A>.  El uso de instancias de DTDProcessing inseguras al hacer referencia a orígenes de entidades externas o resolverlos, o la definición de valores inseguros en el lenguaje XML puede provocar la divulgación de información.

## <a name="rule-description"></a>Descripción de la regla
 Una *definición de tipo de documento (DTD)* es una de las dos formas que tiene un analizador XML para determinar la validez de un documento, como se define en el  [lenguaje de marcado extensible (XML) 1.0 de World Wide Web Consortium (W3C)](http://www.w3.org/TR/2008/REC-xml-20081126/). Esta regla busca propiedades e instancias en las que se aceptan datos que no son de confianza para advertir a los desarrolladores de las posibles amenazas de [Information Disclosure](/dotnet/framework/wcf/feature-details/information-disclosure) , lo que puede provocar ataques por [denegación de servicio (DoS)](/dotnet/framework/wcf/feature-details/denial-of-service) . Esta regla se desencadena cuando:

- <xref:System.Xml.XmlDocument> o <xref:System.Xml.XmlTextReader> clases usan valores de resolución predeterminados para el procesamiento de DTD.

- No se ha definido ningún constructor para las clases derivadas XmlDocument o XmlTextReader o no se usa ningún valor seguro para <xref:System.Xml.XmlResolver>.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones

- Detecte y procese todas las excepciones XmlTextReader correctamente para evitar la divulgación de información de ruta de acceso.

- Use <xref:System.Xml.XmlSecureResolver>en lugar de XmlResolver para restringir los recursos que se puede obtener acceso XmlTextReader.

## <a name="when-to-suppress-warnings"></a>Cuándo Suprimir advertencias
 A menos que esté seguro de que la entrada es de un origen de confianza, no suprima ninguna regla de esta advertencia.

## <a name="pseudo-code-examples"></a>Ejemplos de pseudocódigo

### <a name="violation"></a>Infracción

```csharp
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

### <a name="solution"></a>Soluciones

```csharp
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