---
title: "T4 Parameter Directive | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-tfs-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 1d590387-1d9d-40a5-a72c-65fae7a8bdf3
caps.latest.revision: 3
caps.handback.revision: 3
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
---
# T4 Parameter Directive
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

En una plantilla de texto de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], la directiva `parameter` declara propiedades en el código de plantilla que se inicializan a partir de los valores pasados desde el contexto externo.  Puede establecer estos valores si escribe el código que invocará a la transformación de texto.  
  
## Usar la directiva de parámetro  
  
```  
<#@ parameter type="Full.TypeName" name="ParameterName" #>  
```  
  
 La directiva `parameter` declara propiedades en el código de plantilla que se inicializan a partir de los valores pasados desde el contexto externo.  Puede establecer estos valores si escribe el código que invocará a la transformación de texto.  Los valores se pueden pasar en el diccionario `Session` o en <xref:System.Runtime.Remoting.Messaging.CallContext>.  
  
 Puede declarar parámetros de cualquier tipo remoto.  Es decir, el tipo se debe declarar con <xref:System.SerializableAttribute> o se debe derivar desde <xref:System.MarshalByRefObject>.  Esto permite pasar valores de parámetro en el AppDomain en el que se procesa la plantilla.  
  
 Por ejemplo, podría escribir a una plantilla de texto con el siguiente contenido:  
  
```  
<#@ template language="C#" #>  
  
<#@ parameter type="System.Int32" name="TimesToRepeat" #>  
  
<# for (int i = 0; i < TimesToRepeat; i++) { #>  
Line <#= i #>  
<# } #>  
  
```  
  
## Pasar valores de parámetro a una plantilla  
 Si está escribiendo una extensión de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] como un comando de menú o un controlador de eventos, puede procesar una plantilla utilizando el servicio de plantillas de texto:  
  
```c#  
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
  
## Pasar valores en el contexto de llamada  
 Alternativamente, puede pasar valores como datos lógicos en <xref:System.Runtime.Remoting.Messaging.CallContext>.  
  
 En el siguiente ejemplo se pasan valores utilizando ambos métodos:  
  
```c#  
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
  
## Pasar valores a una plantilla texto \(preprocesada\) en tiempo de ejecución  
 Por lo general, no es necesario utilizar la directiva `<#@parameter#>` con plantillas de texto \(preprocesadas\) en tiempo de ejecución.  En su lugar, puede definir un constructor adicional o una propiedad configurable para el código generado, a través del cual se pasan valores de parámetro.  Para obtener más información, vea [Run\-Time Text Generation with T4 Text Templates](../modeling/run-time-text-generation-with-t4-text-templates.md).  
  
 Sin embargo, si desea utilizar `<#@parameter>` en una plantilla en tiempo de ejecución, puede pasar los valores a la plantilla utilizando el Diccionario de la sesión.  Por ejemplo, suponga que ha creado el archivo como una plantilla preprocesada denominada `PreTextTemplate1`.  Puede invocar a la plantilla en su programa mediante el siguiente código.  
  
```c#  
PreTextTemplate1 t = new PreTextTemplate1();  
t.Session = new Microsoft.VisualStudio.TextTemplating.TextTemplatingSession();  
t.Session["TimesToRepeat"] = 5;  
// Add other parameter values to t.Session here.  
t.Initialize(); // Must call this to transfer values.  
string resultText = t.TransformText();  
  
```  
  
## Obtener argumentos a partir de TextTemplate.exe  
  
> [!IMPORTANT]
>  La directiva `parameter` no recupera el conjunto de valores en el parámetro `–a` de la utilidad `TextTransform.exe`.  Para obtener esos valores, establezca `hostSpecific="true"` en la directiva `template` y utilice `this.Host.ResolveParameterValue("","","argName")`.