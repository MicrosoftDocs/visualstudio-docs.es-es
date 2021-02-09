---
title: Métodos de utilidad de las plantillas de texto
description: Obtenga información sobre los distintos métodos de utilidad de la plantilla de texto que están disponibles cuando se escribe código en Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- text templates, utility methods
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: fcc879a19d3dfcd9e1e8e1bcd79f0488a312e96c
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99924570"
---
# <a name="text-template-utility-methods"></a>Métodos de utilidad de las plantillas de texto

Hay varios métodos que siempre están disponibles cuando se escribe código en una plantilla de texto de Visual Studio. Estos métodos se definen en <xref:Microsoft.VisualStudio.TextTemplating.TextTransformation> .

> [!TIP]
> También puede usar otros métodos y servicios proporcionados por el entorno de host en una plantilla de texto normal (no preprocesada). Por ejemplo, puede resolver rutas de acceso de archivo, registrar errores y obtener servicios proporcionados por Visual Studio y los paquetes cargados. Para obtener más información, vea [obtener acceso a Visual Studio desde una plantilla de texto](/previous-versions/visualstudio/visual-studio-2010/gg604090\(v\=vs.100\)).

## <a name="write-methods"></a>Escribir métodos

Puede usar los `Write()` métodos y `WriteLine()` para anexar texto dentro de un bloque de código estándar, en lugar de usar un bloque de código de expresión. Los dos bloques de código siguientes son funcionalmente equivalentes.

### <a name="code-block-with-an-expression-block"></a>Bloque de código con un bloque de expresiones

```
<#
int i = 10;
while (i-- > 0)
    { #>
        <#= i #>
    <# }
#>
```

### <a name="code-block-using-writeline"></a>Bloque de código mediante WriteLine ()

```
<#
    int i = 10;
    while (i-- > 0)
    {
        WriteLine((i.ToString()));
    }
#>
```

Puede que le resulte útil usar uno de estos métodos de utilidad en lugar de un bloque de expresiones dentro de un bloque de código largo con estructuras de control anidadas.

Los `Write()` `WriteLine()` métodos y tienen dos sobrecargas, una que toma un único parámetro de cadena y otra que toma una cadena de formato compuesto más una matriz de objetos que se van a incluir en la cadena (como el `Console.WriteLine()` método). Los dos usos siguientes de `WriteLine()` son funcionalmente equivalentes:

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

Puede usar métodos de sangría para dar formato a la salida de la plantilla de texto. La <xref:Microsoft.VisualStudio.TextTemplating.TextTransformation> clase tiene una `CurrentIndent` propiedad de cadena que muestra la sangría actual en la plantilla de texto y un `indentLengths` campo que es una lista de las sangrías que se han agregado. Puede Agregar una sangría con el `PushIndent()` método y restar una sangría con el `PopIndent()` método. Si desea quitar todas las sangrías, use el `ClearIndent()` método. En el siguiente bloque de código se muestra el uso de estos métodos:

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

Este bloque de código produce el siguiente resultado:

```
Hello
        Hello
                Hello
Hello
        Hello
```

## <a name="error-and-warning-methods"></a>Métodos de error y de advertencia

Puede usar métodos de utilidad de error y advertencia para agregar mensajes a la Lista de errores de Visual Studio. Por ejemplo, el código siguiente agregará un mensaje de error a la Lista de errores.

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

## <a name="access-to-host-and-service-provider"></a>Acceso al host y al proveedor de servicios

La propiedad `this.Host` puede proporcionar acceso a las propiedades expuestas por el host que ejecuta la plantilla. Para usar `this.Host` , debe establecer `hostspecific` el atributo en la `<@template#>` Directiva:

`<#@template ... hostspecific="true" #>`

El tipo de `this.Host` depende del tipo de host en el que se ejecuta la plantilla. En una plantilla que se ejecuta en Visual Studio, puede convertir `this.Host` a para `IServiceProvider` obtener acceso a servicios como el IDE. Por ejemplo:

```
EnvDTE.DTE dte = (EnvDTE.DTE) ((IServiceProvider) this.Host)
                       .GetService(typeof(EnvDTE.DTE));
```

## <a name="using-a-different-set-of-utility-methods"></a>Usar un conjunto diferente de métodos de utilidad

Como parte del proceso de generación de texto, el archivo de plantilla se transforma en una clase, que siempre se denomina `GeneratedTextTransformation` y hereda de <xref:Microsoft.VisualStudio.TextTemplating.TextTransformation> . Si desea usar un conjunto diferente de métodos en su lugar, puede escribir su propia clase y especificarla en la Directiva de plantilla. La clase debe heredar de <xref:Microsoft.VisualStudio.TextTemplating.TextTransformation> .

```
<#@ template inherits="MyUtilityClass" #>
```

Use la `assembly` Directiva para hacer referencia al ensamblado donde se puede encontrar la clase compilada.
