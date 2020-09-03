---
title: Contribuir al cuadro de diálogo Agregar nuevo elemento | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "68197022"
---
# <a name="contributing-to-the-add-new-item-dialog-box"></a>Contribución al cuadro de diálogo Agregar nuevo elemento
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Un subtipo de proyecto puede proporcionar un nuevo directorio completo de elementos para el cuadro de diálogo **Agregar nuevo elemento** registrando las plantillas de **Agregar elemento** en la `Projects` subclave del registro.  
  
## <a name="registering-add-new-item-templates"></a>Registrar plantillas agregar nuevo elemento  
 Esta sección se encuentra en **HKEY_LOCAL_MACHINE \software\microsoft\visualstudio\8.0\Projects** en el registro. Las entradas del registro siguientes suponen un [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] proyecto agregado por un subtipo hipotético del proyecto. [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]A continuación se enumeran las entradas del proyecto.  
  
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
  
 La `AddItemTemplates\TemplateDirs` subclave contiene entradas del registro con la ruta de acceso al directorio donde se colocan los elementos disponibles en el cuadro de diálogo **Agregar nuevo elemento** .  
  
 El entorno carga automáticamente todos los `AddItemTemplates` datos en la `Projects` subclave del registro. Esto puede incluir los datos de las implementaciones de proyecto base, así como los datos de tipos de subtipo de proyecto específicos. Cada subtipo de proyecto se identifica mediante un tipo de proyecto `GUID` . El subtipo de proyecto puede especificar que se debe usar un conjunto alternativo de `Add Item` plantillas para una instancia determinada del proyecto, ya que admite la `VSHPROPID_ AddItemTemplatesGuid` enumeración de <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2> en <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> implementación para devolver el valor GUID del subtipo de proyecto. Si `VSHPROPID_AddItemTemplatesGuid` no se especifica la propiedad, se usa el GUID del proyecto base.  
  
 Puede filtrar los elementos en el cuadro de diálogo **Agregar nuevo elemento** implementando la <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg> interfaz en el objeto de agregador de subtipos de proyecto. Por ejemplo, un subtipo de proyecto que implementa un proyecto de base de datos mediante la agregación de un [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] proyecto de, puede filtrar los [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] elementos específicos del cuadro de diálogo **Agregar nuevo elemento** implementando el filtrado y, a su vez, puede agregar elementos específicos del proyecto de base de datos al admitir `VSHPROPID_ AddItemTemplatesGuid` en <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> . Para obtener más información sobre cómo filtrar y agregar elementos al cuadro de diálogo **Agregar nuevo elemento** , vea [Agregar elementos a los cuadros de diálogo Agregar nuevo elemento](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md).  
  
## <a name="see-also"></a>Consulte también  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2>   
 [CATID para los objetos que se usan normalmente para ampliar proyectos](../../extensibility/internals/catids-for-objects-that-are-typically-used-to-extend-projects.md)
