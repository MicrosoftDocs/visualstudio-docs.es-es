---
title: Agregar directorios al cuadro de diálogo nuevo proyecto | Microsoft Docs
description: Obtenga información sobre cómo agregar directorios al cuadro de diálogo nuevo proyecto en Visual Studio, para que pueda crear nuevos tipos de proyecto y mostrarlos como plantillas.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- New Project dialog box, extending
ms.assetid: 53b328f5-20bb-49a3-bf9e-1818f4fbdf50
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: d65b7e4adc6d235bcb925efae1cef20d0aa2c9c2
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99969040"
---
# <a name="add-directories-to-the-new-project-dialog-box"></a>Agregar directorios al cuadro de diálogo nuevo proyecto
Al crear nuevos tipos de proyecto, también puede registrar un nuevo directorio en el cuadro de diálogo **nuevo proyecto** para mostrarlos para su uso como plantillas. En el ejemplo de código siguiente se explica cómo registrar un nuevo directorio, también conocido como nodo. En el ejemplo, se registran las plantillas expuestas por el VSPackage *CLSID_Package*. Como resultado, el lado izquierdo del cuadro de diálogo **nuevo proyecto** ofrece el nodo agregado, con un nombre determinado por el recurso de *Folder_Label_ResID* . Este recurso se carga desde el archivo DLL satélite de VSPackage.

 El valor de **carpeta** representa un GUID de una carpeta en la que se muestra el nodo *Folder_Label_ResID* . En el ejemplo, el GUID representa la carpeta **otros proyectos** en el panel **tipos de proyecto** del cuadro de diálogo **nuevo proyecto** . Si el valor de **otros proyectos** no está presente, la etiqueta se coloca en el nivel superior.

 El `TemplatesDir` valor especifica la ruta de acceso completa del directorio que contiene las plantillas de proyecto. Estos archivos pueden ser archivos *. vsz* o archivos de plantilla típicos que se van a clonar.

 Si especifica `TemplatesLocalizedSubDir` , debe ser el identificador de recurso de una cadena que nombra el subdirectorio de `TemplatesDir` que contiene las plantillas localizadas. Dado [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] que carga el recurso de cadena desde un archivo dll satélite, si tiene uno, cada archivo dll satélite puede contener un nombre de subdirectorio diferente. El `SortPriority` valor especifica una prioridad de ordenación.

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
- [Registrar plantillas de proyecto y elemento](../../extensibility/internals/registering-project-and-item-templates.md)
- [Agregar elementos al cuadro de diálogo Agregar nuevo elemento](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md)
- [Agregar directorios al cuadro de diálogo Agregar nuevo elemento](../../extensibility/internals/adding-directories-to-the-add-new-item-dialog-box.md)
