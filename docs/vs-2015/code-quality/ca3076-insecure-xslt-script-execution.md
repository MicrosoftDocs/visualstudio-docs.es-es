---
title: 'CA3076: Ejecución del Script XSLT no segura | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 53cb7a46-c564-488f-bc51-0e210a7853c9
caps.latest.revision: 7
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 39aebc0e7681b139e021c48c12a87d4b060cc7af
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49911478"
---
# <a name="ca3076-insecure-xslt-script-execution"></a>CA3076: Ejecución del script XSLT no segura
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|InsecureXSLTScriptExecution|
|Identificador de comprobación|CA3076|
|Categoría|Microsoft.Security|
|Cambio problemático|No trascendental|

## <a name="cause"></a>Motivo
 Si ejecuta el [lenguaje de transformación basado en hojas de estilo (XSLT)](https://support.microsoft.com/en-us/kb/313997) en aplicaciones .NET de forma no segura, el procesador podría [resolver referencias URI que no sean de confianza](http://msdn.microsoft.com/en-us/ba3e4d4f-1ee7-4226-a51a-78a1f1b5bd8a) y que podrían revelar información confidencial a atacantes, lo que daría lugar a ataques de denegación de servicio y entre sitios.

## <a name="rule-description"></a>Descripción de la regla
 [XSLT](http://msdn.microsoft.com/en-us/6377ce5f-3c45-42a6-b7a9-ec8da588b60c) es un estándar de World Wide Web Consortium (W3C) para transformar datos XML. XSLT normalmente se usa para escribir hojas de estilos para transformar datos XML en otros formatos, como HTML, texto de longitud fija, texto separado por comas o un formato XML distinto. Aunque está prohibido de forma predeterminada, puede habilitarlo para su proyecto.

 Para asegurarse de que no expone una superficie expuesta a ataques, esta regla se desencadena cada vez que el XslCompiledTransform.<xref:System.Xml.Xsl.XslCompiledTransform.Load%2A> recibe las instancias de combinación no seguras de <xref:System.Xml.Xsl.XsltSettings> y <xref:System.Xml.XmlResolver>, lo que permite el procesamiento de scripts malintencionados.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones

-   Reemplace el argumento no seguro XsltSettings por XsltSettings.<xref:System.Xml.Xsl.XsltSettings.Default%2A> o con una instancia que ha deshabilitado la ejecución de función y el script del documento.

-   Reemplace el argumento <xref:System.Xml.XmlResolver> por NULL o una instancia <xref:System.Xml.XmlSecureResolver> .

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 A menos que esté seguro de que la entrada es de un origen de confianza, no suprima ninguna regla de esta advertencia.

## <a name="pseudo-code-examples"></a>Ejemplos de pseudocódigo

### <a name="violation"></a>Infracción

```csharp
using System.Xml;
using System.Xml.Xsl;

namespace TestNamespace
{
    class TestClass
    {
         void TestMethod()
        {
             XslCompiledTransform xslCompiledTransform = new XslCompiledTransform();
             var settings = XsltSettings.TrustedXslt;
             var resolver = new XmlUrlResolver();
             xslCompiledTransform.Load("testStylesheet", settings, resolver); // warn
        }
    }
} 
```

### <a name="solution"></a>Soluciones

```csharp
using System.Xml;
using System.Xml.Xsl;

namespace TestNamespace
{
    class TestClass
    {
        void TestMethod()
        {
            XslCompiledTransform xslCompiledTransform = new XslCompiledTransform();
            var settings = XsltSettings.Default;
            var resolver = new XmlUrlResolver();
            xslCompiledTransform.Load("testStylesheet", settings, resolver);
        }
    }
}
```

### <a name="violation"></a>Infracción

```csharp
using System.Xml;
using System.Xml.Xsl;

namespace TestNamespace
{
    class TestClass
    {
        private static void TestMethod(XsltSettings settings)
        {
            try
            {
                XslCompiledTransform xslCompiledTransform = new XslCompiledTransform();
                var resolver = new XmlUrlResolver();
                xslCompiledTransform.Load("testStylesheet", settings, resolver); // warn
            }
            catch { throw; }
            finally { }
        }
    }
}
```

### <a name="solution"></a>Soluciones

```csharp
using System.Xml;
using System.Xml.Xsl;

namespace TestNamespace
{
    class TestClass
    {
        private static void TestMethod(XsltSettings settings)
        {
            try
            {
                XslCompiledTransform xslCompiledTransform = new XslCompiledTransform();
                settings.EnableDocumentFunction = false;
                settings.EnableScript = false;
                var resolver = new XmlUrlResolver();
                xslCompiledTransform.Load("testStylesheet", settings, resolver);
            }
            catch { throw; }
            finally { }
        }
    }
}
```



