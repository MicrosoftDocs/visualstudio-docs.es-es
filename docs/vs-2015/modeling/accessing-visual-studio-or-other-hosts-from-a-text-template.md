---
title: Obtener acceso a Visual Studio 2015 u otros hosts desde una plantilla de texto | Microsoft Docs
titleSuffix: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
ms.assetid: a68886da-7416-4785-8145-3796bb382cba
caps.latest.revision: 7
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 0e8cedc66d6b52f80239364a3e51b73e93a69aa4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "72655334"
---
# <a name="accessing-visual-studio-or-other-hosts-from-a-text-template"></a>Tener acceso a Visual Studio u otros hosts desde una plantilla de texto
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

En una plantilla de texto, puede usar los métodos y las propiedades que expone el host que ejecuta la plantilla, como [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .

 Esto se aplica a las plantillas de texto normales, no a las plantillas de texto preprocesadas.

## <a name="obtaining-access-to-the-host"></a>Obtención de acceso al host

Establezca `hostspecific="true"` en la `template` Directiva. Esto le permite usar  `this.Host` , que tiene el tipo [ITextTemplatingEngineHost](/previous-versions/visualstudio/visual-studio-2012/bb126505(v=vs.110)). Este tipo tiene miembros que puede usar, por ejemplo, para resolver nombres de archivo y registrar errores.

### <a name="resolving-file-names"></a>Resolver nombres de archivo
 Para buscar la ruta de acceso completa de un archivo con respecto a la plantilla de texto, utilice este. Host. ResolvePath ().

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

### <a name="displaying-error-messages"></a>Mostrar mensajes de error
 En este ejemplo se registran mensajes al transformar la plantilla. Si el host es [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] , se agregan a la ventana de error.

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

## <a name="using-the-visual-studio-api"></a>Uso de la API de Visual Studio
 Si está ejecutando una plantilla de texto en [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] , puede utilizar `this.Host` para obtener acceso a los servicios proporcionados por [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] y cualquier paquete o extensión que se cargue.

 Establezca HostSpecific = "true" y conviértalo `this.Host` en <xref:System.IServiceProvider> .

 Este ejemplo obtiene la [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] API, <xref:EnvDTE.DTE> , como un servicio:

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

## <a name="using-hostspecific-with-template-inheritance"></a>Usar hostSpecific con herencia de plantilla
 Especifique `hostspecific="trueFromBase"` si también utiliza el `inherits` atributo y si hereda de una plantilla que especifica `hostspecific="true"` . Esto evita una advertencia del compilador en el efecto de que la propiedad se ha `Host` declarado dos veces.
