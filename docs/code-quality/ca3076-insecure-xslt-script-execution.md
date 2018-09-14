---
title: 'CA3076: Ejecución del script XSLT no segura'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 74fe556d775e60dec5dde4528a1924e55ab4c2ed
ms.sourcegitcommit: 568bb0b944d16cfe1af624879fa3d3594d020187
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/13/2018
ms.locfileid: "45546397"
---
# <a name="ca3076-insecure-xslt-script-execution"></a>CA3076: Ejecución del script XSLT no segura

|||
|-|-|
|TypeName|InsecureXSLTScriptExecution|
|Identificador de comprobación|CA3076|
|Categoría|Microsoft.Security|
|Cambio problemático|No trascendental|

## <a name="cause"></a>Motivo

Si ejecuta el lenguaje de transformación basado en hojas de estilo (XSLT) en aplicaciones .NET de forma insegura, el procesador podría resolver referencias URI que no sean de confianza y que podrían revelar información confidencial a atacantes, dando lugar a ataques de denegación de servicio y entre sitios. Para obtener más información, consulte [XSLT seguridad Considerations(.NET Guide)](/dotnet/standard/data/xml/xslt-security-considerations).

## <a name="rule-description"></a>Descripción de la regla

**XSLT** es un estándar de World Wide Web Consortium (W3C) para transformar datos XML. XSLT normalmente se usa para escribir hojas de estilos para transformar datos XML en otros formatos, como HTML, texto de longitud fija, texto separado por comas o un formato distinto de XML. Aunque está prohibido de forma predeterminada, puede habilitarlo para su proyecto.

Para asegurarse de que no expone una superficie expuesta a ataques, esta regla se desencadena cada vez que el XslCompiledTransform.<xref:System.Xml.Xsl.XslCompiledTransform.Load%2A> recibe las instancias de combinación no seguras de <xref:System.Xml.Xsl.XsltSettings> y <xref:System.Xml.XmlResolver>, lo que permite el procesamiento de scripts malintencionados.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones

- Reemplace el argumento no seguro XsltSettings por XsltSettings.<xref:System.Xml.Xsl.XsltSettings.Default%2A> o con una instancia que ha deshabilitado la ejecución de función y el script del documento.

- Reemplace el argumento <xref:System.Xml.XmlResolver> por NULL o una instancia <xref:System.Xml.XmlSecureResolver> .

## <a name="when-to-suppress-warnings"></a>Cuándo Suprimir advertencias

A menos que esté seguro de que la entrada es de un origen de confianza, no suprima ninguna regla de esta advertencia.

## <a name="pseudo-code-examples"></a>Ejemplos de pseudocódigo

### <a name="violation-that-uses-xsltsettingstrustedxslt"></a>Infracción que usa XsltSettings.TrustedXslt

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

### <a name="solution-that-uses-xsltsettingsdefault"></a>Solución que usa XsltSettings.Default

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

### <a name="violationmdashdocument-function-and-script-execution-not-disabled"></a>Infracción de&mdash;documentar la función y la secuencia de comandos de ejecución no deshabilitada

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

### <a name="solutionmdashdisable-document-function-and-script-execution"></a>Solución&mdash;deshabilitar la ejecución de función y la secuencia de comandos de documento

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

## <a name="see-also"></a>Vea también

- [Consideraciones de seguridad XSLT (Guía de. NET)](/dotnet/standard/data/xml/xslt-security-considerations)