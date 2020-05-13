---
title: Contribuir al cuadro de diálogo Agregar nuevo elemento ( Add New Item) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Add New Item dialog box, contributing to
ms.assetid: b2e53175-9372-4d17-8c2b-9264c9e51e9c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 83444d9be6ba23392b792a0187bf46dc9920c465
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709275"
---
# <a name="contribute-to-the-add-new-item-dialog-box"></a>Contribuir al cuadro de diálogo Agregar nuevo elemento
Un subtipo de proyecto puede proporcionar un nuevo directorio completo de elementos para el cuadro de diálogo **Agregar nuevo elemento** registrando Agregar plantillas de **elemento** en la subclave del Registro **de proyectos.**

## <a name="register-add-new-item-templates"></a>Registrar Agregar nuevas plantillas de elemento
 Esta sección se encuentra en **HKEY_LOCAL_MACHINE, SOFTWARE, Microsoft, VisualStudio, 8,0, Proyectos,** en el registro. Las entradas de registro [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] siguientes asumen un proyecto agregado por un subtipo de proyecto hipotético. Las entradas para [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] el proyecto se enumeran a continuación.

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

 La subclave **AddItemTemplates-TemplateDirs** contiene entradas del Registro con la ruta de acceso al directorio donde se colocan los elementos disponibles en el cuadro de diálogo **Agregar nuevo elemento.**

 El entorno carga automáticamente todos los datos **AddItemTemplates** en la subclave del Registro **Proyectos.** Estos datos pueden incluir los datos para las implementaciones de proyectos base, así como los datos para tipos de subtipos de proyecto específicos. Cada subtipo de proyecto se identifica mediante un **GUID**de tipo de proyecto. El subtipo de proyecto puede especificar que se debe usar un conjunto alternativo de `VSHPROPID_ AddItemTemplatesGuid` plantillas <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2> <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> Add **Item** para una instancia de proyecto con sabor determinada al admitir la enumeración de in implementation para devolver el valor GUID del subtipo de proyecto. Si `VSHPROPID_AddItemTemplatesGuid` no se especifica la propiedad, se usa el GUID del proyecto base.

 Puede filtrar elementos en el cuadro de <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg> diálogo Agregar nuevo **elemento** implementando la interfaz en el objeto de agregador de subtipo de proyecto. Por ejemplo, un subtipo de proyecto que implementa un [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] proyecto de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] base de datos agregando un proyecto, puede filtrar los elementos específicos del `VSHPROPID_ AddItemTemplatesGuid` <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A>cuadro de diálogo Agregar **nuevo elemento** mediante la implementación de filtrado y, a su vez, puede agregar elementos específicos del proyecto de base de datos mediante la compatibilidad en . Para obtener más información sobre cómo filtrar y agregar elementos al cuadro de diálogo **Agregar nuevo elemento,** vea [Agregar elementos al cuadro](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md)de diálogo Agregar nuevo elemento .

## <a name="see-also"></a>Vea también
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2>
- [CATID para objetos que se utilizan normalmente para extender proyectos](../../extensibility/internals/catids-for-objects-that-are-typically-used-to-extend-projects.md)
