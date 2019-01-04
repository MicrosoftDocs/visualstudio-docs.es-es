---
title: Contribuir a la Agregar cuadro de diálogo nuevo elemento | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Add New Item dialog box, contributing to
ms.assetid: b2e53175-9372-4d17-8c2b-9264c9e51e9c
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 0b9e86b002c212f63076c065d7aca3b7649513b1
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53865666"
---
# <a name="contribute-to-the-add-new-item-dialog-box"></a>Contribuir al cuadro de diálogo Agregar nuevo elemento
Un subtipo de proyecto puede proporcionar un nuevo directorio completando de elementos de la **Agregar nuevo elemento** cuadro de diálogo Registrar **Agregar elemento** plantillas bajo el **proyectos** subclave del registro.  
  
## <a name="register-add-new-item-templates"></a>Registrar las plantillas Agregar nuevo elemento  
 En esta sección se encuentra en **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0\Projects** en el registro. Las entradas del registro siguiente suponen un [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] proyecto agregadas por un subtipo de proyecto hipotético. Las entradas para el [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] proyecto se enumeran a continuación.  
  
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
  
 El **AddItemTemplates\TemplateDirs** subclave contiene las entradas del registro con la ruta de acceso al directorio donde ponen a disposición de los elementos del **Agregar nuevo elemento** se colocan el cuadro de diálogo.  
  
 El entorno carga automáticamente todas las **AddItemTemplates** datos bajo la **proyectos** subclave del registro. Estos datos pueden incluir los datos para las implementaciones de proyecto de base, así como los datos para los tipos de subtipo de proyecto específico. Cada subtipo de proyecto se identifica mediante un tipo de proyecto **GUID**. Puede especificar el subtipo de proyecto que alternativa del conjunto de **Agregar elemento** plantillas se deben utilizar para una instancia determinada de proyecto característico al admitir el `VSHPROPID_ AddItemTemplatesGuid` enumeración desde <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2> en <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> implementación para devolver el valor GUID del subtipo de proyecto. Si el `VSHPROPID_AddItemTemplatesGuid` propiedad no se especifica, el proyecto de base se usa el GUID.  
  
 Puede filtrar los elementos de la **Agregar nuevo elemento** cuadro de diálogo mediante la implementación de la <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg> interfaz en el objeto de agregador del subtipo de proyecto. Por ejemplo, un subtipo de proyecto que implementa un proyecto de base de datos agregando un [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] project, puede filtrar el [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] los elementos específicos de la **Agregar nuevo elemento** cuadro de diálogo mediante la implementación de filtrado y, en activar, puede agregar los elementos específicos del proyecto de base de datos permitiendo `VSHPROPID_ AddItemTemplatesGuid` en <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A>. Para obtener más información sobre filtrado y agregar elementos a la **Agregar nuevo elemento** cuadro de diálogo, vea [agregar elementos al cuadro de diálogo Agregar nuevo elemento](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md).  
  
## <a name="see-also"></a>Vea también  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2>   
 [CATID para los objetos que se suelen usar para ampliar proyectos](../../extensibility/internals/catids-for-objects-that-are-typically-used-to-extend-projects.md)