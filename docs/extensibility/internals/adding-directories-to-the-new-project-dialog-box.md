---
title: Agregar directorios al cuadro de diálogo nuevo proyecto | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- New Project dialog box, extending
ms.assetid: 53b328f5-20bb-49a3-bf9e-1818f4fbdf50
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9d8e68413795b7004542ee312dcb27492e55e7f0
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/21/2019
ms.locfileid: "56626198"
---
# <a name="add-directories-to-the-new-project-dialog-box"></a>Agregar directorios al cuadro de diálogo nuevo proyecto
Al crear nuevos tipos de proyecto, también puede registrar un nuevo directorio en el **nuevo proyecto** cuadro de diálogo para mostrar para su uso como plantillas. El ejemplo de código siguiente explica cómo registrar un nuevo directorio, también conocido como un nodo. En el ejemplo, plantillas expuestos por el VSPackage, *CLSID_Package*, están registrados. Como resultado, el lado izquierdo de la **nuevo proyecto** cuadro de diálogo ofrece el nodo agregado, con un nombre determinado por la *Folder_Label_ResID* recursos. Este recurso se carga desde el archivo DLL satélite de VSPackage.

 El **carpeta** valor representa un GUID de una carpeta en la que el *Folder_Label_ResID* nodo se muestra. En el ejemplo, el GUID que representa el **otros proyectos** carpeta en el **tipos de proyecto** panel de la **nuevo proyecto** cuadro de diálogo. Si el **otros proyectos** valor está ausente, la etiqueta se coloca en el nivel superior.

 El `TemplatesDir` valor especifica la ruta de acceso completa del directorio que contiene las plantillas de proyecto. Estos archivos pueden ser *.vsz* archivos o archivos de plantilla típico para clonarse.

 Si especifica `TemplatesLocalizedSubDir`, debe ser el identificador de recurso de cadena que designa el subdirectorio de `TemplatesDir` que contiene las plantillas localizadas. Dado que [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] carga el recurso de cadena desde un archivo DLL satélite si tiene uno, cada archivo DLL satélite puede contener un nombre de subdirectorio diferentes. El `SortPriority` valor especifica una prioridad de ordenación.

```
NoRemove NewProjectTemplates
{
    NoRemove TemplateDirs
  {
    ForceRemove %CLSID_Package%
    {
      ForceRemove /1 = s '#%Folder_Label_ResID%'
      {
        val Folder = s '{DCF2A94A-45B0-11D1-ADBF-00C04FB6BE4C}'
        val TemplatesDir = s '%Template_Path%'
        val TemplatesLocalizedSubDir = s '#100'
        val SortPriority = d 1000
      }
    }
  }
}
```

## <a name="see-also"></a>Vea también
- [Registrar las plantillas de proyecto y elemento](../../extensibility/internals/registering-project-and-item-templates.md)
- [Agregar elementos al cuadro de diálogo Agregar nuevo elemento](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md)
- [Agregar directorios al cuadro de diálogo Agregar nuevo elemento](../../extensibility/internals/adding-directories-to-the-add-new-item-dialog-box.md)