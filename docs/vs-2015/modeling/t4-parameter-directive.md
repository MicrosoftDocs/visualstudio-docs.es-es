---
title: Directiva de parámetro T4 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
ms.assetid: 1d590387-1d9d-40a5-a72c-65fae7a8bdf3
caps.latest.revision: 5
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 7c1849cbccc1a903716ba94d02f47a339d6ce426
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "72658572"
---
# <a name="t4-parameter-directive"></a>Directiva de parámetro T4
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

En una [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] plantilla de texto, la `parameter` directiva declara propiedades en el código de plantilla que se inicializan a partir de los valores que se pasan desde el contexto externo. Puede establecer estos valores si escribe código que invoca la transformación de texto.

## <a name="using-the-parameter-directive"></a>Usar la Directiva de parámetros

```
<#@ parameter type="Full.TypeName" name="ParameterName" #>
```

 La `parameter` directiva declara propiedades en el código de plantilla que se inicializan a partir de los valores que se pasan desde el contexto externo. Puede establecer estos valores si escribe código que invoca la transformación de texto. Los valores se pueden pasar en el `Session` Diccionario o en <xref:System.Runtime.Remoting.Messaging.CallContext> .

 Puede declarar parámetros de cualquier tipo utilizable de forma remota. Es decir, el tipo se debe declarar con <xref:System.SerializableAttribute> o debe derivarse de <xref:System.MarshalByRefObject> . Esto permite pasar los valores de parámetro al AppDomain en el que se procesa la plantilla.

 Por ejemplo, puede escribir una plantilla de texto con el siguiente contenido:

```
<#@ template language="C#" #>

<#@ parameter type="System.Int32" name="TimesToRepeat" #>

<# for (int i = 0; i < TimesToRepeat; i++) { #>
Line <#= i #>
<# } #>

```

## <a name="passing-parameter-values-to-a-template"></a>Pasar valores de parámetro a una plantilla
 Si está escribiendo una extensión, como [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] un comando de menú o un controlador de eventos, puede procesar una plantilla mediante el servicio de plantillas de texto:

```csharp
// Get a service provider – how you do this depends on the context:
IServiceProvider serviceProvider = dte; // or dslDiagram.Store, for example
// Get the text template service:
ITextTemplating t4 = serviceProvider.GetService(typeof(STextTemplating)) as ITextTemplating;
ITextTemplatingSessionHost host = t4 as ITextTemplatingSessionHost;
// Create a Session in which to pass parameters:
host.Session = host.CreateSession();
// Add parameter values to the Session:
session["TimesToRepeat"] = 5;
// Process a text template:
string result = t4.ProcessTemplate("MyTemplateFile.t4",
  System.IO.File.ReadAllText("MyTemplateFile.t4"));

```

## <a name="passing-values-in-the-call-context"></a>Pasar valores en el contexto de llamada
 También puede pasar valores como datos lógicos en <xref:System.Runtime.Remoting.Messaging.CallContext> .

 En el ejemplo siguiente se pasan valores mediante ambos métodos:

```csharp
ITextTemplating t4 = this.Store.GetService(typeof(STextTemplating)) as ITextTemplating;
ITextTemplatingSessionHost host = t4 as ITextTemplatingSessionHost;
host.Session = host.CreateSession();
// Pass a value in Session:
host.Session["p1"] = 32;
// Pass another value in CallContext:
System.Runtime.Remoting.Messaging.CallContext.LogicalSetData("p2", "test");

// Process a small template inline:
string result = t4.ProcessTemplate("",
   "<#@parameter type=\"System.Int32\" name=\"p1\"#>"
 + "<#@parameter type=\"System.String\" name=\"p2\"#>"
 + "Test <#=p1#> <#=p2#>");

// Result value is:
//     Test 32 test

```

## <a name="passing-values-to-a-run-time-preprocessed-text-template"></a>Pasar valores a una plantilla de texto en tiempo de ejecución (preprocesada)
 Normalmente no es necesario usar la `<#@parameter#>` Directiva con plantillas de texto en tiempo de ejecución (preprocesadas). En su lugar, puede definir un constructor adicional o una propiedad configurable para el código generado, a través del cual se pasan los valores de parámetro. Para obtener más información, vea [generación de texto en tiempo de ejecución con plantillas de texto T4](../modeling/run-time-text-generation-with-t4-text-templates.md).

 Sin embargo, si desea usar `<#@parameter>` en una plantilla en tiempo de ejecución, puede pasar valores a ella mediante el Diccionario de sesión. Por ejemplo, supongamos que ha creado el archivo como una plantilla preprocesada denominada `PreTextTemplate1` . Puede invocar la plantilla en el programa mediante el código siguiente.

```csharp
PreTextTemplate1 t = new PreTextTemplate1();
t.Session = new Microsoft.VisualStudio.TextTemplating.TextTemplatingSession();
t.Session["TimesToRepeat"] = 5;
// Add other parameter values to t.Session here.
t.Initialize(); // Must call this to transfer values.
string resultText = t.TransformText();

```

## <a name="obtaining-arguments-from-texttemplateexe"></a>Obtener argumentos de TextTemplate.exe

> [!IMPORTANT]
> La `parameter` Directiva no recupera los valores establecidos en el `–a` parámetro de la `TextTransform.exe` utilidad. Para obtener esos valores, establezca `hostSpecific="true"` en la `template` Directiva y use `this.Host.ResolveParameterValue("","","argName")` .
