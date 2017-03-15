---
title: "Abrir y guardar elementos de proyecto | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "proyectos de persistencia de archivo [Visual Studio SDK],"
  - "archivos [Visual Studio], abrir y guardar"
  - "persistencia de archivo editores [Visual Studio SDK]"
ms.assetid: f71898ad-335f-4c43-a177-4da87078afd1
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# Abrir y guardar elementos de proyecto
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Cuando se agrega un nuevo tipo de proyecto, debe administrar la apertura y guardar archivos de proyectos en el entorno de desarrollo integrado de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] \(IDE\).  Los temas siguientes describen los distintos enfoques para abrir y guardar archivos.  
  
## En esta sección  
 [Mostrar archivos mediante el comando Abrir archivo](../../extensibility/internals/displaying-files-by-using-the-open-file-command.md)  
 Proporciona una explicación paso a paso de cómo el IDE administra el comando de **Abrir archivo** y el rol de proyectos en respuesta a este comando.  
  
 [Visualización de archivos mediante el abrir con el comando](../../extensibility/internals/displaying-files-by-using-the-open-with-command.md)  
 Proporciona una explicación detallada, paso a paso de cómo el IDE administra el comando de **Abrir con** , y le solicita que la apertura de un archivo con alguna opción de editores estándar.  
  
 [Cómo: abrir editores específicos del proyecto](../../extensibility/how-to-open-project-specific-editors.md)  
 Proporciona instrucciones paso a paso para especificar que los archivos de un tipo determinado en el proyecto se abran mediante un editor específico del proyecto.  
  
 [Cómo: abrir editores estándares](../../extensibility/how-to-open-standard-editors.md)  
 Proporciona instrucciones paso a paso para especificar cómo permitir al IDE para abrir un editor estándar para los archivos del tipo de proyecto.  
  
 [Cómo: abrir editores para los documentos abiertos](../../extensibility/how-to-open-editors-for-open-documents.md)  
 Proporciona instrucciones paso a paso de abrir un editor específico de proyecto para un archivo abierto.  
  
 [Guardar un documento estándar](../../extensibility/internals/saving-a-standard-document.md)  
 Proporciona una explicación detallada de cómo el IDE administra **Guardar**, **Guardar como**, y los comandos de **Guardar todos** para un documento abierto en un editor estándar.  
  
 [Guardar un documento personalizado](../../extensibility/internals/saving-a-custom-document.md)  
 Proporciona un diagrama y la explicación detallada de cómo el IDE administra **Guardar**, los comandos de **Guardar como**, y de **Guardar todos** para los documentos abiertos en un editor personalizado.  
  
 [Determinar qué Editor se abre un archivo en un proyecto](../../extensibility/internals/determining-which-editor-opens-a-file-in-a-project.md)  
 Explica el proceso que el IDE sigue para seleccionar el editor o diseñador adecuado para un archivo.  
  
## Secciones relacionadas  
 [Creación de diseñadores y editores personalizados](../../extensibility/creating-custom-editors-and-designers.md)  
 Enumera los cuatro tipos de editores que el host de la capacidad del IDE y dar a descripciones de cada editorial.  
  
 [Tipos de proyecto](../../extensibility/internals/project-types.md)  
 Explica cómo los proyectos controlan la forma en que el código se compila y integrado, cómo se abren los editores, y cómo se da formato a los elementos de proyecto.