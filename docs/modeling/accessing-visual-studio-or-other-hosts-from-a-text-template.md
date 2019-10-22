---
title: Tener acceso a Visual Studio u otros hosts desde una plantilla de texto
titleSuffix: ''
ms.date: 11/04/2016
ms.topic: conceptual
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 752b9d9e69eee26f267927f03c4b83c68740100b
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72652360"
---
# <a name="access-visual-studio-or-other-hosts-from-a-text-template"></a>Acceso a Visual Studio u otros hosts desde una plantilla de texto

En una plantilla de texto, puede utilizar los métodos y las propiedades que expone el host que ejecuta la plantilla. Visual Studio es un ejemplo de un host.

> [!NOTE]
> Puede usar métodos y propiedades de host en las plantillas de texto normales, pero no en las plantillas de texto *preprocesadas* .

## <a name="obtain-access-to-the-host"></a>Obtención de acceso al host

Para tener acceso al host, establezca `hostspecific="true"` en la Directiva `template`. Ahora puede usar `this.Host`, que tiene el tipo [ITextTemplatingEngineHost](/previous-versions/visualstudio/visual-studio-2012/bb126505(v=vs.110)). El tipo [ITextTemplatingEngineHost](/previous-versions/visualstudio/visual-studio-2012/bb126505(v=vs.110)) tiene miembros que se pueden usar para resolver nombres de archivo y registrar errores, por ejemplo.

### <a name="resolve-file-names"></a>Resolución de nombres de archivo

Para buscar la ruta de acceso completa de un archivo con respecto a la plantilla de texto, use `this.Host.ResolvePath()`.

```csharp
<#@ template hostspecific="true" language="C#" #>
<#@ output extension=".txt" #>
<#@ import namespace="System.IO" #>
<#
 // Find a path within the same project as the text template:
 string myFile = File.ReadAllText(this.Host.ResolvePath("MyFile.txt"));
#>
Content of myFile is:
<#= myFile #>
```

### <a name="display-error-messages"></a>Mostrar mensajes de error

En este ejemplo se registran mensajes al transformar la plantilla. Si el host es Visual Studio, los errores se agregan a la **lista de errores**.

```csharp
<#@ template hostspecific="true" language="C#" #>
<#@ output extension=".txt" #>
<#@ import namespace="System.CodeDom.Compiler" #>
<#
  string message = "test message";
  this.Host.LogErrors(new CompilerErrorCollection()
    { new CompilerError(
       this.Host.TemplateFile, // Identify the source of the error.
       0, 0, "0",   // Line, column, error ID.
       message) }); // Message displayed in error window.
#>
```

## <a name="use-the-visual-studio-api"></a>Uso de la API de Visual Studio

Si está ejecutando una plantilla de texto en Visual Studio, puede usar `this.Host` para tener acceso a los servicios que proporciona Visual Studio y a los paquetes o extensiones que se cargan.

Establezca HostSpecific = "true" y convierta `this.Host` en <xref:System.IServiceProvider>.

En este ejemplo se obtiene la API de Visual Studio, <xref:EnvDTE.DTE>, como servicio:

```csharp
<#@ template hostspecific="true" language="C#" #>
<#@ output extension=".txt" #>
<#@ assembly name="EnvDTE" #>
<#@ import namespace="EnvDTE" #>
<#
 IServiceProvider serviceProvider = (IServiceProvider)this.Host;
 DTE dte = serviceProvider.GetService(typeof(DTE)) as DTE;
#>
Number of projects in this solution: <#=  dte.Solution.Projects.Count #>
```

## <a name="use-hostspecific-with-template-inheritance"></a>Uso de hostSpecific con la herencia de plantillas

Especifique `hostspecific="trueFromBase"` si también utiliza el atributo `inherits` y si hereda de una plantilla que especifica `hostspecific="true"`. Si no lo hace, es posible que obtenga una advertencia del compilador de que la propiedad `Host` se ha declarado dos veces.