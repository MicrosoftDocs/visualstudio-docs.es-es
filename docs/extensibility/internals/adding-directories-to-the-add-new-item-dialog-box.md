---
title: "Agregar directorios a la Add New Item Dialog Box | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Agregar cuadro de diálogo nuevo elemento, extensión"
ms.assetid: 67ae8af6-3752-49e8-8ce3-007aca5f7982
caps.latest.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 14
---
# Agregar directorios a la Add New Item Dialog Box
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

En el ejemplo de código siguiente se muestra cómo registrar un nuevo conjunto de directorios para la **Agregar nuevo elemento** cuadro de diálogo. Directorios para la **Agregar nuevo elemento** cuadro de diálogo son diferentes para cada proyecto. Por lo tanto, se registran los directorios bajo la subclave de proyectos, que se encuentra en \< HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\Projects >:  
  
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
  
 El valor de Template_Path especifica la ruta de acceso completa del directorio que contiene las plantillas de proyecto. Estas plantillas pueden ser .vsz (archivos) o archivos de plantilla de prototipo se va a clonar.  
  
 El valor de SortPriority especifica una prioridad de ordenación.  
  
## <a name="adding-items-to-an-existing-project"></a>Agregar elementos a un proyecto existente  
 También puede agregar elementos a un proyecto existente. Por ejemplo, para un [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] proyecto, puede agregar elementos a la \< raíz>\VC#\CSharpProjectItems\LocalProjectItems carpeta de \Program Visual Studio. En este caso el `%GUID_Project%` es el GUID de un proyecto de C# ({FAE04EC0-301F-11D3-BF4B-00C04F79EFBC}).  
  
 También puede ampliar un proyecto existente mediante programación un subtipo de proyecto. Con un subtipo de proyecto, puede ampliar un proyecto sin necesidad de escribir un nuevo tipo de proyecto. Para obtener más información acerca de los subtipos de proyecto, vea [subtipos de proyecto](../../extensibility/internals/project-subtypes.md).  
  
## <a name="see-also"></a>Vea también  
 [Registro de proyecto y plantillas de elementos](../../extensibility/internals/registering-project-and-item-templates.md)   
 [Agregar elementos a la para agregar elementos nuevos cuadros de diálogo](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md)   
 [Agregar directorios en el cuadro de diálogo nuevo proyecto](../../extensibility/internals/adding-directories-to-the-new-project-dialog-box.md)