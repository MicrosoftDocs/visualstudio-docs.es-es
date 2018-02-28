---
title: Las ventanas de documento | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Visual Studio SDK, document windows
ms.assetid: 50081d48-987f-43db-8bf9-51b7cf76e9c0
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 03e61b80aaf4c5c8b0e25f5b2a4a42f13d75d305
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="document-windows"></a>Ventanas de documento
En Visual Studio, un *ventana de documento* es una ventana secundaria enmarcado que está asociada a una ventana de interfaz de múltiples documentos (MDI). Normalmente se usan las ventanas de documento para la visualización y modificación de código fuente o el texto, pero también pueden hospedar otros tipos funcionales. Ventanas de documento:  
  
-   Se pueden organizar en grupos de pestañas independientes de horizontal o vertical en el elemento primario MDI para que puedan ver varios archivos al mismo tiempo.  
  
-   Se pueden acoplar en cualquier orden en el elemento primario MDI.  
  
-   Puede flotar libremente.  
  
-   Se vinculan en orden de tabulación en otras ventanas MDI.  
  
 Los comandos para la agrupación, acoplar y desacoplar pueden encontrarse en el menú contextual de una pestaña de ventana de documento.  
  
 Para obtener más información sobre el comportamiento de las ventanas en Visual Studio, vea [personalizar los diseños de ventana](../../ide/customizing-window-layouts-in-visual-studio.md).  
  
## <a name="document-window-implementation"></a>Implementación de la ventana de documento  
 Ventanas de documento se crean mediante la implementación de un editor. El <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory> interfaz crea las ventanas de documento como parte de una instancia de un editor. Para obtener más información, consulte [Interfaces heredado en el Editor de](../../extensibility/legacy-interfaces-in-the-editor.md).  
  
> [!NOTE]
>  Para proporcionar hacia atrás y reenviar los puntos de navegación en una ventana, implementar la <xref:Microsoft.VisualStudio.Shell.Interop.IVsBackForwardNavigation> interfaz. El editor de texto usa marcadores de texto para identificar los puntos de navegación en el documento.  
  
## <a name="the-running-document-table"></a>La tabla Document de ejecución  
 El IDE usa la tabla document ejecución (RDT) para realizar un seguimiento del estado de cada ventana de documento. El RDT es el mecanismo a través de qué documento son una notificación de eventos, como cuando se cierra una solución o cuando se ha editado un archivo de windows. Para obtener más información, consulte [ejecutando tabla Document](../../extensibility/internals/running-document-table.md).  
  
## <a name="see-also"></a>Vea también  
 [Carga de documentos retrasada](../../extensibility/internals/delayed-document-loading.md)