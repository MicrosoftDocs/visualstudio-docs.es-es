---
title: "El envío de eventos | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: debugging [Debugging SDK], sending events
ms.assetid: 064231e7-59b5-4437-8240-a23c0a7ec2a9
caps.latest.revision: "7"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: bf4c3b0f494a5825820b8f794ccaf5dc727786e3
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="sending-events"></a>El envío de eventos
El mecanismo de comunicación entre el depurador y el motor de depuración (Alemania) es un modelo de eventos basado en DCOM. Los eventos se envían como objetos COM, y cada evento tiene parámetros que especifican lo siguiente:  
  
-   Alemania a la que llama el evento.  
  
-   Una descripción de lo que sucedió.  
  
-   El proceso, el programa y la información del subproceso que identifica el contexto de donde se produjo el evento. El proceso no se envía para eventos enviados desde un Alemania.  
  
-   El tipo de evento que indica si el evento es sincrónico o asincrónico.  
  
 Todos los eventos de depuración se envían mediante el método [IDebugEventCallback2::Event](../../extensibility/debugger/reference/idebugeventcallback2-event.md).  
  
## <a name="in-this-section"></a>En esta sección  
 [Orígenes de eventos](../../extensibility/debugger/event-sources-visual-studio-sdk.md)  
 Explica los dos orígenes de eventos: el motor de depuración (Alemania) y la sesión de depuración de administrador (SDM).  
  
 [Tipos de evento compatibles](../../extensibility/debugger/supported-event-types.md)  
 Describe los tipos de evento admitidos actualmente: sincrónico y asincrónico.  
  
 [Descripciones de eventos](../../extensibility/debugger/event-descriptions.md)  
 Define los eventos y los motivos para su uso.  
  
## <a name="related-sections"></a>Secciones relacionadas  
 [Creación de un motor de depuración personalizado](../../extensibility/debugger/creating-a-custom-debug-engine.md)  
 Describe cómo funciona un Alemania con el sistema operativo o intérprete para proporcionar servicios de depuración.