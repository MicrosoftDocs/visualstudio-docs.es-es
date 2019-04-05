---
title: Contribuir a la Agregar cuadro de diálogo nuevo elemento | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Add New Item dialog box, contributing to
ms.assetid: b2e53175-9372-4d17-8c2b-9264c9e51e9c
caps.latest.revision: 19
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: d288f2d007fd0f923021847179326069959d3698
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2019
ms.locfileid: "58988133"
---
# <a name="contributing-to-the-add-new-item-dialog-box"></a>Contribución al cuadro de diálogo Agregar nuevo elemento
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Un subtipo de proyecto puede proporcionar un nuevo directorio completando de elementos de la **Agregar nuevo elemento** cuadro de diálogo Registrar **Agregar elemento** plantillas bajo el `Projects` subclave del registro.  
  
## <a name="registering-add-new-item-templates"></a>Registrar plantillas Agregar nuevo elemento  
 En esta sección se encuentra en **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0\Projects** en el registro. Las entradas del registro siguiente suponen un [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] proyecto agregadas por un subtipo de proyecto hipotético. Las entradas para el [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] proyecto se enumeran a continuación.  
  
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
  
 El `AddItemTemplates\TemplateDirs` subclave contiene las entradas del registro con la ruta de acceso al directorio donde ponen a disposición de los elementos del **Agregar nuevo elemento** se colocan el cuadro de diálogo.  
  
 El entorno carga automáticamente todas las `AddItemTemplates` datos bajo la `Projects` subclave del registro. Esto puede incluir los datos para las implementaciones de proyecto de base, así como los datos para los tipos de subtipo de proyecto específico. Cada subtipo de proyecto se identifica mediante un tipo de proyecto `GUID`. Puede especificar el subtipo de proyecto que alternativa del conjunto de `Add Item` plantillas se deben utilizar para una instancia determinada de proyecto característico al admitir el `VSHPROPID_ AddItemTemplatesGuid` enumeración desde <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2> en <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> implementación para devolver el GUID valor del subtipo de proyecto. Si `VSHPROPID_AddItemTemplatesGuid` propiedad no se especifica, el proyecto de base se usa el GUID.  
  
 Puede filtrar los elementos de la **Agregar nuevo elemento** cuadro de diálogo mediante la implementación de la <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg> interfaz en el objeto de agregador del subtipo de proyecto. Por ejemplo, un subtipo de proyecto que implementa un proyecto de base de datos agregando un [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] project, puede filtrar el [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] los elementos específicos de la **Agregar nuevo elemento** cuadro de diálogo mediante la implementación de filtrado y, en activar, puede agregar elementos específicos del proyecto de base de datos permitiendo `VSHPROPID_ AddItemTemplatesGuid` en <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A>. Para obtener más información sobre filtrado y agregar elementos a la **Agregar nuevo elemento** cuadro de diálogo, vea [agregar elementos a los cuadros de diálogo Agregar nuevo elemento](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md).  
  
## <a name="see-also"></a>Vea también  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2>   
 [CATID para los objetos que se utilizan normalmente para ampliar proyectos](../../extensibility/internals/catids-for-objects-that-are-typically-used-to-extend-projects.md)
