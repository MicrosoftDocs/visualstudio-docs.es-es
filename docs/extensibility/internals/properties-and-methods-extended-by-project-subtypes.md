---
title: "Propiedades y m&#233;todos extendidos subtipos de proyecto | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "subtipos de proyecto, métodos ampliados"
  - "subtipos de proyecto, propiedades extendidas"
ms.assetid: 2b9833bf-8551-4ae1-93db-197ba645c65e
caps.latest.revision: 17
caps.handback.revision: 17
ms.author: "gregvanl"
manager: "ghogen"
---
# Propiedades y m&#233;todos extendidos subtipos de proyecto
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Un subtipo del proyecto tiene mucho eficacia para influir en el comportamiento del proyecto porque se genera como agregador de un proyecto base.  En esta sección se resumen algunas de las características que se pueden extender o modificar por subtipos del proyecto.  
  
## características Gained por la agregación  
 La tabla siguiente se resumen muchos de los métodos que la agregación permite a subtipos de proyecto reemplazar en proyectos base.  
  
|Métodos reemplazados por la agregación|Subtipo del proyecto|  
|--------------------------------------------|--------------------------|  
|de <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>:<br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.SetProperty%2A><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetGuidProperty%2A><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.SetGuidProperty%2A>|Habilita un subtipo del proyecto a<br /><br /> -   Cambie la leyenda y el icono del nodo del proyecto.<br />-   Reemplazar completamente el objeto de `Browse` del proyecto.<br />-   Control si el proyecto puede ser cambiado.<br />-   Criterio de ordenación del Control.<br />-   Contexto de usuario del Control para obtener ayuda dinámica.|  
|de <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject>:<br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject.GetItemContext%2A>|Permite a un subtipo del proyecto para controlar a lo que se proporcionan servicios contextuales a los diseñadores y editores.|  
|de <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>:<br /><br /> <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A><br /><br /> <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.ExecCommand%2A>|Habilita un subtipo del proyecto a<br /><br /> -   Participe en el enrutamiento de comandos para los comandos del proyecto.<br />-   Agregar, quitar, o deshabilite los comandos de ambiente de los comandos del activo del explorador de soluciones.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2>|Permite al subtipo del proyecto para filtrar lo que ve el usuario en el cuadro de diálogo de **Agregar nuevo elemento** .|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGeneratorFactory>|Habilita un subtipo del proyecto a<br /><br /> -   Determine el generador predeterminado especificado una extensión de archivo.<br />-   Asigne un nombre legible de generador a un objeto COM.|  
  
## propiedades utilizadas por el proyecto Subtypes  
 El sistema del proyecto del entorno y de base puede utilizar las propiedades de <xref:Microsoft.VisualStudio.Shell.Interop.__VSSPROPID> y las enumeraciones de <xref:Microsoft.VisualStudio.Shell.Interop.__VSSPROPID2> detalladas en la tabla siguiente para habilitar un subtipo del proyecto para controlar las distintas características del sistema del proyecto.  
  
|propiedad de VSHPROPID|Subtipo del proyecto|  
|----------------------------|--------------------------|  
|`AddItemTemplatesGuid`|Permite que un subtipo de proyecto controla el contenido del cuadro de diálogo de **Agregar elemento** .  Subtipo de proyecto puede proporcionar una nueva especificación de directorios de plantillas, agregar nuevas clases de elementos, quitar elementos existentes, y reorganizar un subconjunto de los elementos del cuadro de diálogo base de **Agregar elemento** del proyecto.|  
|`PropertyPagesCLSIDList`|Permite que un subtipo de proyecto agregue o quite las páginas de propiedades independientes.|  
|`CfgPropertyPagesCLSIDList`|Permite que un subtipo de proyecto agregue o quite las páginas de propiedades dependientes.|  
|`ExtObjectCATID`|Permite que un subtipo de proyecto proporciona una automatización Extender para los objetos del proyecto o elemento de proyecto conociendo el Extender CATID.  Por ejemplo, un subtipo del proyecto puede proporcionar un objeto personalizado de `Project.Extender("<subtype>")` .|  
|`BrowseObjectCATID`|Permite que un subtipo de proyecto proporciona una automatización Extender para el objeto de `Browse` conociendo el Extender CATID.  Por ejemplo, un subtipo del proyecto pueden agregar propiedades adicionales a la colección de <xref:EnvDTE.Project.Properties%2A> .|  
|`CfgBrowseObjectCATID`|Permite que un subtipo de proyecto proporciona una automatización Extender para el objeto de exploración de la configuración del proyecto.  Por ejemplo, un subtipo del proyecto pueden agregar propiedades adicionales a la colección de <xref:EnvDTE.Configuration.Properties%2A> .|  
|`CfgExtObjectCATID`|Permite que un subtipo de proyecto proporciona una automatización Extender para el objeto de configuración.|  
|`DefaultPlatformName`|Permite que un subtipo de proyecto determine el nombre de la plataforma para los objetos configurationes del proyecto.|  
  
 El proyecto base proporciona una implementación predeterminada de las propiedades anteriores.  El proyecto base obtiene estas llamando a `QueryInterface` para <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> en subtipo fuera del proyecto, por lo que el subtipo de proyecto reemplace la implementación de las propiedades.  
  
## Vea también  
 [Diseño de subtipos de proyecto](../../extensibility/internals/project-subtypes-design.md)