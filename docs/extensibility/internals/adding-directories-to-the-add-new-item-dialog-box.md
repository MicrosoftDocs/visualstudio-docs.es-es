---
title: Agregar directorios al cuadro de diálogo Agregar nuevo elemento | Microsoft Docs
description: Obtenga información sobre cómo agregar directorios al cuadro de diálogo Agregar nuevo elemento Visual Studio mediante un script del Registro para registrar los directorios.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- Add New Item dialog box, extending
ms.assetid: 67ae8af6-3752-49e8-8ce3-007aca5f7982
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: dab135f8e8632755674d7b3ddf5972592f74d315
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/25/2021
ms.locfileid: "112904365"
---
# <a name="add-directories-to-the-add-new-item-dialog-box"></a>Agregar directorios al cuadro de diálogo Agregar nuevo elemento
En el ejemplo de código siguiente se muestra cómo registrar un nuevo conjunto de directorios para el **cuadro de diálogo** Agregar nuevo elemento . Los directorios del **cuadro de diálogo Agregar nuevo** elemento son diferentes para cada proyecto. Por lo tanto, los directorios se registran en la **subclave Proyectos,** que se encuentra **enHKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\Projects**.

## <a name="registry-script"></a>Script del Registro

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

 El `%Template_Path%` valor especifica la ruta de acceso completa del directorio que contiene las plantillas de proyecto. Estas plantillas pueden ser archivos *.vsz* o archivos de plantilla prototípicos que se clonarán.

 El `SortPriority` valor especifica una prioridad de ordenación.

## <a name="add-items-to-an-existing-project"></a>Agregar elementos a un proyecto existente
 También puede agregar elementos a un proyecto existente. Por ejemplo, para un proyecto, puede agregar elementos a la carpeta \Archivos de [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] *\<root> programa\Microsoft Visual Studio\VC#\CSharpProjectItems\LocalProjectItems.* En este caso, es el GUID de un proyecto de `%GUID_Project%` C# ({FAE04EC0-301F-11D3-BF4B-00C04F79EFBC}).

 También puede extender un proyecto existente programando un subtipo de proyecto. Con un subtipo de proyecto, puede extender un proyecto sin escribir un nuevo tipo de proyecto. Para obtener más información sobre los subtipos de proyecto, vea [Subtipos de proyecto](../../extensibility/internals/project-subtypes.md).

## <a name="see-also"></a>Consulta también
- [Registro de plantillas de proyecto y elemento](../../extensibility/internals/registering-project-and-item-templates.md)
- [Agregar elementos al cuadro de diálogo Agregar nuevo elemento](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md)
- [Agregar directorios al cuadro de diálogo Nuevo proyecto](../../extensibility/internals/adding-directories-to-the-new-project-dialog-box.md)
