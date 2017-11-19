---
title: "Agregar directorios en el cuadro de diálogo nuevo proyecto | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: New Project dialog box, extending
ms.assetid: 53b328f5-20bb-49a3-bf9e-1818f4fbdf50
caps.latest.revision: "13"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: f24fd3c3a0ffb537c63346ef867a2a43481acfa9
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="adding-directories-to-the-new-project-dialog-box"></a>Agregar directorios en el cuadro de diálogo nuevo proyecto
Al crear nuevos tipos de proyecto, también puede registrar un nuevo directorio en el **nuevo proyecto** cuadro de diálogo para mostrar para su uso como plantillas. En el ejemplo de código siguiente se explica cómo registrar un nuevo directorio, también conocido como un nodo. En el ejemplo, se registran plantillas expuestas por el VSPackage CLSID_Package. Como resultado, el lado izquierdo de la **nuevo proyecto** cuadro de diálogo ofrece el nodo agregado, con un nombre determinado por el recurso Folder_Label_ResID. Este recurso se carga desde el archivo DLL satélite de VSPackage.  
  
 El **carpeta** valor representa un GUID de una carpeta en la que se muestra el nodo Folder_Label_ResID. En el ejemplo, se representa el GUID del **otros proyectos** carpeta en el **tipos de proyecto** panel de la **nuevo proyecto** cuadro de diálogo. Si el **otros proyectos** valor no está presente, la etiqueta se coloca en el nivel superior.  
  
 El valor de TemplatesDir especifica la ruta de acceso completa del directorio que contiene las plantillas de proyecto. Estos archivos pueden ser .vsz (archivos) o archivos de plantilla típica se va a clonar.  
  
 Si especifica TemplatesLocalizedSubDir, debe ser el identificador de recurso de una cadena que designa el subdirectorio de TemplatesDir que contiene plantillas de otros idiomas. Dado que [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] carga el recurso de cadena desde un archivo DLL satélite si tiene uno, cada archivo DLL satélite puede contener un nombre de subdirectorio diferentes. El valor de SortPriority especifica una prioridad de ordenación.  
  
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
 [Registro de proyecto y plantillas de elementos](../../extensibility/internals/registering-project-and-item-templates.md)   
 [Agregar elementos a la para agregar elementos nuevos cuadros de diálogo](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md)   
 [Adición directorios al cuadro de diálogo Agregar nuevo elemento](../../extensibility/internals/adding-directories-to-the-add-new-item-dialog-box.md)