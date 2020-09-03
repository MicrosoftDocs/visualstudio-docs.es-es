---
title: Agregar directorios al cuadro de diálogo Agregar nuevo elemento | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "80710251"
---
# <a name="add-directories-to-the-add-new-item-dialog-box"></a>Agregar directorios al cuadro de diálogo Agregar nuevo elemento
En el ejemplo de código siguiente se muestra cómo registrar un nuevo conjunto de directorios para el cuadro de diálogo **Agregar nuevo elemento** . Los directorios del cuadro de diálogo **Agregar nuevo elemento** son diferentes para cada proyecto. Por lo tanto, los directorios se registran en la subclave **Projects** , que se encuentra en **HKEY_LOCAL_MACHINE \software\microsoft\visualstudio\8.0exp\projects**.

## <a name="registry-script"></a>Script del registro

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

 El `%Template_Path%` valor especifica la ruta de acceso completa del directorio que contiene las plantillas de proyecto. Estas plantillas pueden ser archivos *. vsz* o archivos de plantilla prototipos que se van a clonar.

 El `SortPriority` valor especifica una prioridad de ordenación.

## <a name="add-items-to-an-existing-project"></a>Agregar elementos a un proyecto existente
 También puede agregar elementos a un proyecto existente. Por ejemplo, para un [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] proyecto, puede agregar elementos a la carpeta * \<root> \Archivos de programa\Microsoft Visual Studio\VC # \CSharpProjectItems\LocalProjectItems* En este caso, `%GUID_Project%` es el GUID para un proyecto de C# ({FAE04EC0-301F-11D3-BF4B-00C04F79EFBC}).

 También puede extender un proyecto existente mediante la programación de un subtipo de proyecto. Con un subtipo de proyecto, puede extender un proyecto sin escribir un nuevo tipo de proyecto. Para obtener más información sobre los subtipos de proyecto, vea [subtipos de proyecto](../../extensibility/internals/project-subtypes.md).

## <a name="see-also"></a>Vea también
- [Registrar plantillas de proyecto y elemento](../../extensibility/internals/registering-project-and-item-templates.md)
- [Agregar elementos al cuadro de diálogo Agregar nuevo elemento](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md)
- [Agregar directorios al cuadro de diálogo nuevo proyecto](../../extensibility/internals/adding-directories-to-the-new-project-dialog-box.md)
