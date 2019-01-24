---
title: Agregar directorios a la Agregar cuadro de diálogo nuevo elemento | Microsoft Docs
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
- Add New Item dialog box, extending
ms.assetid: 67ae8af6-3752-49e8-8ce3-007aca5f7982
caps.latest.revision: 15
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: d094f9911b80f3cff3e648da2593c62e0429fb54
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/16/2018
ms.locfileid: "51751499"
---
# <a name="adding-directories-to-the-add-new-item-dialog-box"></a>Adición de directorios al cuadro de diálogo Agregar nuevo elemento
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

En el ejemplo de código siguiente se muestra cómo registrar un nuevo conjunto de directorios para la **Agregar nuevo elemento** cuadro de diálogo. Directorios para la **Agregar nuevo elemento** cuadro de diálogo son diferentes para cada proyecto. Por lo tanto, se registran los directorios bajo la subclave de proyectos, se encuentra en \<HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\Projects >:  
  
## <a name="the-registry-script"></a>El Script de registro  
  
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
  
 El valor Template_Path especifica la ruta de acceso completa del directorio que contiene las plantillas de proyecto. Estas plantillas pueden ser archivos .vsz o archivos de plantilla de prototipo para clonarse.  
  
 El valor de SortPriority especifica una prioridad de ordenación.  
  
## <a name="adding-items-to-an-existing-project"></a>Agregar elementos a un proyecto existente  
 También puede agregar elementos a un proyecto existente. Por ejemplo, para un [!INCLUDE[csprcs](../../includes/csprcs-md.md)] proyecto, puede agregar elementos a la \<raíz > carpeta \Archivos de Visual Studio \VC#\CSharpProjectItems\LocalProjectItems \Program Files\Microsoft. En este caso el `%GUID_Project%` es el GUID de un proyecto de C# ({FAE04EC0-301F-11D3-BF4B-00C04F79EFBC}).  
  
 También puede ampliar un proyecto existente mediante programación un subtipo de proyecto. Con un subtipo de proyecto, puede ampliar un proyecto sin necesidad de escribir un nuevo tipo de proyecto. Para obtener más información acerca de subtipos de proyecto, vea [subtipos de proyecto](../../extensibility/internals/project-subtypes.md).  
  
## <a name="see-also"></a>Vea también  
 [Registro de plantillas de proyecto y elemento](../../extensibility/internals/registering-project-and-item-templates.md)   
 [Agregar elementos a la Agregar nuevo elemento de los cuadros de diálogo](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md)   
 [Adición de directorios al cuadro de diálogo Nuevo proyecto](../../extensibility/internals/adding-directories-to-the-new-project-dialog-box.md)

