---
title: Tener acceso a Visual Studio u otros hosts desde una plantilla de texto
description: Obtenga información sobre cómo puede usar métodos y propiedades en una plantilla de texto expuesta por el host que ejecuta la plantilla.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 11/04/2016
ms.topic: how-to
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 3cde4b2afe6d09c3958bbabe7a5669a13f8de8f2
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/19/2021
ms.locfileid: "112389129"
---
# <a name="access-visual-studio-or-other-hosts-from-a-text-template"></a>Acceso Visual Studio u otros hosts desde una plantilla de texto

En una plantilla de texto, puede usar métodos y propiedades expuestos por el host que ejecuta la plantilla. Visual Studio es un ejemplo de un host.

> [!NOTE]
> Puede usar métodos host y propiedades en plantillas de texto normales, pero no en plantillas *de texto preprocesado.*

## <a name="obtain-access-to-the-host"></a>Obtener acceso al host

Para acceder al host, establezca `hostspecific="true"` en la `template` directiva . Ahora puede usar `this.Host` , que tiene el tipo [ITextTemplatingEngineHost](/previous-versions/visualstudio/visual-studio-2012/bb126505(v=vs.110)). El [tipo ITextTemplatingEngineHost tiene](/previous-versions/visualstudio/visual-studio-2012/bb126505(v=vs.110)) miembros que puede usar para resolver errores de registro y nombres de archivo, por ejemplo.

### <a name="resolve-file-names"></a>Resolver nombres de archivo

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

Este ejemplo registra mensajes al transformar la plantilla. Si el host está Visual Studio, los errores se agregan a la **lista de errores**.

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

## <a name="use-the-visual-studio-api"></a>Uso de Visual Studio API

Si ejecuta una plantilla de texto en Visual Studio, puede usar para acceder a los servicios proporcionados por Visual Studio y los paquetes o extensiones que `this.Host` se cargan.

Establezca hostspecific="true" y `this.Host` consítelo en <xref:System.IServiceProvider> .

En este ejemplo se obtiene Visual Studio API, <xref:EnvDTE.DTE> , como servicio:

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

Especifique `hostspecific="trueFromBase"` si también usa el atributo y si `inherits` hereda de una plantilla que especifica `hostspecific="true"` . Si no lo hace, es posible que reciba una advertencia del compilador de que la propiedad `Host` se ha declarado dos veces.
