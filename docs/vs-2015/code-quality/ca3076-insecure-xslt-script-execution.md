---
title: 'CA3076: ejecución de script XSLT no segura | Microsoft Docs'
ms.date: 11/15/2016
ms.technology: vs-ide-code-analysis
ms.topic: reference
ms.assetid: 53cb7a46-c564-488f-bc51-0e210a7853c9
caps.latest.revision: 7
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 2b3e06bb7a150c4bb07eefc0571818f1127fe460
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "85545124"
---
# <a name="ca3076-insecure-xslt-script-execution"></a>CA3076: Ejecución del script XSLT no segura
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Elemento|Value|
|-|-|
|TypeName|InsecureXSLTScriptExecution|
|Identificador de comprobación|CA3076|
|Category|Microsoft.Security|
|Cambio problemático|No trascendental|

## <a name="cause"></a>Causa
 Si ejecuta las [transformaciones del lenguaje de hojas de estilo extensible (XSLT)](https://support.microsoft.com/kb/313997) en aplicaciones .net de forma no segura, el procesador puede [resolver referencias de URI](https://msdn.microsoft.com/ba3e4d4f-1ee7-4226-a51a-78a1f1b5bd8a) que no son de confianza y que podrían revelar información confidencial a atacantes, lo que provoca ataques de denegación de servicio y entre sitios.

## <a name="rule-description"></a>Descripción de la regla
 [XSLT](https://msdn.microsoft.com/6377ce5f-3c45-42a6-b7a9-ec8da588b60c) es un estándar de World Wide Web Consortium (W3C) para transformar datos XML. XSLT normalmente se usa para escribir hojas de estilos para transformar datos XML en otros formatos, como HTML, texto de longitud fija, texto separado por comas o un formato XML distinto. Aunque está prohibido de forma predeterminada, puede habilitarlo para su proyecto.

 Para asegurarse de que no expone una superficie expuesta a ataques, esta regla se desencadena cuando XslCompiledTransform.<xref:System.Xml.Xsl.XslCompiledTransform.Load%2A> recibe instancias de combinación no seguras de <xref:System.Xml.Xsl.XsltSettings> y <xref:System.Xml.XmlResolver> , lo que permite el procesamiento de scripts malintencionados.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones

- Reemplace el argumento XsltSettings inseguro por XsltSettings.<xref:System.Xml.Xsl.XsltSettings.Default%2A> o con una instancia de que ha deshabilitado la función de documento y la ejecución de scripts.

- Reemplace el argumento <xref:System.Xml.XmlResolver> por NULL o una instancia <xref:System.Xml.XmlSecureResolver> .

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

### <a name="solution"></a>Solución

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

### <a name="solution"></a>Solución

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
