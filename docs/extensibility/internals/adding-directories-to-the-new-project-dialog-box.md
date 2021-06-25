---
title: Agregar directorios al cuadro de diálogo Nuevo proyecto | Microsoft Docs
description: Obtenga información sobre cómo agregar directorios al cuadro de diálogo Nuevo proyecto de Visual Studio, para que pueda crear nuevos tipos de proyecto y mostrarlos para usarlos como plantillas.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- New Project dialog box, extending
ms.assetid: 53b328f5-20bb-49a3-bf9e-1818f4fbdf50
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 44554c8bd7b758f1bf191d1a4bef9ba07941191d
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/25/2021
ms.locfileid: "112901843"
---
# <a name="add-directories-to-the-new-project-dialog-box"></a>Agregar directorios al cuadro de diálogo Nuevo proyecto
Al crear nuevos tipos de proyecto, también puede  registrar un nuevo directorio en el cuadro de diálogo Nuevo proyecto para mostrarlos para usarlos como plantillas. En el ejemplo de código siguiente se explica cómo registrar un nuevo directorio, también conocido como nodo. En el ejemplo, se registran las plantillas expuestas por el *VSPackage, CLSID_Package*, . Como resultado, el lado  izquierdo del cuadro de diálogo Nuevo proyecto ofrece el nodo agregado, con un nombre determinado por el *Folder_Label_ResID* recurso. Este recurso se carga desde la DLL satélite de VSPackage.

 El **valor** Carpeta representa un GUID de una carpeta en la que *se muestra Folder_Label_ResID* nodo. En el ejemplo, el GUID representa la **carpeta Otros proyectos** en el panel Tipos de **proyecto** del cuadro **de diálogo** Nuevo proyecto . Si el **valor Otros proyectos** no está presente, la etiqueta se coloca en el nivel superior.

 El `TemplatesDir` valor especifica la ruta de acceso completa del directorio que contiene las plantillas de proyecto. Estos archivos pueden ser archivos *.vsz* o archivos de plantilla típicos que se clonarán.

 Si especifica , debe ser el identificador de recurso de una cadena que nombra el `TemplatesLocalizedSubDir` subdirectorio de `TemplatesDir` que contiene plantillas localizadas. Dado que carga el recurso de cadena desde un archivo DLL satélite si tiene uno, cada [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] archivo DLL satélite puede contener un nombre de subdirectorio diferente. El `SortPriority` valor especifica una prioridad de ordenación.

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

## <a name="see-also"></a>Consulta también
- [Registro de plantillas de proyecto y elemento](../../extensibility/internals/registering-project-and-item-templates.md)
- [Agregar elementos al cuadro de diálogo Agregar nuevo elemento](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md)
- [Agregar directorios al cuadro de diálogo Agregar nuevo elemento](../../extensibility/internals/adding-directories-to-the-add-new-item-dialog-box.md)
