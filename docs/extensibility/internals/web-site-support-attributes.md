---
title: "Atributos de soporte t&#233;cnico del sitio Web | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "proyectos de sitio Web, registro"
ms.assetid: 46d52e2c-ca2a-4bbd-8500-5b0129768aec
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# Atributos de soporte t&#233;cnico del sitio Web
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

el proyecto de sitio Web de[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] se puede extender para proporcionar compatibilidad con los lenguajes de programación web.  El idioma debe registrarse con [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] de modo que las plantillas de proyecto pueden aparecer en el cuadro de diálogo de **Nuevo sitio web** cuando el idioma es seleccionado.  
  
 El ejemplo de IronPython Studio incluye el sitio Web.  Puede resultarle con [Muestras de VSSDK](../../misc/vssdk-samples.md).  Incluye las siguientes clases de atributos para registrar IronPython como lenguaje de codebehind para los nuevos proyectos web.  
  
## WebSiteProjectAttribute  
 Este atributo se coloca en el proyecto del lenguaje.  Agrega el lenguaje a la lista de lenguajes de programación web en **LENGUAJE** mostrado en el cuadro de diálogo de **Nuevo sitio web** .  Por ejemplo, el siguiente agrega IronPython a la lista:  
  
```  
[WebSiteProject("IronPython", "Iron Python")]public class PythonProjectPackage : ProjectPackage  
```  
  
 Este atributo también establece la ruta de acceso de las plantillas para que apunten a las plantillas la carpeta.  Para obtener más información sobre la ubicación de la carpeta de plantillas, vea [Compatibilidad con plantillas de sitio Web](../../extensibility/internals/web-site-support-templates.md).  
  
## WebSiteProjectRelatedFilesAttribute  
 Este atributo se coloca en el proyecto del lenguaje.  Permite el proyecto de sitio Web de anidar un tipo de archivo \(relacionado\) en otro tipo de archivo \(principal\) en **Explorador de soluciones**.  
  
 Por ejemplo:  
  
```  
[WebSiteProjectRelatedFiles("aspx", "py")]public class PythonProjectPackage : ProjectPackage  
```  
  
 especifica que un archivo de codebehind de IronPython está relacionado con un archivo .aspx.  Cuando una nueva página Web .aspx se crea en una solución de sitio Web de IronPython, un nuevo archivo de código fuente de .py se genera y aparece como un nodo secundario de la página .aspx.  
  
## ProvideIntellisenseProviderAttribute  
 Este atributo se coloca en el paquete del proyecto del lenguaje.  Selecciona el proveedor de Intellisense para el idioma.  
  
 Por ejemplo:  
  
```  
[ProvideIntellisenseProvider(typeof(PythonIntellisenseProvider), "IronPythonCodeProvider", "Iron Python", ".py", "IronPython;Python", "IronPython")]public class PythonPackage : Package, IOleComponent  
```  
  
 especifica que una instancia de PythonIntellisenseProvider, que implementa <xref:Microsoft.VisualStudio.Shell.Interop.IVsIntellisenseProject>, debe crearse a petición para proporcionar servicios.  
  
 La implementación de IVsIntellisenseProject controla referencias y llama al compilador de lenguaje cuando una página Web con código se solicita pero no se almacena en memoria caché.  
  
## Vea también  
 [Compatibilidad con sitios Web](../../extensibility/internals/web-site-support.md)