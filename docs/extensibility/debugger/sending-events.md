---
title: Envío de eventos | Microsoft Docs
description: Obtenga información sobre cómo el depurador y el motor de depuración usan un modelo de eventos basado en DCOM. Los eventos se envían como objetos COM.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- debugging [Debugging SDK], sending events
ms.assetid: 064231e7-59b5-4437-8240-a23c0a7ec2a9
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 6e9af2618150df522a459e47f312c1dc1e6a220c
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/25/2021
ms.locfileid: "112902259"
---
# <a name="send-events"></a>Envío de eventos
El mecanismo de comunicación entre el depurador y el motor de depuración (DE) es un modelo de eventos basado en DCOM. Los eventos se envían como objetos COM y cada evento tiene parámetros que especifican:

- DE que llamó al evento.

- Descripción de lo que ha ocurrido.

- Información sobre el proceso, el programa y el subproceso que identifica el contexto en el que se produjo el evento. El proceso no se envía para los eventos enviados desde un DE.

- Tipo de evento que indica si el evento es sincrónico o asincrónico.

  Todos los eventos de depuración se envían mediante el [método IDebugEventCallback2::Event](../../extensibility/debugger/reference/idebugeventcallback2-event.md).

## <a name="in-this-section"></a>En esta sección
 [Orígenes de eventos](../../extensibility/debugger/event-sources-visual-studio-sdk.md) Explica los dos orígenes de eventos: el motor de depuración (DE) y el administrador de depuración de sesión (SDM).

 [Tipos de eventos admitidos](../../extensibility/debugger/supported-event-types.md) Describe los tipos de eventos admitidos actualmente: asincrónicos y sincrónicos.

 [Descripciones de eventos](../../extensibility/debugger/event-descriptions.md) Define los eventos y las razones de su uso.

## <a name="related-sections"></a>Secciones relacionadas
 [Creación de un motor de depuración personalizado](../../extensibility/debugger/creating-a-custom-debug-engine.md) Describe cómo funciona un DE con el intérprete o el sistema operativo para proporcionar servicios de depuración.
