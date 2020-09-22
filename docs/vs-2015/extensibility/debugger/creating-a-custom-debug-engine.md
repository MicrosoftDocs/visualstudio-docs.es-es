---
title: Crear un motor de depuración personalizado | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debug engines, implementing
- debug engines, custom
- debugging [Debugging SDK], custom debug engines
ms.assetid: 52794238-6fae-451c-bf1c-99f344c6f173
caps.latest.revision: 16
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: b2a73dfae7772d8edec076238704aa1b52c9b028
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "90843166"
---
# <a name="creating-a-custom-debug-engine"></a>Creación de un motor de depuración personalizado
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Un motor de depuración (DE) es un componente que permite depurar determinadas arquitecturas en tiempo de ejecución. Normalmente solo hay una implementación DE para cada entorno en tiempo de ejecución.  
  
> [!NOTE]
> Aunque hay implementaciones independientes de para Transact-SQL y JScript, VBScript y JScript comparten un único DE.  
  
 Una DE funciona con el intérprete o el sistema operativo para proporcionar servicios de depuración como control de la ejecución, puntos de interrupción y evaluación de expresiones. Estos servicios se implementan a través DE las interfaces DE y pueden hacer que el depurador pase de un modo operativo a otro. Para obtener más información, vea [modos operativos](../../extensibility/debugger/operational-modes.md).  
  
 La creación de un DE consta de los siguientes pasos:  
  
1. Registrar un DE con Visual Studio  
  
2. Habilitar la depuración de un programa  
  
3. Control de ejecución y evaluación del estado  
  
4. Envío de eventos  
  
5. Terminación y desasociación  
  
## <a name="in-this-section"></a>En esta sección  
 [Registro de un motor de depuración personalizado](../../extensibility/debugger/registering-a-custom-debug-engine.md)  
 Explica los pasos necesarios para registrar un motor de depuración con Visual Studio para que se pueda usar.  
  
 [Habilitación de un programa que se va a depurar](../../extensibility/debugger/enabling-a-program-to-be-debugged.md)  
 Explica que antes DE que el DE pueda depurar un programa, primero debe iniciar el DE o adjuntarlo a un programa existente.  
  
 [Control de ejecución y evaluación de estado](../../extensibility/debugger/execution-control-and-state-evaluation.md)  
 Describe por qué la depuración de una aplicación requiere la implementación de características de control de ejecución.  
  
 [Enviar eventos](../../extensibility/debugger/sending-events.md)  
 Describe la comunicación entre el depurador y el DE como un modelo de eventos basado en DCOM.  
  
 [Terminación y desasociación](../../extensibility/debugger/termination-and-detaching.md)  
 Explica cómo lograr la terminación normal, lo que significa que no hay puntos de interrupción, excepciones, errores en tiempo de ejecución ni bucles infinitos en la aplicación que se va a depurar.  
  
 [Llamada a eventos del depurador](../../extensibility/debugger/calling-debugger-events.md)  
 Documenta el orden de llamada de los eventos que se producen en una sesión de depuración.  
  
 [Cómo: Depurar un motor de depuración personalizado](../../extensibility/debugger/how-to-debug-a-custom-debug-engine.md)  
 Explica cómo depurar un personalizado DE.  
  
## <a name="see-also"></a>Consulte también  
 [Extensibilidad del depurador de Visual Studio](../../extensibility/debugger/visual-studio-debugger-extensibility.md)
