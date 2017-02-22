---
title: "Accessing Visual Studio or other Hosts from a Text Template | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-tfs-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a68886da-7416-4785-8145-3796bb382cba
caps.latest.revision: 5
caps.handback.revision: 5
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
---
# Accessing Visual Studio or other Hosts from a Text Template
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

En una plantilla de texto, puede utilizar los métodos y propiedades expuestas por el host que ejecuta la plantilla, como [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
 Esto se aplica a las plantillas de texto normales, no a las plantillas de texto preprocesadas.  
  
## Obtener acceso al host  
 Establezca `hostspecific="true"` en la directiva `template`.  Esto le permite utilizar `this.Host`, que tiene el tipo de <xref:Microsoft.VisualStudio.TextTemplating.ITextTemplatingEngineHost>.  Este tipo tiene miembros que se pueden utilizar, por ejemplo, para resolver nombres de archivo y registro de errores.  
  
### Resolver nombres de archivo  
 Para encontrar la ruta de acceso completa de un archivo relativo a la plantilla de texto, utilice this.Host.ResolvePath \(\).  
  
```c#  
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
  
### Mostrar mensajes de error  
 Este ejemplo registra los mensajes cuando se transforma la plantilla.  Si el host es [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], se agregan a la ventana de error.  
  
```c#  
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
  
## Usar la API de Visual Studio  
 Si está ejecutando una plantilla de texto en [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], puede utilizar `this.Host` para obtener acceso a los servicios proporcionados por [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] y a cualquier paquete o extensiones que se cargan.  
  
 Establezca hostspecific\="true" y realice la conversión de `this.Host` a <xref:System.IServiceProvider>.  
  
 En este ejemplo se obtiene la API de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], <xref:EnvDTE.DTE>, como un servicio:  
  
```c#  
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
  
## Uso de hostSpecific con herencia de plantilla  
 Especificar `hostspecific="trueFromBase"` si también utiliza la `inherits` atributo, y si se hereda de una plantilla que especifica `hostspecific="true"`.  Esto evita una advertencia del compilador para el efecto que la propiedad `Host` se ha declarado dos veces.