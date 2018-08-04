---
title: Agregar directorios a la Agregar cuadro de diálogo nuevo elemento | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Add New Item dialog box, extending
ms.assetid: 67ae8af6-3752-49e8-8ce3-007aca5f7982
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: ba535908b1c5ccb06f0f29490c0b87c377d6b2be
ms.sourcegitcommit: 1c2ed640512ba613b3bbbc9ce348e28be6ca3e45
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/03/2018
ms.locfileid: "39498339"
---
# <a name="add-directories-to-the-add-new-item-dialog-box"></a>Agregar directorios al cuadro de diálogo Agregar nuevo elemento
En el ejemplo de código siguiente se muestra cómo registrar un nuevo conjunto de directorios para la **Agregar nuevo elemento** cuadro de diálogo. Directorios para la **Agregar nuevo elemento** cuadro de diálogo son diferentes para cada proyecto. Por lo tanto, los directorios están registrados en el **proyectos** subclave, se encuentra en **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\Projects**.
  
## <a name="registry-script"></a>Script de registro  
  
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
  
 El `%Template_Path%` valor especifica la ruta de acceso completa del directorio que contiene las plantillas de proyecto. Estas plantillas pueden ser *.vsz* archivos o archivos de plantilla prototípico para clonarse.  
  
 El `SortPriority` valor especifica una prioridad de ordenación.  
  
## <a name="add-items-to-an-existing-project"></a>Agregar elementos a un proyecto existente  
 También puede agregar elementos a un proyecto existente. Por ejemplo, para un [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] proyecto, puede agregar elementos a la  *\<raíz > \Program Files\Microsoft Visual Studio\VC #\CSharpProjectItems\LocalProjectItems* carpeta. En este caso, `%GUID_Project%` es el GUID de un proyecto de C# ({FAE04EC0-301F-11D3-BF4B-00C04F79EFBC}).  
  
 También puede ampliar un proyecto existente mediante programación un subtipo de proyecto. Con un subtipo de proyecto, puede ampliar un proyecto sin necesidad de escribir un nuevo tipo de proyecto. Para obtener más información acerca de subtipos de proyecto, vea [subtipos de proyecto](../../extensibility/internals/project-subtypes.md).  
  
## <a name="see-also"></a>Vea también  
 [Registrar las plantillas de proyecto y elemento](../../extensibility/internals/registering-project-and-item-templates.md)   
 [Agregar elementos al cuadro de diálogo Agregar nuevo elemento](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md)   
 [Agregar directorios al cuadro de diálogo nuevo proyecto](../../extensibility/internals/adding-directories-to-the-new-project-dialog-box.md)