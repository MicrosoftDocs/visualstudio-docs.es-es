---
title: Métodos de utilidad de las plantillas de texto
description: Obtenga información sobre los distintos métodos de utilidad de plantilla de texto que están disponibles al escribir código en Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- text templates, utility methods
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: b45bf6418562da5315c986a64a1295c137e982d6
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/19/2021
ms.locfileid: "112388690"
---
# <a name="text-template-utility-methods"></a>Métodos de utilidad de las plantillas de texto

Hay varios métodos que siempre están disponibles al escribir código en una plantilla Visual Studio texto. Estos métodos se definen en <xref:Microsoft.VisualStudio.TextTemplating.TextTransformation> .

> [!TIP]
> También puede usar otros métodos y servicios proporcionados por el entorno host en una plantilla de texto normal (no preprocesada). Por ejemplo, puede resolver rutas de acceso de archivo, errores de registro y obtener servicios proporcionados por Visual Studio y los paquetes cargados. Para obtener más información, vea [Accessing Visual Studio from a Text Template](/previous-versions/visualstudio/visual-studio-2010/gg604090\(v\=vs.100\)).

## <a name="write-methods"></a>Escribir métodos

Puede usar los `Write()` `WriteLine()` métodos y para anexar texto dentro de un bloque de código estándar, en lugar de usar un bloque de código de expresión. Los dos bloques de código siguientes son funcionalmente equivalentes.

### <a name="code-block-with-an-expression-block"></a>Bloque de código con un bloque de expresión

```
<#
int i = 10;
while (i-- > 0)
    { #>
        <#= i #>
    <# }
#>
```

### <a name="code-block-using-writeline"></a>Bloque de código mediante WriteLine()

```
<#
    int i = 10;
    while (i-- > 0)
    {
        WriteLine((i.ToString()));
    }
#>
```

Puede resultar útil usar uno de estos métodos de utilidad en lugar de un bloque de expresión dentro de un bloque de código largo con estructuras de control anidadas.

Los métodos y tienen dos sobrecargas, una que toma un único parámetro de cadena y otra que toma una cadena de formato compuesto más una matriz de objetos para incluir en la cadena `Write()` `WriteLine()` (como el `Console.WriteLine()` método ). Los dos usos siguientes de `WriteLine()` son funcionalmente equivalentes:

```
<#
    string msg = "Say: {0}, {1}, {2}";
    string s1 = "hello";
    string s2 = "goodbye";
    string s3 = "farewell";

    WriteLine(msg, s1, s2, s3);
    WriteLine("Say: hello, goodbye, farewell");
#>
```

## <a name="indentation-methods"></a>Métodos de sangría

Puede usar métodos de sangría para dar formato a la salida de la plantilla de texto. La clase tiene una propiedad de cadena que muestra la sangría actual en la plantilla de texto y un campo que es una lista de las sangrías que <xref:Microsoft.VisualStudio.TextTemplating.TextTransformation> `CurrentIndent` se han `indentLengths` agregado. Puede agregar una sangría con el método `PushIndent()` y restar una sangría con el `PopIndent()` método . Si desea quitar todas las sangrías, use el `ClearIndent()` método . El siguiente bloque de código muestra el uso de estos métodos:

```
<#
    WriteLine(CurrentIndent + "Hello");
    PushIndent("    ");
    WriteLine(CurrentIndent + "Hello");
    PushIndent("    ");
    WriteLine(CurrentIndent + "Hello");
    ClearIndent();
    WriteLine(CurrentIndent + "Hello");
    PushIndent("    ");
    WriteLine(CurrentIndent + "Hello");
#>
```

Este bloque de código genera la siguiente salida:

```
Hello
        Hello
                Hello
Hello
        Hello
```

## <a name="error-and-warning-methods"></a>Métodos de error y advertencia

Puede usar métodos de utilidad de error y advertencia para agregar mensajes a Visual Studio lista de errores. Por ejemplo, el código siguiente agregará un mensaje de error a la lista de errores.

```
<#
  try
  {
    string str = null;
    Write(str.Length.ToString());
  }
  catch (Exception e)
  {
    Error(e.Message);
  }
#>
```

## <a name="access-to-host-and-service-provider"></a>Acceso al proveedor de servicios y host

La propiedad `this.Host` puede proporcionar acceso a las propiedades expuestas por el host que ejecuta la plantilla. Para usar `this.Host` , debe establecer el atributo en la directiva `hostspecific` `<@template#>` :

`<#@template ... hostspecific="true" #>`

El tipo de `this.Host` depende del tipo de host en el que se ejecuta la plantilla. En una plantilla que se ejecuta en Visual Studio, puede convertir a para obtener acceso a `this.Host` `IServiceProvider` servicios como el IDE. Por ejemplo:

```
EnvDTE.DTE dte = (EnvDTE.DTE) ((IServiceProvider) this.Host)
                       .GetService(typeof(EnvDTE.DTE));
```

## <a name="using-a-different-set-of-utility-methods"></a>Uso de un conjunto diferente de métodos de utilidad

Como parte del proceso de generación de texto, el archivo de plantilla se transforma en una clase, que siempre se denomina `GeneratedTextTransformation` y hereda de <xref:Microsoft.VisualStudio.TextTemplating.TextTransformation> . Si en su lugar desea usar un conjunto diferente de métodos, puede escribir su propia clase y especificarla en la directiva de plantilla. La clase debe heredar de <xref:Microsoft.VisualStudio.TextTemplating.TextTransformation> .

```
<#@ template inherits="MyUtilityClass" #>
```

Use la `assembly` directiva para hacer referencia al ensamblado donde se puede encontrar la clase compilada.
