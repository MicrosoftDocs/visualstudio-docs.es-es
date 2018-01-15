---
title: Obtiene acceso a Visual Studio u otros Hosts desde una plantilla de texto | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: fa3f2c0a259afdb09f5565872c9c43c72f38e1c2
ms.sourcegitcommit: f89ed5fc2e5078213e30a6ade4604e34df48181f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/13/2018
---
# <a name="accessing-visual-studio-or-other-hosts-from-a-text-template"></a>Tener acceso a Visual Studio u otros hosts desde una plantilla de texto
En una plantilla de texto, puede usar métodos y propiedades expuestas por el host que ejecuta la plantilla, como [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
 Esto se aplica a las plantillas de texto normal, plantillas de texto preprocesadas no.  
  
## <a name="obtaining-access-to-the-host"></a>Obtener acceso al host  
 Establecer `hostspecific="true"` en el `template` directiva. Esto le permite usar `this.Host`, que tiene el tipo <xref:Microsoft.VisualStudio.TextTemplating.ITextTemplatingEngineHost>. Este tipo tiene miembros que pueden usar, por ejemplo, para resolver nombres de archivo y para registrar los errores.  
  
### <a name="resolving-file-names"></a>Resolver nombres de archivo  
 Para buscar la ruta de acceso completa de un archivo con respecto a la plantilla de texto, utilícelo. Host.ResolvePath().  
  
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
  
### <a name="displaying-error-messages"></a>Mostrar mensajes de Error  
 Este ejemplo registra los mensajes cuando se transforma la plantilla. Si el host es [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], se agregan a la ventana de error.  
  
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
  
## <a name="using-the-visual-studio-api"></a>Con la API de Visual Studio  
 Si está ejecutando una plantilla de texto en [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], puede usar `this.Host` acceder a los servicios proporcionados por [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] y los paquetes o extensiones que se cargan.  
  
 Establecer hostspecific = "true" y convertir `this.Host` a <xref:System.IServiceProvider>.  
  
 Este ejemplo obtiene la [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] API, <xref:EnvDTE.DTE>, como un servicio:  
  
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
 Especifique `hostspecific="trueFromBase"` si también utiliza el `inherits` atributo, y si se hereda de una plantilla que especifica `hostspecific="true"`. Esto evita una advertencia del compilador en el efecto que la propiedad `Host` se ha declarado dos veces.