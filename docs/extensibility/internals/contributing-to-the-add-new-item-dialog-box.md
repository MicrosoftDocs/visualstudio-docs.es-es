---
title: "Contribuir a la Add New Item Dialog Box | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Cuadro de diálogo nuevo elemento, que contribuyen a agregar"
ms.assetid: b2e53175-9372-4d17-8c2b-9264c9e51e9c
caps.latest.revision: 18
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 18
---
# Contribuir a la Add New Item Dialog Box
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Un subtipo del proyecto puede proporcionar un nuevo directorio completo de los elementos del cuadro de diálogo de **Agregar nuevo elemento** registrar las plantillas de **Agregar elemento** bajo la subclave del Registro de `Projects` .  
  
## El registro agrega plantillas de elementos  
 Esta sección está situado bajo **HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\VisualStudio\\8.0\\Projects** en el registro.  Las entradas del Registro siguiente se supone un proyecto de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] agregado por un subtipo hipotético del proyecto.  Las entradas del proyecto de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] se enumeran.  
  
```  
[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0\Projects\{F184B08F-C81C-45F6-A57F-5ABD9991F28F}]  
@="#2143"  
"DefaultProjectExtension"="vbproj"  
"PossibleProjectExtensions"="vbproj;vbp"  
"ProjectTemplatesDir"="visualStudioInstallPath\\Vb\\.\\VBProjects"  
  
[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0\Projects\{F184B08F-C81C-45F6-A57F-5ABD9991F28F}\AddItemTemplates\TemplateDirs\{12345678-1234-1234-1122334455667788}\/1]  
@="#100"  
"TemplatesDir"="projectSubTypeTemplatesDir\\VBProjectItems"  
```  
  
 La subclave de `AddItemTemplates\TemplateDirs` contiene entradas de Registro con la ruta de acceso al directorio donde los elementos disponibles en el cuadro de diálogo de **Agregar nuevo elemento** se colocan.  
  
 El entorno carga automáticamente todos los datos de `AddItemTemplates` bajo la subclave del Registro de `Projects` .  Esto puede incluir los datos de las ejecuciones de proyecto bases así como datos para tipos de subtipo de un proyecto específico.  Cada subtipo de proyecto se identifica mediante un tipo de proyecto `GUID`.  Subtipo de proyecto puede especificar que un conjunto alternas de plantillas de `Add Item` se debe utilizar para una instancia condimentada detalle de proyecto admitiendo a la enumeración de `VSHPROPID_ AddItemTemplatesGuid` de <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2> en la implementación de <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> que devuelve el valor de GUID del subtipo del proyecto.  si la propiedad de `VSHPROPID_AddItemTemplatesGuid` no se especifica, se utiliza el proyecto base GUID.  
  
 Puede filtrar los elementos del cuadro de diálogo de **Agregar nuevo elemento** implementando la interfaz de <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg> en el objeto del agregador de subtipo del proyecto.  Por ejemplo, un subtipo del proyecto que implementa un proyecto de base de datos agregando un proyecto de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] , puede filtrar los elementos específicos de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] del cuadro de diálogo de **Agregar nuevo elemento** implementando el filtrado y, a su vez, puede agregar elementos específicos del proyecto de base de datos a `VSHPROPID_ AddItemTemplatesGuid` en <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A>.  Para obtener más información sobre el filtrado y cómo agregar elementos al cuadro de diálogo de **Agregar nuevo elemento** , vea [Agregar elementos a la para agregar elementos nuevos cuadros de diálogo](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md).  
  
## Vea también  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2>   
 [CATID para los objetos que se utilizan normalmente para extender proyectos](../../extensibility/internals/catids-for-objects-that-are-typically-used-to-extend-projects.md)