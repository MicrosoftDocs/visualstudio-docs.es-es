---
title: Tener acceso a Visual Studio u otros hosts desde una plantilla de texto
titleSuffix: ''
ms.date: 11/04/2016
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 26845b3878a89ea52a3f77f9a0a8d23363877edd
ms.sourcegitcommit: 2da366ba9ad124366f6502927ecc720985fc2f9e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/09/2019
ms.locfileid: "68870686"
---
# <a name="access-visual-studio-or-other-hosts-from-a-text-template"></a>Acceso a Visual Studio u otros hosts desde una plantilla de texto

En una plantilla de texto, puede usar los métodos y propiedades expuestos por el host que ejecuta la plantilla. Visual Studio es un ejemplo de un host.

> [!NOTE]
> Puede usar propiedades y métodos de host en las plantillas de texto normal, pero no en *preprocesada* plantillas de texto.

## <a name="obtain-access-to-the-host"></a>Obtener acceso al host

Para tener acceso al host, establezca `hostspecific="true"` en el `template` directiva. Ahora puede usar `this.Host`, que tiene el tipo [ITextTemplatingEngineHost](/previous-versions/visualstudio/visual-studio-2012/bb126505(v=vs.110)). El tipo [ITextTemplatingEngineHost](/previous-versions/visualstudio/visual-studio-2012/bb126505(v=vs.110)) tiene miembros que se pueden usar para resolver nombres de archivo y registrar errores, por ejemplo.

### <a name="resolve-file-names"></a>Resolver nombres de archivo

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

### <a name="display-error-messages"></a>Mostrar mensajes de Error

En este ejemplo registra los mensajes al transformar la plantilla. Si el host está Visual Studio, los errores se agregan a la **lista de errores**.

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

## <a name="use-the-visual-studio-api"></a>Usar la API de Visual Studio

Si está ejecutando una plantilla de texto en Visual Studio, puede usar `this.Host` acceder a los servicios proporcionados por Visual Studio y los paquetes o las extensiones que se cargan.

Establecer hostspecific = "true" y convertir `this.Host` a <xref:System.IServiceProvider>.

En este ejemplo obtiene la API de Visual Studio, <xref:EnvDTE.DTE>, como un servicio:

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

## <a name="use-hostspecific-with-template-inheritance"></a>Usar hostSpecific con herencia de plantilla

Especificar `hostspecific="trueFromBase"` si también usa el `inherits` atributo, y si se hereda de una plantilla que especifica `hostspecific="true"`. Si no lo hace, podría obtener un compilador de advertencia que indica que la propiedad `Host` se ha declarado dos veces.