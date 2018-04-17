---
title: Elemento que contribuye a la Agregar cuadro de diálogo nuevo elemento | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Add New Item dialog box, contributing to
ms.assetid: b2e53175-9372-4d17-8c2b-9264c9e51e9c
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 6d8b35537828f99fe3683e03feac3960d6ca4adc
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="contributing-to-the-add-new-item-dialog-box"></a>Elemento que contribuye a la Agregar cuadro de diálogo nuevo elemento
Un subtipo de proyecto puede proporcionar un nuevo directorio completando de elementos de la **Agregar nuevo elemento** cuadro de diálogo Registrar **Agregar elemento** plantillas en la `Projects` subclave del registro.  
  
## <a name="registering-add-new-item-templates"></a>Registrar plantillas Agregar nuevo elemento  
 En esta sección se encuentra en **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0\Projects** en el registro. Las entradas del registro siguientes se supone un [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] proyecto agregadas por un subtipo de proyecto hipotético. Las entradas para el [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] proyecto se enumeran a continuación.  
  
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
  
 El `AddItemTemplates\TemplateDirs` subclave contiene las entradas del registro con la ruta de acceso al directorio donde están disponibles en los elementos de la **Agregar nuevo elemento** se colocan el cuadro de diálogo.  
  
 El entorno de carga automáticamente todos los `AddItemTemplates` datos bajo la `Projects` subclave del registro. Esto puede incluir los datos para las implementaciones de proyecto base, así como los datos para los tipos de subtipo de proyecto específico. Cada subtipo de proyecto se identifica mediante un tipo de proyecto `GUID`. Puede especificar el subtipo de proyecto que se establezca una alternativa de `Add Item` plantillas se deben utilizar para una instancia de proyecto con tipo concreto por compatibilidad con la `VSHPROPID_ AddItemTemplatesGuid` enumeración de <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2> en <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> implementación para devolver el GUID valor del subtipo de proyecto. Si `VSHPROPID_AddItemTemplatesGuid` no se especifica la propiedad, el proyecto de base que se usa el GUID.  
  
 Puede filtrar los elementos de la **Agregar nuevo elemento** cuadro de diálogo mediante la implementación de la <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg> interfaz en el objeto de agregador del subtipo de proyecto. Por ejemplo, un subtipo de proyecto que implementa un proyecto de base de datos agregando un [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] del proyecto, puede filtrar la [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] elementos específicos de la **Agregar nuevo elemento** cuadro de diálogo mediante la implementación de filtrado y en Active, puede agregar elementos específicos del proyecto de base de datos ya que admite `VSHPROPID_ AddItemTemplatesGuid` en <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A>. Para obtener más información sobre el filtrado y agregar elementos a la **Agregar nuevo elemento** cuadro de diálogo, vea [agregar elementos a los cuadros de diálogo Agregar nuevo elemento](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md).  
  
## <a name="see-also"></a>Vea también  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2>   
 [CATID para los objetos que se utilizan normalmente para ampliar proyectos](../../extensibility/internals/catids-for-objects-that-are-typically-used-to-extend-projects.md)