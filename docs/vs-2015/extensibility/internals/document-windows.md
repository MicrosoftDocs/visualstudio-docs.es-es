---
title: Ventanas de documento | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio SDK, document windows
ms.assetid: 50081d48-987f-43db-8bf9-51b7cf76e9c0
caps.latest.revision: 18
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 5e62be456422b7ee5e9f2828a44a6be05e1211d9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "90842531"
---
# <a name="document-windows"></a>Ventanas de documento
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

En Visual Studio, una *ventana de documento* es una ventana secundaria con marco que está asociada a una ventana de interfaz de múltiples documentos (MDI). Las ventanas de documento se usan normalmente para mostrar y modificar el código fuente o el texto, pero también pueden hospedar otros tipos funcionales. Ventanas de documento:  
  
- Se pueden organizar en grupos de pestañas horizontales o verticales independientes en el MDI primario para que se puedan ver varios archivos al mismo tiempo.  
  
- Se puede acoplar en cualquier orden en el MDI primario.  
  
- Puede flotar libremente.  
  
- Se vinculan en el orden de tabulación a otras ventanas MDI.  
  
  Los comandos para agrupar, acoplar y flotar se pueden encontrar en el menú contextual de una pestaña de la ventana de documento.  
  
  Para obtener más información sobre el comportamiento de las ventanas en Visual Studio, vea [personalizar los diseños de ventana](../../ide/customizing-window-layouts-in-visual-studio.md).  
  
## <a name="document-window-implementation"></a>Implementación de ventana de documento  
 Las ventanas de documento se crean mediante la implementación de un editor. La <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory> interfaz crea ventanas de documento como parte de la creación de instancias de un editor. Para obtener más información, vea [interfaces heredadas en el editor](../../extensibility/legacy-interfaces-in-the-editor.md).  
  
> [!NOTE]
> Para proporcionar puntos de navegación hacia atrás y hacia delante en una ventana, implemente la <xref:Microsoft.VisualStudio.Shell.Interop.IVsBackForwardNavigation> interfaz. El editor de texto utiliza marcadores de texto para identificar los puntos de navegación del documento.  
  
## <a name="the-running-document-table"></a>La tabla de documentos en ejecución  
 El IDE usa la tabla de documentos en ejecución (RDT) para realizar un seguimiento del estado de cada ventana de documento. RDT es el mecanismo a través del cual se notifican los eventos a las ventanas de documento, como cuando se cierra una solución o cuando se edita un archivo. Para obtener más información, vea [ejecutar la tabla de documentos](../../extensibility/internals/running-document-table.md).  
  
## <a name="see-also"></a>Consulte también  
 [Carga de documentos retrasada](../../extensibility/internals/delayed-document-loading.md)
