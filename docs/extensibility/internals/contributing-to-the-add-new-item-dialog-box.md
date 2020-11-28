---
title: Contribuir al cuadro de diálogo Agregar nuevo elemento | Microsoft Docs
description: Obtenga información sobre cómo colaborar en el cuadro de diálogo Agregar nuevo elemento de Visual Studio registrando las plantillas de Agregar elemento en la subclave del registro Projects.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 94a13890f0b5e60b1da204b89a01c1cadc6d00c4
ms.sourcegitcommit: 2244665d5a0e22d12dd976417f2a782e68684705
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/28/2020
ms.locfileid: "96304634"
---
# <a name="contribute-to-the-add-new-item-dialog-box"></a>Contribuir al cuadro de diálogo Agregar nuevo elemento
Un subtipo de proyecto puede proporcionar un nuevo directorio completo de elementos para el cuadro de diálogo **Agregar nuevo elemento** registrando las plantillas de **Agregar elemento** en la subclave del registro **Projects** .

## <a name="register-add-new-item-templates"></a>Registro agregar nuevo elemento plantillas
 Esta sección se encuentra en **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0\Projects** en el registro. Las entradas del registro siguientes suponen un [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] proyecto agregado por un subtipo hipotético del proyecto. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]A continuación se enumeran las entradas del proyecto.

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

 La subclave **AddItemTemplates\TemplateDirs** contiene entradas del registro con la ruta de acceso al directorio donde se colocan los elementos disponibles en el cuadro de diálogo **Agregar nuevo elemento** .

 El entorno carga automáticamente todos los datos de **AddItemTemplates** en la subclave del registro **Projects** . Estos datos pueden incluir los datos de las implementaciones de proyecto base, así como los datos de tipos de subtipo de proyecto específicos. Cada subtipo de proyecto se identifica mediante un **GUID** de tipo de proyecto. El subtipo de proyecto puede especificar que se debe usar un conjunto alternativo de plantillas **Add item** para una instancia determinada del proyecto; para ello, se admite la `VSHPROPID_ AddItemTemplatesGuid` enumeración de <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2> in <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> Implementation para devolver el valor GUID del subtipo de proyecto. Si `VSHPROPID_AddItemTemplatesGuid` no se especifica la propiedad, se usa el GUID del proyecto base.

 Puede filtrar los elementos en el cuadro de diálogo **Agregar nuevo elemento** implementando la <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg> interfaz en el objeto de agregador de subtipos de proyecto. Por ejemplo, un subtipo de proyecto que implementa un proyecto de base de datos mediante la agregación de un [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] proyecto, puede filtrar los [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] elementos específicos del cuadro de diálogo **Agregar nuevo elemento** implementando el filtrado y, a su vez, puede agregar elementos específicos del proyecto de base de datos al admitir `VSHPROPID_ AddItemTemplatesGuid` en <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> . Para obtener más información sobre cómo filtrar y agregar elementos al cuadro de diálogo **Agregar nuevo elemento** , vea [Agregar elementos al cuadro de diálogo Agregar nuevo elemento](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md).

## <a name="see-also"></a>Consulte también
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2>
- [CATID para los objetos que se utilizan normalmente para ampliar proyectos](../../extensibility/internals/catids-for-objects-that-are-typically-used-to-extend-projects.md)
