---
title: Tener acceso a Visual Studio u otros hosts desde una plantilla de texto
description: Obtenga información sobre cómo puede usar métodos y propiedades en una plantilla de texto expuesta por el host que ejecuta la plantilla.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 11/04/2016
ms.topic: how-to
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: ce008d0a14cbd75cf8a46599ff67bd9e799ee8ce
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99908883"
---
# <a name="access-visual-studio-or-other-hosts-from-a-text-template"></a>Acceso a Visual Studio u otros hosts desde una plantilla de texto

En una plantilla de texto, puede utilizar los métodos y las propiedades que expone el host que ejecuta la plantilla. Visual Studio es un ejemplo de un host.

> [!NOTE]
> Puede usar métodos y propiedades de host en las plantillas de texto normales, pero no en las plantillas de texto *preprocesadas* .

## <a name="obtain-access-to-the-host"></a>Obtención de acceso al host

Para tener acceso al host, establezca `hostspecific="true"` en la `template` Directiva. Ahora puede usar `this.Host` , que tiene el tipo [ITextTemplatingEngineHost](/previous-versions/visualstudio/visual-studio-2012/bb126505(v=vs.110)). El tipo [ITextTemplatingEngineHost](/previous-versions/visualstudio/visual-studio-2012/bb126505(v=vs.110)) tiene miembros que se pueden usar para resolver nombres de archivo y registrar errores, por ejemplo.

### <a name="resolve-file-names"></a>Resolución de nombres de archivo

Para buscar la ruta de acceso completa de un archivo con respecto a la plantilla de texto, use `this.Host.ResolvePath()` .

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

Si está ejecutando una plantilla de texto en Visual Studio, puede usar `this.Host` para obtener acceso a los servicios proporcionados por Visual Studio y los paquetes o extensiones que se cargan.

Establezca HostSpecific = "true" y conviértalo `this.Host` en <xref:System.IServiceProvider> .

En este ejemplo se obtiene la API de Visual Studio, <xref:EnvDTE.DTE> , como un servicio:

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

Especifique `hostspecific="trueFromBase"` si también utiliza el `inherits` atributo y si hereda de una plantilla que especifica `hostspecific="true"` . Si no lo hace, es posible que obtenga una advertencia del compilador que indica que la propiedad se ha `Host` declarado dos veces.
