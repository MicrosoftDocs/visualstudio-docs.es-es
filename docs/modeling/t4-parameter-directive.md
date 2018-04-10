---
title: T4 Directiva de parámetro | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.topic: article
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.technology: vs-ide-modeling
ms.openlocfilehash: f44e25f9256cd37692970e92744d7564bc3abd19
ms.sourcegitcommit: 3b692c9bf332b7b9150901e16daf99a64b599fee
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/10/2018
---
# <a name="t4-parameter-directive"></a>Directiva de parámetro T4
En un [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] plantilla de texto, el `parameter` directiva declara propiedades en el código de plantilla que se inicializan de valores que se pasan desde el contexto externo. Puede establecer estos valores si escribe código que invoca la transformación de texto.  
  
## <a name="using-the-parameter-directive"></a>Mediante la directiva de parámetro  
  
```  
<#@ parameter type="Full.TypeName" name="ParameterName" #>  
```  
  
 El `parameter` directiva declara propiedades en el código de plantilla que se inicializan de valores que se pasan desde el contexto externo. Puede establecer estos valores si escribe código que invoca la transformación de texto. Los valores se pueden pasar en el `Session` diccionario, o en <xref:System.Runtime.Remoting.Messaging.CallContext>.  
  
 Puede declarar parámetros de cualquier tipo de uso remoto. Es decir, el tipo debe declararse con <xref:System.SerializableAttribute>, o debe derivar de <xref:System.MarshalByRefObject>. Esto permite que los valores de parámetro que se pasan en el dominio de aplicación en el que se procesa la plantilla.  
  
 Por ejemplo, podría escribir una plantilla de texto con el siguiente contenido:  
  
```  
<#@ template language="C#" #>  
  
<#@ parameter type="System.Int32" name="TimesToRepeat" #>  
  
<# for (int i = 0; i < TimesToRepeat; i++) { #>  
Line <#= i #>  
<# } #>  
  
```  
  
## <a name="passing-parameter-values-to-a-template"></a>Pasar valores de parámetro a una plantilla  
 Si está escribiendo un [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] extensión, como un comando de menú o un controlador de eventos, puede procesar una plantilla mediante el servicio de plantillas de texto:  
  
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
  
## <a name="passing-values-in-the-call-context"></a>Pasar valores en el contexto de llamadas  
 También puede pasar valores de datos lógicos como en <xref:System.Runtime.Remoting.Messaging.CallContext>.  
  
 En el ejemplo siguiente se pasa valores mediante el uso de ambos métodos:  
  
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
  
## <a name="passing-values-to-a-run-time-preprocessed-text-template"></a>Pasar valores a una plantilla de texto (preprocesada) en tiempo de ejecución  
 No suele ser necesario usar el `<#@parameter#>` directiva con plantillas de texto en tiempo de ejecución (preprocesadas). En su lugar, puede definir un constructor adicional o una propiedad configurable para el código generado, a través del cual pasar valores de parámetro. Para obtener más información, consulte [tiempo de ejecución de generación de texto con plantillas de texto T4](../modeling/run-time-text-generation-with-t4-text-templates.md).  
  
 Sin embargo, si desea usar `<#@parameter>` en una plantilla en tiempo de ejecución, puede pasar valores a él mediante el diccionario de sesión. Por ejemplo, supongamos que ha creado el archivo como una plantilla preprocesada denominada `PreTextTemplate1`. Puede invocar la plantilla en el programa mediante el código siguiente.  
  
```csharp  
PreTextTemplate1 t = new PreTextTemplate1();  
t.Session = new Microsoft.VisualStudio.TextTemplating.TextTemplatingSession();  
t.Session["TimesToRepeat"] = 5;  
// Add other parameter values to t.Session here.  
t.Initialize(); // Must call this to transfer values.  
string resultText = t.TransformText();  
  
```  
  
## <a name="obtaining-arguments-from-texttemplateexe"></a>Obtener los argumentos de TextTemplate.exe  
  
> [!IMPORTANT]
>  El `parameter` directiva no recuperar valores establecidos en el `-a` parámetro de la `TextTransform.exe` utilidad. Para obtener estos valores, establezca `hostSpecific="true"` en el `template` directiva y usar `this.Host.ResolveParameterValue("","","argName")`.