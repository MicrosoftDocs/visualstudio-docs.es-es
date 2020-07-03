---
title: Crear un motor de depuración personalizado | Microsoft Docs
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- debug engines, implementing
- debug engines, custom
- debugging [Debugging SDK], custom debug engines
ms.assetid: 52794238-6fae-451c-bf1c-99f344c6f173
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 241bc016d8a64905951bffef07ba425f1351a727
ms.sourcegitcommit: 05487d286ed891a04196aacd965870e2ceaadb68
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/02/2020
ms.locfileid: "85903582"
---
# <a name="create-a-custom-debug-engine"></a>Crear un motor de depuración personalizado
Un motor de depuración (DE) es un componente que permite depurar determinadas arquitecturas en tiempo de ejecución. Normalmente solo hay una implementación DE para cada entorno en tiempo de ejecución.

> [!NOTE]
> Aunque hay implementaciones independientes de para Transact-SQL y JScript, VBScript y JScript comparten un único DE.

 Una DE funciona con el intérprete o el sistema operativo para proporcionar servicios de depuración como control de la ejecución, puntos de interrupción y evaluación de expresiones. Estos servicios se implementan a través DE las interfaces DE y pueden hacer que el depurador pase de un modo operativo a otro. Para obtener más información, vea [modos operativos](../../extensibility/debugger/operational-modes.md).

 La creación de un DE consta de los siguientes pasos:

1. Registro DE un DE con Visual Studio

2. Habilitar la depuración de un programa

3. Implementar control de ejecución y evaluación de estado

4. Envío de eventos

5. Configuración de la finalización y desasociación

## <a name="in-this-section"></a>En esta sección
 [Registrar un motor de depuración personalizado](../../extensibility/debugger/registering-a-custom-debug-engine.md) Explica los pasos necesarios para registrar un motor de depuración con Visual Studio para que se pueda usar.

 [Habilitar la depuración de un programa](../../extensibility/debugger/enabling-a-program-to-be-debugged.md) Explica que antes DE que el DE pueda depurar un programa, primero debe iniciar el DE o adjuntarlo a un programa existente.

 [Implementar control de ejecución y evaluación de estado](../../extensibility/debugger/execution-control-and-state-evaluation.md) Describe por qué la depuración de una aplicación requiere la implementación de características de control de ejecución.

 [Enviar eventos](../../extensibility/debugger/sending-events.md) Describe la comunicación entre el depurador y el DE como un modelo de eventos basado en DCOM.

 [Configuración de la finalización y desasociación](../../extensibility/debugger/termination-and-detaching.md) Explica cómo lograr la terminación normal, lo que significa que no hay puntos de interrupción, excepciones, errores en tiempo de ejecución ni bucles infinitos en la aplicación que se va a depurar.

 [Llamar a eventos del depurador](../../extensibility/debugger/calling-debugger-events.md) Documenta el orden de llamada de los eventos que se producen en una sesión de depuración.

 [Cómo: depurar un motor de depuración personalizado](../../extensibility/debugger/how-to-debug-a-custom-debug-engine.md) Explica cómo depurar un personalizado DE.

## <a name="see-also"></a>Vea también
- [Extensibilidad del depurador de Visual Studio](../../extensibility/debugger/visual-studio-debugger-extensibility.md)
