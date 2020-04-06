---
title: Ventanas del documento ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio SDK, document windows
ms.assetid: 50081d48-987f-43db-8bf9-51b7cf76e9c0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 711033a4ad2e782ecbe509595266426d186bed8f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708513"
---
# <a name="document-windows"></a>Ventanas de documento
En Visual Studio, una ventana de *documento* es una ventana secundaria con marco que está asociada a una ventana de interfaz de varios documentos (MDI). Las ventanas de documento se usan normalmente para la visualización y modificación del código fuente o el texto, pero también pueden hospedar otros tipos funcionales. Ventanas de documentos:

- Se puede organizar en grupos de pestañas horizontales o verticales independientes en el MDI primario para que se puedan ver varios archivos al mismo tiempo.

- Se puede acoplar en cualquier orden en el MDI principal.

- Se puede flotar libremente.

- Se vinculan en orden de tabulación a otras ventanas MDI.

  Los comandos para agrupar, acoplar y flotante se pueden encontrar en el menú contextual de una pestaña de ventana de documento.

  Para obtener más información sobre el comportamiento de la ventana en Visual Studio, vea [Personalizar diseños](../../ide/customizing-window-layouts-in-visual-studio.md)de ventana .

## <a name="document-window-implementation"></a>Implementación de la ventana de documentos
 Las ventanas de documento se crean mediante la implementación de un editor. La <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory> interfaz crea ventanas de documentos como parte de la creación de instancias de un editor. Para obtener más información, consulte [Interfaces heredadas en el editor.](/visualstudio/extensibility/legacy-interfaces-in-the-editor?view=vs-2015)

> [!NOTE]
> Para proporcionar puntos de navegación hacia <xref:Microsoft.VisualStudio.Shell.Interop.IVsBackForwardNavigation> atrás y hacia delante en una ventana, implemente la interfaz. El editor de texto utiliza marcadores de texto para identificar los puntos de navegación en el documento.

## <a name="the-running-document-table"></a>La tabla Documento en ejecución
 El IDE utiliza la tabla de documentos en ejecución (RDT) para realizar un seguimiento del estado de cada ventana de documento. El RDT es el mecanismo a través del cual se notifican eventos a las ventanas de documentos, como cuando se cierra una solución o cuando se ha editado un archivo. Para obtener más información, consulte Ejecución de la tabla de [documentos](../../extensibility/internals/running-document-table.md).

## <a name="see-also"></a>Vea también
- [Carga de documentos retrasada](../../extensibility/internals/delayed-document-loading.md)
