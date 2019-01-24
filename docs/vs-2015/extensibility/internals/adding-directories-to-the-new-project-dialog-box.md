---
title: Agregar directorios al cuadro de diálogo nuevo proyecto | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- New Project dialog box, extending
ms.assetid: 53b328f5-20bb-49a3-bf9e-1818f4fbdf50
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 6a03e61cf3699cd45a7b4b8e6a7e5b7d192ca6de
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/16/2018
ms.locfileid: "51769745"
---
# <a name="adding-directories-to-the-new-project-dialog-box"></a>Adición de directorios al cuadro de diálogo Nuevo proyecto
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Al crear nuevos tipos de proyecto, también puede registrar un nuevo directorio en el **nuevo proyecto** cuadro de diálogo para mostrar para su uso como plantillas. El ejemplo de código siguiente explica cómo registrar un nuevo directorio, también conocido como un nodo. En el ejemplo, se registran plantillas expuestas por VSPackage CLSID_Package. Como resultado, el lado izquierdo de la **nuevo proyecto** cuadro de diálogo ofrece el nodo agregado, con un nombre determinado por el recurso Folder_Label_ResID. Este recurso se carga desde el archivo DLL satélite de VSPackage.  
  
 El **carpeta** valor representa un GUID de una carpeta en la que se muestra el nodo Folder_Label_ResID. En el ejemplo, el GUID que representa el **otros proyectos** carpeta en el **tipos de proyecto** panel de la **nuevo proyecto** cuadro de diálogo. Si el **otros proyectos** valor está ausente, la etiqueta se coloca en el nivel superior.  
  
 El valor TemplatesDir especifica la ruta de acceso completa del directorio que contiene las plantillas de proyecto. Estos archivos pueden ser archivos .vsz o archivos de plantilla típico para clonarse.  
  
 Si especifica TemplatesLocalizedSubDir, debe ser el identificador de recurso de cadena que designa el subdirectorio de TemplatesDir que contiene las plantillas localizadas. Dado que [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] carga el recurso de cadena desde un archivo DLL satélite si tiene uno, cada archivo DLL satélite puede contener un nombre de subdirectorio diferentes. El valor de SortPriority especifica una prioridad de ordenación.  
  
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
 [Registro de plantillas de proyecto y elemento](../../extensibility/internals/registering-project-and-item-templates.md)   
 [Agregar elementos a la Agregar nuevo elemento de los cuadros de diálogo](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md)   
 [Adición directorios al cuadro de diálogo Agregar nuevo elemento](../../extensibility/internals/adding-directories-to-the-add-new-item-dialog-box.md)

