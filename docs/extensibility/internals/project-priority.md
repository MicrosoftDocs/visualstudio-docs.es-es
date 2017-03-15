---
title: "Prioridad del proyecto | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "proyectos [Visual Studio SDK], abrir elementos"
ms.assetid: 9f707592-2fb6-4f75-9269-f6d4700a998e
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# Prioridad del proyecto
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Un elemento de proyecto suele ser un miembro de un solo proyecto de la solución.  Por consiguiente, el IDE puede determinar con facilidad se utiliza qué proyecto de abrir el elemento.  Sin embargo, si un elemento es miembro de más de un proyecto, el IDE utiliza un esquema de prioridad de determinar el mejor proyecto para abrir el elemento.  
  
 La lista siguiente muestra el esquema de la prioridad del proyecto:  
  
-   El IDE llama al método de <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject2.IsDocumentInProject%2A> para cada proyecto de la solución de determinar si el documento es miembro de ese proyecto.  
  
-   Si el documento es un miembro del proyecto, el proyecto responde con una prioridad esa las asignaciones de proyecto según su control de ese documento.  Por ejemplo, un proyecto de lenguaje responde con una prioridad alta para los archivos de código fuente del lenguaje pero responde con una prioridad para un tipo de archivo desconocido que no se utilice como parte del proceso de compilación.  
  
-   Los proyectos que proporcionan editores o diseñadores personalizados, específicos para un documento también reciben una prioridad alta.  
  
-   La enumeración de <xref:Microsoft.VisualStudio.Shell.Interop.VSDOCUMENTPRIORITY> proporciona valores de prioridad del documento.  
  
-   El proyecto que especifica la prioridad máxima recibe el contexto a abrir el documento.  si dos proyectos devuelven valores de prioridad iguales, se prefiere el proyecto activo.  Si responde ningún proyecto de la solución que puede abrir el documento, el IDE coloca el documento en el proyecto de archivos varios.  Para obtener más información, vea [Proyecto de archivos varios](../../extensibility/internals/miscellaneous-files-project.md).  
  
## Vea también  
 [Proyecto de archivos varios](../../extensibility/internals/miscellaneous-files-project.md)   
 [Cómo: abrir editores para los documentos abiertos](../../extensibility/how-to-open-editors-for-open-documents.md)   
 [Agregar proyecto y plantillas de elemento de proyecto](../../extensibility/internals/adding-project-and-project-item-templates.md)