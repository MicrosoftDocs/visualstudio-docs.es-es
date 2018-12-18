---
title: Modelo para los paquetes de Control de código fuente | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], model
ms.assetid: 6164b2d3-a622-4de8-bef3-a6de985e9ebd
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: fa0dcdd930412e4e53c59509848f0b7c1503c47b
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
ms.locfileid: "31129448"
---
# <a name="model-for-source-control-packages"></a>Modelo para los paquetes de Control de código fuente
El modelo siguiente representa un ejemplo de una implementación de control de código fuente. En el modelo, vea las interfaces que debe implementar y los servicios de entorno que se deben llamar. Al igual que todos los servicios, se llame realmente a los métodos de una interfaz concreta que obtiene mediante el servicio. Los nombres de las clases se identifican para que sea más fácil ver cómo se efectúa el control de código fuente.  
  
 ![SCC&#95;ejemplos TUP](../../extensibility/internals/media/scc_tup.gif "SCC_TUP")  
Proyecto de Control de código fuente de ejemplo  
  
## <a name="interfaces"></a>Interfaces  
 Puede implementar el control de código fuente para los nuevos tipos de proyecto en Visual Studio mediante la lista de interfaces que se muestran en la tabla siguiente.  
  
|Interfaz|Usar|  
|---------------|---------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>|Llama a los proyectos y editores antes de que guarde o archivos de cambio (modificado). Esta interfaz se tiene acceso con el <xref:Microsoft.VisualStudio.Shell.Interop.SVsQueryEditQuerySave> service.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>|Llama a los proyectos para solicitar permiso para agregar, quitar o cambiar el nombre de un archivo o directorio. Esta interfaz también se denomina proyectos para informar el entorno cuando una aprobadas de agregar, quitar o cambiar el nombre de acción ha finalizado. Se tiene acceso mediante el <xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackProjectDocuments> service.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2>|Implementado por cualquier entidad que se registra para recibir una notificación cuando agrega proyectos, cambiar el nombre o quitar un archivo o directorio. Para registrarse para la notificación de eventos, llamar a <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2.AdviseTrackProjectDocumentsEvents%2A>.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2>|Llama a los proyectos que se va a registrar con el paquete de control de código fuente como obtener información sobre el estado de control de código fuente. Esta interfaz se tiene acceso con el <xref:Microsoft.VisualStudio.Shell.Interop.SVsSccManager> service.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2>|Implementa el proyecto para responder a las solicitudes de control de código fuente para obtener información acerca de los archivos y para obtener el origen de la configuración de control necesaria para el archivo de proyecto.|  
  
## <a name="see-also"></a>Vea también  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2.AdviseTrackProjectDocumentsEvents%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2>   
 [Compatibilidad con control de código fuente](../../extensibility/internals/supporting-source-control.md)