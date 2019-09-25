---
title: 'CA3076: Ejecución del script XSLT no segura'
ms.date: 11/04/2016
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1c6c5df0109a8cff3cefcc308ea27077ef0fbe03
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/24/2019
ms.locfileid: "71237074"
---
# <a name="ca3076-insecure-xslt-script-execution"></a>CA3076: Ejecución del script XSLT no segura

|||
|-|-|
|TypeName|InsecureXSLTScriptExecution|
|Identificador de comprobación|CA3076|
|Categoría|Microsoft.Security|
|Cambio importante|Poco problemático|

## <a name="cause"></a>Motivo

Si ejecuta el lenguaje de transformación basado en hojas de estilo (XSLT) en aplicaciones .NET de forma insegura, el procesador podría resolver referencias URI que no sean de confianza y que podrían revelar información confidencial a atacantes, dando lugar a ataques de denegación de servicio y entre sitios. Para obtener más información, vea [consideraciones de seguridad de XSLT (.net Guide)](/dotnet/standard/data/xml/xslt-security-considerations).

## <a name="rule-description"></a>Descripción de la regla

**XSLT** es un estándar de World Wide Web Consortium (W3C) para transformar datos XML. XSLT normalmente se usa para escribir hojas de estilos para transformar datos XML en otros formatos, como HTML, texto de longitud fija, texto separado por comas o un formato XML distinto. Aunque está prohibido de forma predeterminada, puede habilitarlo para su proyecto.

Para asegurarse de que no expone una superficie expuesta a ataques, esta regla se desencadena cuando XslCompiledTransform.<xref:System.Xml.Xsl.XslCompiledTransform.Load%2A> recibe instancias de combinación no seguras <xref:System.Xml.Xsl.XsltSettings> de <xref:System.Xml.XmlResolver>y, lo que permite el procesamiento de scripts malintencionados.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones

- Reemplace el argumento XsltSettings inseguro por XsltSettings.<xref:System.Xml.Xsl.XsltSettings.Default%2A> o con una instancia de que ha deshabilitado la función de documento y la ejecución de scripts.

- Reemplace el argumento <xref:System.Xml.XmlResolver> por NULL o una instancia <xref:System.Xml.XmlSecureResolver> .

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias

A menos que esté seguro de que la entrada es de un origen de confianza, no suprima ninguna regla de esta advertencia.

## <a name="pseudo-code-examples"></a>Ejemplos de pseudocódigo

### <a name="violation-that-uses-xsltsettingstrustedxslt"></a>Infracción que usa XsltSettings. TrustedXslt

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

### <a name="solution-that-uses-xsltsettingsdefault"></a>Solución que usa XsltSettings. default

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

### <a name="violationmdashdocument-function-and-script-execution-not-disabled"></a>Función&mdash;de documento de infracción y ejecución de script no deshabilitada

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

### <a name="solutionmdashdisable-document-function-and-script-execution"></a>Solución&mdash;deshabilite la función de documento y la ejecución de script

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

- [Consideraciones de seguridad de XSLT (Guía de .net)](/dotnet/standard/data/xml/xslt-security-considerations)