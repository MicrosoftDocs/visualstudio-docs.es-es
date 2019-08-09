---
title: Invocar la transformación de texto en una extensión de VS
ms.date: 11/04/2016
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7bf32a1722ec8029840566b7602ba78f84adb7ec
ms.sourcegitcommit: 2da366ba9ad124366f6502927ecc720985fc2f9e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/09/2019
ms.locfileid: "68870519"
---
# <a name="invoke-text-transformation-in-a-visual-studio-extension"></a>Invocar la transformación de texto en una extensión de Visual Studio

Si está escribiendo una extensión de Visual Studio, como un comando de menú o un [lenguaje específico de dominio](../modeling/modeling-sdk-for-visual-studio-domain-specific-languages.md), puede utilizar el servicio de plantillas de texto para transformar las plantillas de texto. Obtiene el servicio [STextTemplating](/previous-versions/visualstudio/visual-studio-2012/bb932394(v=vs.110)) y lo convierte en [ITextTemplating](/previous-versions/visualstudio/visual-studio-2012/bb932392(v=vs.110)).

## <a name="get-the-text-templating-service"></a>Obtener el servicio de plantillas de texto

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

 Para el tipo de parámetro, debe utilizar un tipo que sea serializable o que pueda calcular las referencias. Es decir, el tipo se debe declarar con <xref:System.SerializableAttribute> o se debe derivar desde <xref:System.MarshalByRefObject>. Esta restricción es necesaria porque la plantilla de texto se ejecuta en un AppDomain independiente. Todos los tipos integrados, como **System. String** y **System. Int32** , son serializables.

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

## <a name="error-reporting-and-the-output-directive"></a>Informes de errores y la Directiva de salida

Cualquier error que se produzca durante el procesamiento se mostrará en la ventana de error de Visual Studio. Además, se puede notificar los errores especificando una devolución de llamada que implemente [ITextTemplatingCallback](/previous-versions/visualstudio/visual-studio-2012/bb932397(v=vs.110)).

Si desea escribir la cadena de resultado a un archivo, puede que desee conocer la extensión de archivo y codificación que se han especificado en la directiva `<#@output#>` de la plantilla. Esta información también se pasará a la devolución de llamada. Para obtener más información, consulte [la Directiva de salida T4](../modeling/t4-output-directive.md).

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

La advertencia del compilador aparecerá en la ventana de error de Visual Studio y también generará una `ErrorCallback`llamada a.

## <a name="reference-parameters"></a>Parámetros de referencia

Puede pasar valores de una plantilla de texto mediante una clase de parámetro que se deriva de <xref:System.MarshalByRefObject>.

## <a name="related-articles"></a>Artículos relacionados

Para generar texto en una plantilla de texto preprocesada: Llame al método `TransformText()` de la clase generada. Para obtener más información, vea [generación de texto en tiempo de ejecución con plantillas de texto T4](../modeling/run-time-text-generation-with-t4-text-templates.md).

Para generar texto fuera de una extensión de Visual Studio: Defina un host personalizado. Para obtener más información, consulte [de procesamiento de plantillas de texto mediante el uso de un Host personalizado](../modeling/processing-text-templates-by-using-a-custom-host.md).

Para generar código fuente que se puede compilar y ejecutar más tarde: Llame al método [PreprocessTemplate](/previous-versions/visualstudio/visual-studio-2012/ee844321(v=vs.110)) de [ITextTemplating](/previous-versions/visualstudio/visual-studio-2012/bb932392(v=vs.110)).
