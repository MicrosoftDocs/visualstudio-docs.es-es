---
title: "Modelo de paquetes de Control de c&#243;digo fuente | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "control [Visual Studio SDK], modelo de origen"
ms.assetid: 6164b2d3-a622-4de8-bef3-a6de985e9ebd
caps.latest.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 13
---
# Modelo de paquetes de Control de c&#243;digo fuente
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

El modelo siguiente representa un ejemplo de una implementación del control de código fuente.  En el modelo, ve las interfaces que debe implementar y los servicios del entorno que debe llamar.  Como todos los servicios, se llama realmente los métodos de una interfaz concreta que obtenga el servicio.  Los nombres de las clases se identifican para que sea más fácil ver cómo se realiza el control de código fuente.  
  
 ![Ejemplos SCC&#95;TUP](~/extensibility/internals/media/scc_tup.gif "SCC\_TUP")  
Proyecto de control de código fuente de ejemplo  
  
## Interfaces  
 Puede implementar el control de código fuente para los nuevos tipos de proyectos en Visual Studio utilizando la lista de interfaces que se muestran en la tabla siguiente.  
  
|Interfaz|Utilice|  
|--------------|-------------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>|Llamado por proyectos y editores antes de que se guarda o cambian los archivos \(modificados\).  Esta interfaz se usa el servicio de <xref:Microsoft.VisualStudio.Shell.Interop.SVsQueryEditQuerySave> .|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>|Llama a proyectos de solicitar permiso para agregar, quitar, o cambiar el nombre de un archivo o directorio.  Esta interfaz también llaman proyectos de informar al entorno cuando se completa un aprobado add, remove, o cambiar la acción.  Se tiene acceso mediante el servicio de <xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackProjectDocuments> .|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2>|Implementa cualquier entidad que registre para ser notificada cuando los proyectos agregan, cambie, o quitar un archivo o directorio.  Para registrar la notificación de eventos, llame al <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2.AdviseTrackProjectDocumentsEvents%2A>.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2>|Llama a proyectos de registrar con el paquete de control de código fuente y obtener información sobre el estado del control de código fuente.  Esta interfaz se usa el servicio de <xref:Microsoft.VisualStudio.Shell.Interop.SVsSccManager> .|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2>|Implementa el proyecto de responder a las solicitudes de control de código fuente información sobre archivos y obtener los valores de control de código fuente necesarios para el archivo de proyecto.|  
  
## Vea también  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2.AdviseTrackProjectDocumentsEvents%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2>   
 [Compatibilidad con Control de código fuente](../../extensibility/internals/supporting-source-control.md)