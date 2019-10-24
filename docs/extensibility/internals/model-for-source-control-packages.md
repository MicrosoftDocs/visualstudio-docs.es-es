---
title: Modelo de paquetes de control de código fuente | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], model
ms.assetid: 6164b2d3-a622-4de8-bef3-a6de985e9ebd
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1a9ae5f2704d625da2212e92626c33fb384ebbc5
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/22/2019
ms.locfileid: "72726565"
---
# <a name="model-for-source-control-packages"></a>Modelo para paquetes de control de código fuente
El modelo siguiente representa un ejemplo de una implementación de control de código fuente. En el modelo, verá las interfaces que debe implementar y los servicios de entorno a los que debe llamar. Al igual que todos los servicios, en realidad se llama a los métodos de una interfaz determinada que se obtiene por medio del servicio. Los nombres de las clases se identifican para facilitar la visualización del modo en que se realiza el control de código fuente.

 ![Ejemplos&#95;de instalado de SCC](../../extensibility/internals/media/scc_tup.gif "SCC_TUP") Proyecto de control de código fuente de ejemplo

## <a name="interfaces"></a>Interfaces
 Puede implementar el control de código fuente para los nuevos tipos de proyecto en Visual Studio mediante la lista de interfaces que se muestran en la tabla siguiente.

|Interfaz|Usar|
|---------------|---------|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>|Lo llaman los proyectos y los editores antes de guardar o cambiar los archivos (modificados). Se tiene acceso a esta interfaz mediante el servicio de <xref:Microsoft.VisualStudio.Shell.Interop.SVsQueryEditQuerySave>.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>|Lo llaman los proyectos para solicitar permiso para agregar, quitar o cambiar el nombre de un archivo o directorio. Los proyectos también llaman a esta interfaz para informar al entorno cuando se completa una acción de agregar, quitar o cambiar nombre. Se tiene acceso a él mediante el servicio de <xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackProjectDocuments>.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2>|Implementado por cualquier entidad que se registra para recibir una notificación cuando los proyectos agreguen, cambien el nombre o quiten un archivo o un directorio. Para registrarse para la notificación de eventos, llame a <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2.AdviseTrackProjectDocumentsEvents%2A>.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2>|Lo llaman los proyectos para registrarse con el paquete de control de código fuente y obtener información sobre el estado del control de código fuente. Se tiene acceso a esta interfaz mediante el servicio de <xref:Microsoft.VisualStudio.Shell.Interop.SVsSccManager>.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2>|Implementado por el proyecto para responder a las solicitudes de control de código fuente para obtener información sobre los archivos y para obtener la configuración de control de código fuente necesaria para el archivo de proyecto.|

## <a name="see-also"></a>Vea también
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2.AdviseTrackProjectDocumentsEvents%2A>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2>
- [Compatibilidad con control de código fuente](../../extensibility/internals/supporting-source-control.md)