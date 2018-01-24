---
title: "CA3076: Ejecución del Script XSLT insegura | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 66d415b792558dce91de0205ee688fecb5caa182
ms.sourcegitcommit: 49aa031cbebdd9c7ec070c713afb1a97d1ecb701
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2018
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

**XSLT** es un estándar de World Wide Web Consortium (W3C) para transformar los datos XML. XSLT normalmente se usa para escribir hojas de estilos para transformar datos XML en otros formatos, como HTML, texto de longitud fija, texto separado por comas o un formato XML distinto. Aunque está prohibido de forma predeterminada, puede habilitarlo para su proyecto.

Para garantizar que no expone una superficie a ataques, esta regla se desencadena cada vez que XslCompiledTransform.<xref:System.Xml.Xsl.XslCompiledTransform.Load%2A> recibe instancias de combinación no seguras de <xref:System.Xml.Xsl.XsltSettings> y <xref:System.Xml.XmlResolver>, lo que permite el procesamiento de scripts malintencionados.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones

- Reemplace el argumento no seguro XsltSettings por XsltSettings.<xref:System.Xml.Xsl.XsltSettings.Default%2A> o por una instancia que tenga deshabilitada la función de documento y la ejecución de scripts.

- Reemplace el argumento <xref:System.Xml.XmlResolver> por NULL o una instancia <xref:System.Xml.XmlSecureResolver> .

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias

A menos que esté seguro de que la entrada es de un origen de confianza, no suprima ninguna regla de esta advertencia.

## <a name="pseudo-code-examples"></a>Ejemplos de pseudocódigo

### <a name="violationmdashuses-xsltsettingstrustedxslt"></a>Infracción de&mdash;utiliza XsltSettings.TrustedXslt

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

### <a name="solutionmdashuse-xsltsettingsdefault"></a>Solución&mdash;usar XsltSettings.Default

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

### <a name="solutionmdashdisable-document-function-and-script-execution"></a>Solución&mdash;deshabilitar la ejecución de script y la función de documento

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

[Consideraciones de seguridad XSLT (Guía de. NET)](/dotnet/standard/data/xml/xslt-security-considerations)