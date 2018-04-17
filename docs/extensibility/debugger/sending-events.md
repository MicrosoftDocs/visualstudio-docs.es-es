---
title: El envío de eventos | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], sending events
ms.assetid: 064231e7-59b5-4437-8240-a23c0a7ec2a9
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 9bbe7946b866cd751be1f0dac2dba5b8dea57e04
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
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