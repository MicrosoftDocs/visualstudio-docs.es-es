---
title: Enviando Eventos ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], sending events
ms.assetid: 064231e7-59b5-4437-8240-a23c0a7ec2a9
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5ec0d3aa29da562147b71b8efde49baf07d8ae0b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80713041"
---
# <a name="send-events"></a>Envío de eventos
El mecanismo de comunicación entre el depurador y el motor de depuración (DE) es un modelo de eventos basado en DCOM. Los eventos se envían como objetos COM y cada evento tiene parámetros que especifican:

- El DE que llamó al evento.

- Una descripción de lo que pasó.

- La información de proceso, programa y subproceso que identifica el contexto de donde se produjo el evento. El proceso no se envía para los eventos enviados desde un DE.

- El tipo de evento que indica si el evento es sincrónico o asincrónico.

  Todos los eventos de depuración se envían mediante el método [IDebugEventCallback2::Event](../../extensibility/debugger/reference/idebugeventcallback2-event.md).

## <a name="in-this-section"></a>En esta sección
 [Fuentes de eventos](../../extensibility/debugger/event-sources-visual-studio-sdk.md) Explica las dos fuentes de eventos: el motor de depuración (DE) y el administrador de depuración de sesión (SDM).

 [Tipos de eventos admitidos](../../extensibility/debugger/supported-event-types.md) Describe los tipos de eventos admitidos actualmente: asincrónicos y sincrónicos.

 [Descripciones de eventos](../../extensibility/debugger/event-descriptions.md) Define los eventos y las razones de su uso.

## <a name="related-sections"></a>Secciones relacionadas
 [Creación de un motor](../../extensibility/debugger/creating-a-custom-debug-engine.md) de depuración personalizado Describe cómo funciona un DE con el intérprete o el sistema operativo para proporcionar servicios de depuración.
