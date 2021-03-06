---
title: Invocar la transformación de texto en una extensión de VS
description: Obtenga información sobre cómo puede usar el servicio de plantillas de texto para transformar plantillas de texto. Obtenga también información sobre cómo obtener el servicio STextTemplating y convertirlo en ITextTemplating.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 71f376cbe0ffd6c2716802977f1570aa5036fcdb
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/19/2021
ms.locfileid: "112386779"
---
# <a name="invoke-text-transformation-in-a-visual-studio-extension"></a>Invocación de la transformación de texto en Visual Studio extensión

Si está escribiendo una extensión Visual Studio, como un comando de menú o un lenguaje específico del [dominio,](../modeling/modeling-sdk-for-visual-studio-domain-specific-languages.md)puede usar el servicio de plantillas de texto para transformar plantillas de texto. Obtenga el [servicio STextTemplating](/previous-versions/visualstudio/visual-studio-2012/bb932394(v=vs.110)) y conéctelo a [ITextTemplating](/previous-versions/visualstudio/visual-studio-2012/bb932392(v=vs.110)).

## <a name="get-the-text-templating-service"></a>Obtener el servicio de templación de texto

```csharp
using Microsoft.VisualStudio.TextTemplating;
using Microsoft.VisualStudio.TextTemplating.VSHost;
...
// Get a service provider - how you do this depends on the context:
IServiceProvider serviceProvider = ...; // An instance of EnvDTE, for example

// Get the text template service:
ITextTemplating t4 = serviceProvider.GetService(typeof(STextTemplating)) as ITextTemplating;

// Process a text template:
string result = t4.ProcessTemplate(filePath, System.IO.File.ReadAllText(filePath));
```

## <a name="pass-parameters-to-the-template"></a>Pasar parámetros a la plantilla

 Puede pasar parámetros en la plantilla. Dentro de la plantilla, puede obtener los valores de parámetro mediante la directiva `<#@parameter#>`.

 Para el tipo de parámetro, debe utilizar un tipo que sea serializable o que pueda calcular las referencias. Es decir, el tipo se debe declarar con <xref:System.SerializableAttribute> o se debe derivar desde <xref:System.MarshalByRefObject>. Esta restricción es necesaria porque la plantilla de texto se ejecuta en un AppDomain independiente. Todos los tipos integrados, **como System.String** y **System.Int32,** son serializables.

 Para pasar valores de parámetro, el código de llamada puede colocar los valores en el diccionario `Session` o en el <xref:System.Runtime.Remoting.Messaging.CallContext>.

 En el siguiente ejemplo se utilizan ambos métodos para transformar una plantilla de pruebas corta:

```csharp
using Microsoft.VisualStudio.TextTemplating;
using Microsoft.VisualStudio.TextTemplating.VSHost;
...
// Get a service provider - how you do this depends on the context:
IServiceProvider serviceProvider = dte;

// Get the text template service:
ITextTemplating t4 = serviceProvider.GetService(typeof(STextTemplating)) as ITextTemplating;
ITextTemplatingSessionHost sessionHost = t4 as ITextTemplatingSessionHost;

// Create a Session in which to pass parameters:
sessionHost.Session = sessionHost.CreateSession();
sessionHost.Session["parameter1"] = "Hello";
sessionHost.Session["parameter2"] = DateTime.Now;

// Pass another value in CallContext:
System.Runtime.Remoting.Messaging.CallContext.LogicalSetData("parameter3", 42);

// Process a text template:
string result = t4.ProcessTemplate("",
   // This is the test template:
   "<#@parameter type=\"System.String\" name=\"parameter1\"#>"
 + "<#@parameter type=\"System.DateTime\" name=\"parameter2\"#>"
 + "<#@parameter type=\"System.Int32\" name=\"parameter3\"#>"
 + "Test: <#=parameter1#>    <#=parameter2#>    <#=parameter3#>");

// This test code yields a result similar to the following line:
//     Test: Hello    07/06/2010 12:37:45    42
```

## <a name="error-reporting-and-the-output-directive"></a>Informes de errores y la directiva de salida

Los errores que surjan durante el procesamiento se mostrarán en la ventana Visual Studio error. Además, puede recibir una notificación de errores especificando una devolución de llamada que implemente [ITextTemplatingCallback](/previous-versions/visualstudio/visual-studio-2012/bb932397(v=vs.110)).

Si desea escribir la cadena de resultado a un archivo, puede que desee conocer la extensión de archivo y codificación que se han especificado en la directiva `<#@output#>` de la plantilla. Esta información también se pasará a la devolución de llamada. Para obtener más información, vea [Directiva de salida T4](../modeling/t4-output-directive.md).

```csharp
void ProcessMyTemplate(string MyTemplateFile)
{
  string templateContent = File.ReadAllText(MyTemplateFile);
  T4Callback cb = new T4Callback();
  // Process a text template:
  string result = t4.ProcessTemplate(MyTemplateFile, templateContent, cb);
  // If there was an output directive in the MyTemplateFile,
  // then cb.SetFileExtension() will have been called.
  // Determine the output file name:
  string resultFileName =
    Path.Combine(Path.GetDirectoryName(MyTemplateFile),
        Path.GetFileNameWithoutExtension(MyTemplateFile))
      + cb.fileExtension;
  // Write the processed output to file:
  File.WriteAllText(resultFileName, result, cb.outputEncoding);
  // Append any error messages:
  if (cb.errorMessages.Count > 0)
  {
    File.AppendAllLines(resultFileName, cb.errorMessages);
  }
}

class T4Callback : ITextTemplatingCallback
{
  public List<string> errorMessages = new List<string>();
  public string fileExtension = ".txt";
  public Encoding outputEncoding = Encoding.UTF8;

  public void ErrorCallback(bool warning, string message, int line, int column)
  { errorMessages.Add(message); }

  public void SetFileExtension(string extension)
  { fileExtension = extension; }

  public void SetOutputEncoding(Encoding encoding, bool fromOutputDirective)
  { outputEncoding = encoding; }
}
```

El código se puede probar con un archivo de plantilla similar al siguiente:

```
<#@output extension=".htm" encoding="ASCII"#>
<# int unused;  // Compiler warning "unused variable"
#>
Sample text.
```

La advertencia del compilador aparecerá en Visual Studio ventana de error y también generará una llamada a `ErrorCallback` .

## <a name="reference-parameters"></a>Parámetros de referencia

Puede pasar valores de una plantilla de texto mediante una clase de parámetro que se deriva de <xref:System.MarshalByRefObject>.

## <a name="related-articles"></a>Artículos relacionados

Para generar texto a partir de una plantilla de texto preprocesado: llame al `TransformText()` método de la clase generada. Para obtener más información, vea [Generación de texto en tiempo de ejecución con plantillas de texto T4](../modeling/run-time-text-generation-with-t4-text-templates.md).

Para generar texto fuera de una extensión Visual Studio: defina un host personalizado. Para obtener más información, vea [Procesamiento de plantillas de texto mediante un host personalizado.](../modeling/processing-text-templates-by-using-a-custom-host.md)

Para generar código fuente que se pueda compilar y ejecutar más adelante: llame al [método PreprocessTemplate](/previous-versions/visualstudio/visual-studio-2012/ee844321(v=vs.110)) [de ITextTemplating](/previous-versions/visualstudio/visual-studio-2012/bb932392(v=vs.110)).
