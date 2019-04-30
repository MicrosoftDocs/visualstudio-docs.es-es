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
ms.openlocfilehash: cd282dd38d322a5b7d9821406d30a303fabb02bb
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62864355"
---
# <a name="send-events"></a>Envío de eventos
El mecanismo para la comunicación entre el depurador y el motor de depuración (DE) es un modelo de eventos en función de DCOM. Los eventos se envían como objetos COM, y cada evento tiene parámetros que especifican:

- La DE que llama el evento.

- Una descripción de lo que sucedió.

- El proceso, el programa y la información de subproceso que identifica el contexto de dónde se produjo el evento. El proceso no se envía para eventos enviados desde un DE.

- El tipo de evento que indica si el evento es sincrónica o asincrónica.

  Todos los eventos de depuración se envían mediante el método [IDebugEventCallback2::Event](../../extensibility/debugger/reference/idebugeventcallback2-event.md).

## <a name="in-this-section"></a>En esta sección
 [Orígenes de eventos](../../extensibility/debugger/event-sources-visual-studio-sdk.md) explica los dos orígenes de eventos: el motor de depuración (DE) y la sesión de depuración manager (SDM).

 [Admite los tipos de evento](../../extensibility/debugger/supported-event-types.md) se describen los tipos de eventos actualmente admitidos: sincrónicas y asincrónicas.

 [Las descripciones de evento](../../extensibility/debugger/event-descriptions.md) define los eventos y los motivos para su uso.

## <a name="related-sections"></a>Secciones relacionadas
 [Creación de un motor de depuración](../../extensibility/debugger/creating-a-custom-debug-engine.md) describe el funcionamiento a DE con el sistema operativo o intérprete para proporcionar servicios de depuración.