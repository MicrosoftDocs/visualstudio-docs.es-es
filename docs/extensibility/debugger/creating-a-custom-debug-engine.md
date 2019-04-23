---
title: Creación de un archivo de motor de depuración | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debug engines, implementing
- debug engines, custom
- debugging [Debugging SDK], custom debug engines
ms.assetid: 52794238-6fae-451c-bf1c-99f344c6f173
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 67a58ab1bf508ba1b2edc7117412638de6c2231a
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/22/2019
ms.locfileid: "60099551"
---
# <a name="create-a-custom-debug-engine"></a>Crear un motor de depuración personalizado
Un motor de depuración (DE) es un componente que permite la depuración de las arquitecturas de tiempo de ejecución determinadas. Normalmente hay solo una implementación DE cada entorno de tiempo de ejecución.

> [!NOTE]
>  Aunque hay otras implementaciones DE para Transact-SQL y JScript, VBScript y JScript comparten una única DE.

 A DE funciona con el sistema de operación o intérprete para proporcionar servicios depuración como la evaluación de expresión, los puntos de interrupción y control de ejecución. Estos servicios se implementan a través de las interfaces DE y pueden hacer que al depurador en la transición entre distintos modos de funcionamiento. Para obtener más información, consulte [modos operativos](../../extensibility/debugger/operational-modes.md).

 Creación de una DE consta de los pasos siguientes:

1. Registre un DE con Visual Studio

2. Habilitar un programa que se desea depurar

3. Implementar la evaluación de control y el estado de ejecución

4. Envío de eventos

5. Configuración de terminación y separado

## <a name="in-this-section"></a>En esta sección
 [Registrar un motor de depuración](../../extensibility/debugger/registering-a-custom-debug-engine.md) explica los pasos necesarios para registrar un motor de depuración con Visual Studio para que se puede usar.

 [Habilitar un programa que se desea depurar](../../extensibility/debugger/enabling-a-program-to-be-debugged.md) explica que antes de que la DE poder depurar un programa, primero debe iniciar la DE o adjuntarlo a un programa existente.

 [Implementar la evaluación de control y el estado de ejecución](../../extensibility/debugger/execution-control-and-state-evaluation.md) explica por qué depurar una aplicación requiere la implementación de características de control de ejecución.

 [Enviar eventos](../../extensibility/debugger/sending-events.md) describe la comunicación entre el depurador y la DE como un modelo de eventos en función de DCOM.

 [Configuración de terminación y separado](../../extensibility/debugger/termination-and-detaching.md) explica cómo lograr la terminación normal, lo que significa que no hay ningún puntos de interrupción, excepciones, errores de tiempo de ejecución o bucles infinitos en la aplicación que se desea depurar.

 [Llamar a los eventos del depurador](../../extensibility/debugger/calling-debugger-events.md) documenta el orden de llamada de los eventos que se producen en una sesión de depuración.

 [Cómo: Depurar un motor de depuración](../../extensibility/debugger/how-to-debug-a-custom-debug-engine.md) se explica cómo depurar una personalizada DE.

## <a name="see-also"></a>Vea también
- [Extensibilidad del depurador de Visual Studio](../../extensibility/debugger/visual-studio-debugger-extensibility.md)