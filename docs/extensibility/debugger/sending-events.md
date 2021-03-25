---
title: Enviar eventos | Microsoft Docs
description: Obtenga información sobre cómo el depurador y el motor de depuración utilizan un modelo de eventos basado en DCOM. Los eventos se envían como objetos COM.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], sending events
ms.assetid: 064231e7-59b5-4437-8240-a23c0a7ec2a9
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 135dd0278ee765ef88ae6cef39675a2fa92236d7
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/25/2021
ms.locfileid: "105070399"
---
# <a name="send-events"></a>Envío de eventos
El mecanismo de comunicación entre el depurador y el motor de depuración (DE) es un modelo de eventos basado en DCOM. Los eventos se envían como objetos COM y cada evento tiene parámetros que especifican:

- DE que llamó al evento.

- Una descripción de lo que ha sucedido.

- Información sobre el proceso, el programa y el subproceso que identifica el contexto en el que se produjo el evento. No se envía el proceso para los eventos enviados desde un DE.

- Tipo de evento que indica si el evento es sincrónico o asincrónico.

  Todos los eventos de depuración se envían mediante el método [IDebugEventCallback2:: Event](../../extensibility/debugger/reference/idebugeventcallback2-event.md).

## <a name="in-this-section"></a>En esta sección
 [Orígenes de eventos](../../extensibility/debugger/event-sources-visual-studio-sdk.md) Explica los dos orígenes de eventos: el motor de depuración (DE) y el administrador de depuración de sesión (SDM).

 [Tipos de eventos admitidos](../../extensibility/debugger/supported-event-types.md) Describe los tipos de eventos admitidos actualmente: asincrónicos y sincrónicos.

 [Descripciones de eventos](../../extensibility/debugger/event-descriptions.md) Define los eventos y los motivos para su uso.

## <a name="related-sections"></a>Secciones relacionadas
 [Crear un motor de depuración personalizado](../../extensibility/debugger/creating-a-custom-debug-engine.md) Describe cómo funciona un DE con el intérprete o el sistema operativo para proporcionar servicios de depuración.
