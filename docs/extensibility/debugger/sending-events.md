---
title: Envío de eventos | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], sending events
ms.assetid: 064231e7-59b5-4437-8240-a23c0a7ec2a9
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 397c5edfb76d2a4277db0e805daf4a55bd9608dc
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/25/2019
ms.locfileid: "54995833"
---
# <a name="send-events"></a>Envío de eventos
El mecanismo para la comunicación entre el depurador y el motor de depuración (DE) es un modelo de eventos en función de DCOM. Los eventos se envían como objetos COM, y cada evento tiene parámetros que especifican:  
  
- La DE que llama el evento.  
  
- Una descripción de lo que sucedió.  
  
- El proceso, el programa y la información de subproceso que identifica el contexto de dónde se produjo el evento. El proceso no se envía para eventos enviados desde un DE.  
  
- El tipo de evento que indica si el evento es sincrónica o asincrónica.  
  
  Todos los eventos de depuración se envían mediante el método [IDebugEventCallback2::Event](../../extensibility/debugger/reference/idebugeventcallback2-event.md).  
  
## <a name="in-this-section"></a>En esta sección  
 [Orígenes de eventos](../../extensibility/debugger/event-sources-visual-studio-sdk.md)  
 Explica los dos orígenes de eventos: el motor de depuración (DE) y la sesión de depuración manager (SDM).  
  
 [Tipos de evento compatibles](../../extensibility/debugger/supported-event-types.md)  
 Describe los tipos de eventos actualmente admitidos: sincrónicas y asincrónicas.  
  
 [Descripciones de evento](../../extensibility/debugger/event-descriptions.md)  
 Define los eventos y los motivos para su uso.  
  
## <a name="related-sections"></a>Secciones relacionadas  
 [Creación de un motor de depuración personalizado](../../extensibility/debugger/creating-a-custom-debug-engine.md)  
 Describe cómo funciona a DE con el sistema operativo o intérprete para proporcionar servicios de depuración.