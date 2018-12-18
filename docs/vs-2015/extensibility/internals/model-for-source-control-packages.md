---
title: Modelo para paquetes de Control de código fuente | Documentos de Microsoft
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
- source control [Visual Studio SDK], model
ms.assetid: 6164b2d3-a622-4de8-bef3-a6de985e9ebd
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 27bac56b862d4a3dfd0495420ee20920801faaae
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/16/2018
ms.locfileid: "51734133"
---
# <a name="model-for-source-control-packages"></a>Modelo para paquetes de control de código fuente
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

El modelo siguiente representa un ejemplo de una implementación de control de código fuente. En el modelo, vea las interfaces que debe implementar y los servicios del entorno que se deben llamar. Al igual que todos los servicios, se llama realmente a los métodos de una interfaz concreta que se obtiene por medio del servicio. Los nombres de las clases se identifican para que sea más fácil ver cómo se efectúa el control de código fuente.  
  
 ![SCC&#95;ejemplos SCRIP](../../extensibility/internals/media/scc-tup.gif "SCC_TUP")  
Proyecto de Control de código fuente de ejemplo  
  
## <a name="interfaces"></a>Interfaces  
 Puede implementar el control de código fuente para los nuevos tipos de proyecto en Visual Studio mediante la lista de interfaces que se muestran en la tabla siguiente.  
  
|Interfaz|Usar|  
|---------------|---------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>|Lo llaman los proyectos y editores antes de que guarde o archivos de cambio (modificado). Esta interfaz se obtiene acceso mediante el <xref:Microsoft.VisualStudio.Shell.Interop.SVsQueryEditQuerySave> service.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>|Lo llaman los proyectos para solicitar permiso para agregar, quitar o cambiar el nombre de un archivo o directorio. Esta interfaz también lo llaman los proyectos para informar el entorno cuando una adición aprobada, quitar o cambiar el nombre de la acción ha finalizado. Se tiene acceso con el <xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackProjectDocuments> service.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2>|Implementado por cualquier entidad que se registra para recibir una notificación cuando los proyectos de agregarán, cambiar el nombre o quitar un archivo o directorio. Para registrar la notificación de eventos, llamar a <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2.AdviseTrackProjectDocumentsEvents%2A>.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2>|Lo llaman los proyectos para registrar con el paquete de control de código fuente y obtener información sobre el estado de control de código fuente. Esta interfaz se obtiene acceso mediante el <xref:Microsoft.VisualStudio.Shell.Interop.SVsSccManager> service.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2>|Implementa el proyecto para responder a las solicitudes de control de código fuente para obtener información acerca de los archivos y obtener el origen de configuración de control necesario para el archivo de proyecto.|  
  
## <a name="see-also"></a>Vea también  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2.AdviseTrackProjectDocumentsEvents%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2>   
 [Compatibilidad con control de código fuente](../../extensibility/internals/supporting-source-control.md)

