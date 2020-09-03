---
title: Agregar directorios al cuadro de diálogo nuevo proyecto | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- New Project dialog box, extending
ms.assetid: 53b328f5-20bb-49a3-bf9e-1818f4fbdf50
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: a8a9eeca4dc455c4f16e3551541454483138a993
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "68203879"
---
# <a name="adding-directories-to-the-new-project-dialog-box"></a>Adición de directorios al cuadro de diálogo Nuevo proyecto
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Al crear nuevos tipos de proyecto, también puede registrar un nuevo directorio en el cuadro de diálogo **nuevo proyecto** para mostrarlos para su uso como plantillas. En el ejemplo de código siguiente se explica cómo registrar un nuevo directorio, también conocido como nodo. En el ejemplo, se registran las plantillas expuestas por VSPackage CLSID_Package. Como resultado, el lado izquierdo del cuadro de diálogo **nuevo proyecto** ofrece el nodo agregado, con un nombre determinado por el recurso de Folder_Label_ResID. Este recurso se carga desde el archivo DLL satélite de VSPackage.  
  
 El valor de **carpeta** representa un GUID de una carpeta en la que se muestra el nodo Folder_Label_ResID. En el ejemplo, el GUID representa la carpeta **otros proyectos** en el panel **tipos de proyecto** del cuadro de diálogo **nuevo proyecto** . Si el valor de **otros proyectos** no está presente, la etiqueta se coloca en el nivel superior.  
  
 El valor TemplatesDir especifica la ruta de acceso completa del directorio que contiene las plantillas de proyecto. Estos archivos pueden ser archivos. vsz o archivos de plantilla típicos que se van a clonar.  
  
 Si especifica TemplatesLocalizedSubDir, debe ser el identificador de recurso de una cadena que nombra el subdirectorio de TemplatesDir que contiene las plantillas localizadas. Dado [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] que carga el recurso de cadena desde un archivo dll satélite, si tiene uno, cada archivo dll satélite puede contener un nombre de subdirectorio diferente. El valor SortPriority especifica una prioridad de ordenación.  
  
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
  
## <a name="see-also"></a>Consulte también  
 [Registrar plantillas de proyecto y de elemento](../../extensibility/internals/registering-project-and-item-templates.md)   
 [Agregar elementos a los cuadros de diálogo Agregar nuevo elemento](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md)   
 [Adición de directorios al cuadro de diálogo Agregar nuevo elemento](../../extensibility/internals/adding-directories-to-the-add-new-item-dialog-box.md)
