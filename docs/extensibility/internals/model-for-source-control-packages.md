---
title: Modelo para paquetes de control de código fuente ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], model
ms.assetid: 6164b2d3-a622-4de8-bef3-a6de985e9ebd
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 46845be1bc22a67d6703af12933945bdfcfa7f4b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707072"
---
# <a name="model-for-source-control-packages"></a>Modelo para paquetes de control de código fuente
El modelo siguiente representa un ejemplo de una implementación de control de código fuente. En el modelo, verá las interfaces que debe implementar y los servicios de entorno a los que debe llamar. Al igual que todos los servicios, en realidad se llaman los métodos de una interfaz determinada que se obtiene n.o del servicio. Los nombres de las clases se identifican para facilitar la ver cómo se lleva a cabo el control de código fuente.

 ![Ejemplos de SCC&#95;TUP](../../extensibility/internals/media/scc_tup.gif "SCC_TUP") Ejemplo de proyecto de control de código fuente

## <a name="interfaces"></a>Interfaces
 Puede implementar el control de código fuente para los nuevos tipos de proyecto en Visual Studio mediante la lista de interfaces que se muestra en la tabla siguiente.

|Interfaz|Uso|
|---------------|---------|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>|Llamado por proyectos y editores antes de guardar o cambiar archivos (sucios). Se accede a <xref:Microsoft.VisualStudio.Shell.Interop.SVsQueryEditQuerySave> esta interfaz mediante el servicio.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>|Llamado por los proyectos para solicitar permiso para agregar, quitar o cambiar el nombre de un archivo o directorio. Los proyectos también llaman a esta interfaz para informar al entorno cuando se completa una acción de agregar, quitar o cambiar el nombre aprobada. Se accede mediante <xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackProjectDocuments> el servicio.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2>|Implementado por cualquier entidad que se registre para recibir una notificación cuando los proyectos agreguen, renombre o quiten un archivo o directorio. Para registrarse para <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2.AdviseTrackProjectDocumentsEvents%2A>la notificación de eventos, llame a .|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2>|Llamado por los proyectos para registrarse con el paquete de control de código fuente y para obtener información sobre el estado del control de código fuente. Se accede a <xref:Microsoft.VisualStudio.Shell.Interop.SVsSccManager> esta interfaz mediante el servicio.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2>|Implementado por el proyecto para responder a las solicitudes de control de código fuente para obtener información sobre los archivos y para obtener la configuración de control de código fuente necesaria para el archivo de proyecto.|

## <a name="see-also"></a>Vea también
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2.AdviseTrackProjectDocumentsEvents%2A>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2>
- [Compatibilidad con control de código fuente](../../extensibility/internals/supporting-source-control.md)
