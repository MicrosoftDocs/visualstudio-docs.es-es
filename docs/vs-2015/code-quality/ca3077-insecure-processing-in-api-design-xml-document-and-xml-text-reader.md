---
title: 'CA3077: Procesamiento inseguro en el diseño de API, documento XML y lector de texto XML | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7f33771b-f3c8-4c02-bef6-f581b623c303
caps.latest.revision: 9
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 0e75f86b958d0f2602a3f32830e8c6f18c185584
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49925095"
---
# <a name="ca3077-insecure-processing-in-api-design-xml-document-and-xml-text-reader"></a>CA3077: procesamiento inseguro en el diseño de una API, documento XML y lector de texto XML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|InsecureDTDProcessingInAPIDesign|
|Identificador de comprobación|CA3077|
|Categoría|Microsoft.Security|
|Cambio problemático|No trascendental|

## <a name="cause"></a>Motivo
 Al diseñar una API derivada de XMLDocument y XMLTextReader, tenga en cuenta la propiedad <xref:System.Xml.XmlReaderSettings.DtdProcessing%2A>.  El uso de instancias de DTDProcessing inseguras al hacer referencia a orígenes de entidades externas o resolverlos, o la definición de valores inseguros en el lenguaje XML puede provocar la divulgación de información.

## <a name="rule-description"></a>Descripción de la regla
 Una [definición de tipo de documento (DTD)](https://msdn.microsoft.com/library/aa468547.aspx) es una de las dos formas que tiene un analizador XML para determinar la validez de un documento, como se define en el  [lenguaje de marcado extensible (XML) 1.0 de World Wide Web Consortium (W3C)](http://www.w3.org/TR/2008/REC-xml-20081126/). Esta regla busca propiedades e instancias en las que se aceptan datos que no son de confianza para advertir a los desarrolladores de las posibles amenazas de [Information Disclosure](http://msdn.microsoft.com/library/4064c89f-afa6-444a-aa7e-807ef072131c) , lo que puede provocar ataques por [denegación de servicio (DoS)](http://msdn.microsoft.com/library/dfb150f3-d598-4697-a5e6-6779e4f9b600) . Esta regla se desencadena cuando:

-   <xref:System.Xml.XmlDocument> o <xref:System.Xml.XmlTextReader> clases usan valores de resolución predeterminados para el procesamiento de DTD.

-   No se ha definido ningún constructor para las clases derivadas XmlDocument o XmlTextReader o no se usa ningún valor seguro para <xref:System.Xml.XmlResolver>.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones

-   Detecte y procese todas las excepciones XmlTextReader correctamente para evitar la divulgación de información de ruta de acceso.

-   Use <xref:System.Xml.XmlSecureResolver>en lugar de XmlResolver para restringir los recursos que se puede obtener acceso XmlTextReader.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
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



