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
ms.openlocfilehash: aff0f3ba1bef25c7754f80dcbb6fb04e2e7da60e
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/25/2019
ms.locfileid: "55029913"
---
# <a name="create-a-custom-debug-engine"></a>Crear un motor de depuración personalizado
Un motor de depuración (DE) es un componente que permite la depuración de las arquitecturas de tiempo de ejecución determinadas. Normalmente hay solo una implementación DE cada entorno de tiempo de ejecución.  
  
> [!NOTE]
>  Aunque hay otras implementaciones DE para Transact-SQL y JScript, VBScript y JScript comparten una única DE.  
  
 A DE funciona con el sistema de operación o intérprete para proporcionar servicios depuración como la evaluación de expresión, los puntos de interrupción y control de ejecución. Estos servicios se implementan a través de las interfaces DE y pueden hacer que al depurador en la transición entre distintos modos de funcionamiento. Para obtener más información, consulte [modos operativos](../../extensibility/debugger/operational-modes.md).  
  
 Creación de una DE consta de los pasos siguientes:  
  
1.  Registre un DE con Visual Studio  
  
2.  Habilitar un programa que se desea depurar  
  
3.  Implementar la evaluación de control y el estado de ejecución  
  
4.  Envío de eventos  
  
5.  Configuración de terminación y separado  
  
## <a name="in-this-section"></a>En esta sección  
 [Registrar un motor de depuración personalizado](../../extensibility/debugger/registering-a-custom-debug-engine.md)  
 Explica los pasos necesarios para registrar un motor de depuración con Visual Studio para que se puede usar.  
  
 [Habilitar un programa que se desea depurar](../../extensibility/debugger/enabling-a-program-to-be-debugged.md)  
 Se explica que antes de que la DE poder depurar un programa, primero debe iniciar la DE o adjuntarlo a un programa existente.  
  
 [Implementar la evaluación de control y el estado de ejecución](../../extensibility/debugger/execution-control-and-state-evaluation.md)  
 Describe por qué depurar una aplicación requiere la implementación de características de control de ejecución.  
  
 [Envío de eventos](../../extensibility/debugger/sending-events.md)  
 Se describe la comunicación entre el depurador y la DE como un modelo de eventos en función de DCOM.  
  
 [Configuración de terminación y separado](../../extensibility/debugger/termination-and-detaching.md)  
 Explica cómo lograr la terminación normal, lo que significa que no hay ningún puntos de interrupción, excepciones, errores de tiempo de ejecución o bucles infinitos en la aplicación que se desea depurar.  
  
 [Llamar a los eventos del depurador](../../extensibility/debugger/calling-debugger-events.md)  
 Documenta el orden de llamada de los eventos que se producen en una sesión de depuración.  
  
 [Cómo: Depurar un motor de depuración personalizado](../../extensibility/debugger/how-to-debug-a-custom-debug-engine.md)  
 Explica cómo depurar una personalizada DE.  
  
## <a name="see-also"></a>Vea también  
 [Extensibilidad del depurador de Visual Studio](../../extensibility/debugger/visual-studio-debugger-extensibility.md)