---
title: "Compatibilidad con Control de c&#243;digo fuente | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "origen de control [Visual Studio SDK], compatibilidad"
ms.assetid: 567acde3-354e-4f39-8d99-0ef86c103396
caps.latest.revision: 18
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 18
---
# Compatibilidad con Control de c&#243;digo fuente
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] admite desprotecciones de archivo, protecciones, y otras operaciones de control de código fuente del proyecto o el editor.  Como cliente de control de código fuente, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] está diseñado para interactuar con un paquete de control de código fuente, como [!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)], que proporciona el archivado, la versión, y las funciones de control para un conjunto de archivos definidos dinámicamente.  
  
## En esta sección  
 [Modelo de paquetes de Control de código fuente](../../extensibility/internals/model-for-source-control-packages.md)  
 describe las interfaces que un tipo de proyecto debe implementar para admitir el control de código fuente.  
  
 [Decisiones de diseño](../../extensibility/internals/source-control-design-decisions.md)  
 Proporciona las preguntas cuyas respuestas cambia cómo se implementa un tipo de proyecto.  
  
 [Detalles de configuración](../../extensibility/internals/source-control-configuration-details.md)  
 describe cómo admite cambios de control de código fuente la implementación de un tipo de proyecto.  
  
 [Instrucciones adicionales para los proyectos y editores](../../extensibility/internals/additional-source-control-guidelines-for-projects-and-editors.md)  
 Describe los procedimientos recomendados para los tipos y los editores.  
  
 [Detalles de tiempo de ejecución](../../extensibility/internals/source-control-runtime-details.md)  
 describe cómo registrar un proyecto cuando un usuario lo agrega a un sistema de control de código fuente.  
  
## Referencia  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>  
 Indica al entorno o paquete de control de código fuente que un archivo se va a cambiar en memoria o guardar.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2>  
 Permite proyectos y jerarquías de registrar con el control de código fuente y obtener información sobre el estado de control de código fuente.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2>  
 Implementado en un sistema de proyectos para proporcionar el control de código fuente para los archivos de proyecto y elementos de proyecto.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>  
 Utilizado por proyectos de ver el entorno permiso para agregar, quitar, o cambiar el nombre de un archivo o directorio en una solución.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2>  
 Notifica a los clientes de los cambios realizados en los archivos de proyecto o directorios.  
  
## Secciones relacionadas  
 [Tipos de proyecto](../../extensibility/internals/project-types.md)  
 Proporciona información general sobre proyectos como bloques de creación básicos del entorno de desarrollo integrado de \(IDE\) [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .  Los vínculos se proporcionan a los otros temas que explican cómo código que compila y de compilación del control de proyectos.