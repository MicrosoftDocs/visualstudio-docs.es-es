---
title: Agregar directorios al cuadro de diálogo Agregar nuevo elemento | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Add New Item dialog box, extending
ms.assetid: 67ae8af6-3752-49e8-8ce3-007aca5f7982
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: f370d208cb8f7aad88f806983983ccee9f584625
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "68203931"
---
# <a name="adding-directories-to-the-add-new-item-dialog-box"></a>Adición de directorios al cuadro de diálogo Agregar nuevo elemento
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

En el ejemplo de código siguiente se muestra cómo registrar un nuevo conjunto de directorios para el cuadro de diálogo **Agregar nuevo elemento** . Los directorios del cuadro de diálogo **Agregar nuevo elemento** son diferentes para cada proyecto. Por lo tanto, los directorios se registran en la subclave Projects, que se encuentra en \<HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\Projects> :  
  
## <a name="the-registry-script"></a>El script del registro  
  
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
  
 El valor Template_Path especifica la ruta de acceso completa del directorio que contiene las plantillas de proyecto. Estas plantillas pueden ser archivos. vsz o archivos de plantilla prototipos que se van a clonar.  
  
 El valor SortPriority especifica una prioridad de ordenación.  
  
## <a name="adding-items-to-an-existing-project"></a>Agregar elementos a un proyecto existente  
 También puede agregar elementos a un proyecto existente. Por ejemplo, para un [!INCLUDE[csprcs](../../includes/csprcs-md.md)] proyecto, puede agregar elementos a la \<root> carpeta \Archivos de Programa\microsoft Visual Studio \VC # \CSharpProjectItems\LocalProjectItems En este caso `%GUID_Project%` , es el GUID para un proyecto de C# ({FAE04EC0-301F-11D3-BF4B-00C04F79EFBC}).  
  
 También puede extender un proyecto existente mediante la programación de un subtipo de proyecto. Con un subtipo de proyecto, puede extender un proyecto sin escribir un nuevo tipo de proyecto. Para obtener más información sobre los subtipos de proyecto, vea [subtipos de proyecto](../../extensibility/internals/project-subtypes.md).  
  
## <a name="see-also"></a>Consulte también  
 [Registrar plantillas de proyecto y de elemento](../../extensibility/internals/registering-project-and-item-templates.md)   
 [Agregar elementos a los cuadros de diálogo Agregar nuevo elemento](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md)   
 [Adición de directorios al cuadro de diálogo Nuevo proyecto](../../extensibility/internals/adding-directories-to-the-new-project-dialog-box.md)
