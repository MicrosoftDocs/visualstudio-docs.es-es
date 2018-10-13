---
title: Acceso a Visual Studio u otros Hosts desde una plantilla de texto | Documentos de Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a68886da-7416-4785-8145-3796bb382cba
caps.latest.revision: 7
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 3eb61ab5d372d02581c68391d125c7def23a402a
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49298485"
---
# <a name="accessing-visual-studio-or-other-hosts-from-a-text-template"></a>Tener acceso a Visual Studio u otros hosts desde una plantilla de texto
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

En una plantilla de texto, puede usar los métodos y propiedades expuestas por el host que ejecuta la plantilla, como [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
 Esto se aplica a las plantillas de texto normal, las plantillas de texto preprocesada no.  
  
## <a name="obtaining-access-to-the-host"></a>Obtener acceso al host  
 Establecer `hostspecific="true"` en el `template` directiva. Esto le permite usar `this.Host`, que tiene el tipo <xref:Microsoft.VisualStudio.TextTemplating.ITextTemplatingEngineHost>. Este tipo tiene miembros que puede usar, por ejemplo, para resolver los nombres de archivo y registrar los errores.  
  
### <a name="resolving-file-names"></a>Resolver nombres de archivo  
 Para buscar la ruta de acceso completa de un archivo con respecto a la plantilla de texto, use esto. Host.ResolvePath().  
  
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
 En este ejemplo registra los mensajes al transformar la plantilla. Si el host es [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], se agregan a la ventana de error.  
  
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
 Si va a ejecutar una plantilla de texto en [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], puede usar `this.Host` acceder a los servicios proporcionados por [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] y ningún paquete o extensiones que se cargan.  
  
 Establecer hostspecific = "true" y convertir `this.Host` a <xref:System.IServiceProvider>.  
  
 Este ejemplo obtiene la [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] API, <xref:EnvDTE.DTE>, como un servicio:  
  
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
  
## <a name="using-hostspecific-with-template-inheritance"></a>Uso de hostSpecific con herencia de plantilla  
 Especificar `hostspecific="trueFromBase"` si también usa el `inherits` atributo, y si se hereda de una plantilla que especifica `hostspecific="true"`. Esto evita una advertencia del compilador para el efecto que la propiedad `Host` se ha declarado dos veces.



