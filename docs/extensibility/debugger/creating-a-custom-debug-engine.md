---
title: Creación de un motor de depuración personalizado ( Custom Debug Engine ) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
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
ms.openlocfilehash: a350d640fffcc6e09cf8f981c797b97071a0cacf
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739040"
---
# <a name="create-a-custom-debug-engine"></a>Crear un motor de depuración personalizado
Un motor de depuración (DE) es un componente que permite la depuración de arquitecturas en tiempo de ejecución determinadas. Normalmente, solo hay una implementación DE por entorno en tiempo de ejecución.

> [!NOTE]
> Aunque hay implementaciones DE independientes para Transact-SQLTransact-SQL y JScript, VBScript y JScript comparten una sola DE.

 Un DE trabaja con el intérprete o el sistema operativo para proporcionar servicios de depuración como control de ejecución, puntos de interrupción y evaluación de expresiones. Estos servicios se implementan a través de las interfaces DE y pueden hacer que el depurador pase entre diferentes modos operativos. Para obtener más información, consulte [Modos operativos](../../extensibility/debugger/operational-modes.md).

 La creación de un DE consta de los siguientes pasos:

1. Registrar un DE con Visual Studio

2. Habilitar la depuración de un programa

3. Implementar el control de ejecución y la evaluación del estado

4. Envío de eventos

5. Configurar la terminación y desmontaje

## <a name="in-this-section"></a>En esta sección
 Registrar un motor de [depuración personalizado](../../extensibility/debugger/registering-a-custom-debug-engine.md) Explica los pasos necesarios para registrar un motor de depuración con Visual Studio para que se pueda usar.

 [Habilitar la depuración de un programa](../../extensibility/debugger/enabling-a-program-to-be-debugged.md) Explica que antes de que su DE pueda depurar un programa, primero debe iniciar el DE o adjuntarlo a un programa existente.

 [Implementar el control de ejecución y la evaluación del estado](../../extensibility/debugger/execution-control-and-state-evaluation.md) Describe por qué la depuración de una aplicación requiere la implementación de características de control de ejecución.

 [Enviar eventos](../../extensibility/debugger/sending-events.md) Describe la comunicación entre el depurador y la DE como un modelo de eventos basado en DCOM.

 [Configurar la terminación y desmontaje](../../extensibility/debugger/termination-and-detaching.md) Explica cómo lograr la terminación normal, lo que significa que no hay puntos de interrupción, excepciones, errores en tiempo de ejecución o bucles infinitos en la aplicación que se va a depurar.

 [Eventos del depurador de llamadas](../../extensibility/debugger/calling-debugger-events.md) Documenta el orden de llamada de los eventos que se producen en una sesión de depuración.

 [Cómo: Depurar un motor de depuración personalizado](../../extensibility/debugger/how-to-debug-a-custom-debug-engine.md) Explica cómo depurar un DE personalizado.

## <a name="see-also"></a>Vea también
- [Extensibilidad del depurador de Visual Studio](../../extensibility/debugger/visual-studio-debugger-extensibility.md)
