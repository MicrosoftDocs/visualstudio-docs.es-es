---
title: 'CA3077: procesamiento inseguro en el diseño de la API, documento XML y lector de texto XML | Microsoft Docs'
ms.date: 11/15/2016
ms.technology: vs-ide-code-analysis
ms.topic: reference
ms.assetid: 7f33771b-f3c8-4c02-bef6-f581b623c303
caps.latest.revision: 9
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: c0d6a6f6ab42d69d4503741f6625627c46d4ef77
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/30/2020
ms.locfileid: "85545111"
---
# <a name="ca3077-insecure-processing-in-api-design-xml-document-and-xml-text-reader"></a>CA3077: Procesamiento no seguro en el diseño de una API, documento XML y lector de texto XML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Elemento|Valor|
|-|-|
|TypeName|InsecureDTDProcessingInAPIDesign|
|Identificador de comprobación|CA3077|
|Categoría|Microsoft.Security|
|Cambio problemático|No trascendental|

## <a name="cause"></a>Causa
 Al diseñar una API derivada de XMLDocument y XMLTextReader, tenga en cuenta la propiedad <xref:System.Xml.XmlReaderSettings.DtdProcessing%2A>.  El uso de instancias de DTDProcessing inseguras al hacer referencia a orígenes de entidades externas o resolverlos, o la definición de valores inseguros en el lenguaje XML puede provocar la divulgación de información.

## <a name="rule-description"></a>Descripción de la regla
 Una [definición de tipo de documento (DTD)](https://msdn.microsoft.com/library/aa468547.aspx) es una de las dos formas que tiene un analizador XML para determinar la validez de un documento, como se define en el  [lenguaje de marcado extensible (XML) 1.0 de World Wide Web Consortium (W3C)](https://www.w3.org/TR/2008/REC-xml-20081126/). Esta regla busca propiedades e instancias en las que se aceptan datos que no son de confianza para advertir a los desarrolladores de las posibles amenazas de [Information Disclosure](https://msdn.microsoft.com/library/4064c89f-afa6-444a-aa7e-807ef072131c) , lo que puede provocar ataques por [denegación de servicio (DoS)](https://msdn.microsoft.com/library/dfb150f3-d598-4697-a5e6-6779e4f9b600) . Esta regla se desencadena cuando:

- <xref:System.Xml.XmlDocument><xref:System.Xml.XmlTextReader>las clases o usan valores de resolución predeterminados para el procesamiento de DTD.

- No se ha definido ningún constructor para las clases derivadas XmlDocument o XmlTextReader o no se usa ningún valor seguro para <xref:System.Xml.XmlResolver>.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones

- Detecte y procese todas las excepciones de XmlTextReader correctamente para evitar la divulgación de información de ruta de acceso.

- Use en  <xref:System.Xml.XmlSecureResolver> lugar de XmlResolver para restringir los recursos a los que puede tener acceso XmlTextReader.

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

### <a name="solution"></a>Solución

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
