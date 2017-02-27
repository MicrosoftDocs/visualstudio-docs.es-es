---
title: "Agregar directorios en el cuadro de di&#225;logo nuevo proyecto | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Cuadro de diálogo nuevo proyecto, extender"
ms.assetid: 53b328f5-20bb-49a3-bf9e-1818f4fbdf50
caps.latest.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 13
---
# Agregar directorios en el cuadro de di&#225;logo nuevo proyecto
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Cuando cree nuevos tipos de proyecto, también puede registrar un nuevo directorio en el cuadro de diálogo de **Nuevo proyecto** mostrarlos para el uso como plantillas.  el ejemplo de código siguiente explica cómo registrar un nuevo directorio, también conocido como nodo.  en el ejemplo, las plantillas expuestas por VSPackage CLSID\_Package se registran.  Como resultado, el lado izquierdo del cuadro de diálogo de **Nuevo proyecto** proporciona el nodo agregado, con un nombre determinado por el recurso de Folder\_Label\_ResID.  Este recurso se carga el archivo DLL de VSPackage.  
  
 El valor de **carpeta** representa el GUID de una carpeta en la que se muestre el nodo de Folder\_Label\_ResID.  En el ejemplo, GUID representa la carpeta de **otros proyectos** en el panel de **tipos de proyecto** del cuadro de diálogo de **Nuevo proyecto** .  Si el valor de **otros proyectos** no está presente, la etiqueta se coloca en el nivel superior.  
  
 El valor de TemplatesDir especifica la ruta de acceso completa del directorio que contiene las plantillas de proyecto.  Estos archivos pueden ser archivos .vsz o archivos de plantilla típicos que se clonarán.  
  
 Si especifica TemplatesLocalizedSubDir, debe ser el Id. de recurso de cadena que los nombres el subdirectorio de TemplatesDir que contiene plantillas adaptadas.  Dado que [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] carga el recurso de cadena del archivo DLL satélite si tiene uno, cada archivo DLL puede contener otro nombre de subdirectorios. El valor de SortPriority especifica una prioridad de ordenación.  
  
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
  
## Vea también  
 [Registro de proyecto y plantillas de elementos](../../extensibility/internals/registering-project-and-item-templates.md)   
 [Agregar elementos a la para agregar elementos nuevos cuadros de diálogo](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md)   
 [Agregar directorios a la Add New Item Dialog Box](../../extensibility/internals/adding-directories-to-the-add-new-item-dialog-box.md)