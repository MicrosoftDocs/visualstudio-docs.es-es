---
title: Directiva de parámetro T4
description: Aprenda que en Visual Studio, la Directiva de parámetros declara propiedades en el código de plantilla que se inicializan a partir de los valores que se pasan desde el contexto externo.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: fe68d31d214ae4be8fca35f1e90e63690f3ad581
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99924604"
---
# <a name="t4-parameter-directive"></a>Directiva de parámetro T4

En una plantilla de texto de Visual Studio, la `parameter` directiva declara propiedades en el código de plantilla que se inicializan a partir de los valores que se pasan desde el contexto externo. Puede establecer estos valores si escribe código que invoca la transformación de texto.

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
 Si está escribiendo una extensión de Visual Studio, como un comando de menú o un controlador de eventos, puede procesar una plantilla mediante el servicio de plantillas de texto:

```csharp
// Get a service provider - how you do this depends on the context:
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

## <a name="passing-values-to-a-run-time-preprocessed-text-template"></a>Pasar valores a una plantilla de texto Run-Time (preprocesada)
 Normalmente no es necesario usar la `<#@parameter#>` Directiva con plantillas de texto en tiempo de ejecución (preprocesadas). En su lugar, puede definir un constructor adicional o una propiedad configurable para el código generado, a través del cual se pasan los valores de parámetro. Para obtener más información, vea [Generación de texto en tiempo de ejecución con plantillas de texto T4](../modeling/run-time-text-generation-with-t4-text-templates.md).

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
> La `parameter` Directiva no recupera los valores establecidos en el `-a` parámetro de la `TextTransform.exe` utilidad. Para obtener esos valores, establezca `hostSpecific="true"` en la `template` Directiva y use `this.Host.ResolveParameterValue("","","argName")` .
