---
title: Adición de directorios al cuadro de diálogo Agregar nuevo elemento ( Add New Item Dialog) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Add New Item dialog box, extending
ms.assetid: 67ae8af6-3752-49e8-8ce3-007aca5f7982
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1d4af79f95c87271e9a10eece6c728daa9a81305
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80710251"
---
# <a name="add-directories-to-the-add-new-item-dialog-box"></a>Agregar directorios al cuadro de diálogo Agregar nuevo elemento
En el ejemplo de código siguiente se muestra cómo registrar un nuevo conjunto de directorios para el **Agregar nuevo elemento** cuadro de diálogo. Los directorios del cuadro de diálogo **Agregar nuevo elemento** son diferentes para cada proyecto. Por lo tanto, los directorios se registran en la subclave **Proyectos,** que se encuentra en **HKEY_LOCAL_MACHINE, SOFTWARE, Microsoft, VisualStudio, 8.0Exp, Proyectos**.

## <a name="registry-script"></a>Script de registro

```
NoRemove Projects
{
  NoRemove %GUID_Project%
  {
    NoRemove AddItemTemplates
    {
      NoRemove TemplateDirs
      {
        ForceRemove %CLSID_Package%
        {
      ForceRemove /1 = s '#%Folder_Label_ResID%'
          {
            val TemplatesDir = s '%Template_Path%'
            val SortPriority = d 2000
          }
        }
      }
    }
  }
}
```

 El `%Template_Path%` valor especifica la ruta de acceso completa del directorio que contiene las plantillas de proyecto. Estas plantillas pueden ser archivos *.vsz* o archivos de plantilla prototípicos que se van a clonar.

 El `SortPriority` valor especifica una prioridad de ordenación.

## <a name="add-items-to-an-existing-project"></a>Agregar elementos a un proyecto existente
 También puede agregar elementos a un proyecto existente. Por ejemplo, [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] para un proyecto, puede agregar elementos a la * \<carpeta raíz>, Archivos de programa, Microsoft Visual Studio, VC, CSharpProjectItems, LocalProjectItems.* En este `%GUID_Project%` caso, es el GUID para un proyecto de C- ('FAE04EC0-301F-11D3-BF4B-00C04F79EFBC').

 También puede ampliar un proyecto existente programando un subtipo de proyecto. Con un subtipo de proyecto, puede extender un proyecto sin escribir un nuevo tipo de proyecto. Para obtener más información acerca de los subtipos de proyecto, vea [Subtipos de proyecto](../../extensibility/internals/project-subtypes.md).

## <a name="see-also"></a>Vea también
- [Registrar plantillas de proyectos y elementos](../../extensibility/internals/registering-project-and-item-templates.md)
- [Agregar elementos al cuadro de diálogo Agregar nuevo elemento](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md)
- [Agregar directorios al cuadro de diálogo Nuevo proyecto](../../extensibility/internals/adding-directories-to-the-new-project-dialog-box.md)
