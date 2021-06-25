---
title: Documentación de Windows | Microsoft Docs
description: Obtenga información sobre las ventanas de Visual Studio, incluido cómo implementarlas y cómo la tabla de documentos en ejecución (RDT) realiza un seguimiento de su estado.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Visual Studio SDK, document windows
ms.assetid: 50081d48-987f-43db-8bf9-51b7cf76e9c0
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: df7a797c0b4587698197412f49eef6bfab183a7a
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/25/2021
ms.locfileid: "112899919"
---
# <a name="document-windows"></a>Ventanas de documento
En Visual Studio, una ventana *de* documento es una ventana secundaria enmarcada que está asociada a una ventana de interfaz de varios documentos (MDI). Las ventanas de documento se usan normalmente para mostrar y modificar el código fuente o el texto, pero también pueden hospedar otros tipos funcionales. Ventanas de documentos:

- Se puede organizar en grupos de pestañas horizontales o verticales independientes en el MDI primario para que se puedan ver varios archivos al mismo tiempo.

- Se puede acoplar en cualquier orden en el MDI primario.

- Se puede flotar libremente.

- Se vinculan en orden de tabulación a otras ventanas MDI.

  Los comandos de agrupación, acoplamiento y flotante se pueden encontrar en el menú contextual de una pestaña de ventana de documento.

  Para obtener más información sobre el comportamiento de la ventana Visual Studio, vea [Personalizar diseños de ventana.](../../ide/customizing-window-layouts-in-visual-studio.md)

## <a name="document-window-implementation"></a>Implementación de ventana de documento
 Las ventanas de documento se crean mediante la implementación de un editor. La <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory> interfaz crea ventanas de documentos como parte de la creación de instancias de un editor. Para obtener más información, vea [Interfaces heredadas en el editor](/previous-versions/visualstudio/visual-studio-2015/extensibility/legacy-interfaces-in-the-editor?preserve-view=true&view=vs-2015).

> [!NOTE]
> Para proporcionar puntos de navegación hacia atrás y hacia delante en una ventana, implemente la <xref:Microsoft.VisualStudio.Shell.Interop.IVsBackForwardNavigation> interfaz . El editor de texto usa marcadores de texto para identificar los puntos de navegación del documento.

## <a name="the-running-document-table"></a>Tabla de documentos en ejecución
 El IDE usa la tabla de documentos en ejecución (RDT) para realizar un seguimiento del estado de cada ventana de documento. RDT es el mecanismo a través del cual se notifica a las ventanas de documentos eventos, como cuando se cierra una solución o cuando se ha editado un archivo. Para obtener más información, vea [Running document table](../../extensibility/internals/running-document-table.md).

## <a name="see-also"></a>Consulta también
- [Carga retrasada de documentos](../../extensibility/internals/delayed-document-loading.md)
