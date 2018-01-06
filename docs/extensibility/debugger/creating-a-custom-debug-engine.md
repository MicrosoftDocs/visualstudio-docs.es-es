---
title: Crear un personalizado depurar motor | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- debug engines, implementing
- debug engines, custom
- debugging [Debugging SDK], custom debug engines
ms.assetid: 52794238-6fae-451c-bf1c-99f344c6f173
caps.latest.revision: "15"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 0edee6528919cfe28c542be850b9a104188ce403
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="creating-a-custom-debug-engine"></a>Creación de un motor de depuración personalizadas
Un motor de depuración (Alemania) es un componente que permite la depuración de arquitecturas de tiempo de ejecución determinadas. Normalmente hay sólo una implementación DE por cada entorno de tiempo de ejecución.  
  
> [!NOTE]
>  Si bien hay implementaciones DE independientes para Transact-SQL y JScript, VBScript y JScript comparten un único DE.  
  
 Un Alemania funciona con el sistema de operación o intérprete para proporcionar servicios depuración como la evaluación de expresión, control y los puntos de interrupción de ejecución. Estos servicios se implementan a través de las interfaces de Alemania y pueden hacer que el depurador para la transición entre distintos modos de funcionamiento. Para obtener más información, consulte [modos de funcionamiento](../../extensibility/debugger/operational-modes.md).  
  
 Creación de una DE consta de los siguientes pasos:  
  
1.  Registrar un Alemania con Visual Studio  
  
2.  Habilitar un programa que se va a depurar  
  
3.  Evaluación de control y el estado de ejecución  
  
4.  El envío de eventos  
  
5.  Separar y terminación  
  
## <a name="in-this-section"></a>En esta sección  
 [Registro de un motor de depuración personalizado](../../extensibility/debugger/registering-a-custom-debug-engine.md)  
 Explica los pasos necesarios para registrar un motor de depuración con Visual Studio para que se puede utilizar.  
  
 [Habilitación de un programa que se desea depurar](../../extensibility/debugger/enabling-a-program-to-be-debugged.md)  
 Explica que antes de su Alemania puede depurar un programa, primero debe iniciar el Alemania o adjuntar a un programa existente.  
  
 [Control de ejecución y evaluación de estado](../../extensibility/debugger/execution-control-and-state-evaluation.md)  
 Describe por qué depurar una aplicación requiere la implementación de características de control de ejecución.  
  
 [Envío de eventos](../../extensibility/debugger/sending-events.md)  
 Describe la comunicación entre el depurador y la DE como un modelo de eventos basado en DCOM.  
  
 [Terminación y separado](../../extensibility/debugger/termination-and-detaching.md)  
 Explica cómo lograr la terminación normal, lo que significa que no haya puntos de interrupción, excepciones, errores en tiempo de ejecución ni bucles infinitos en la aplicación que desea depurar.  
  
 [Llamada a eventos del depurador](../../extensibility/debugger/calling-debugger-events.md)  
 Documenta el orden de llamada de los eventos que se producen en una sesión de depuración.  
  
 [Depuración de un motor de depuración personalizado](../../extensibility/debugger/how-to-debug-a-custom-debug-engine.md)  
 Explica cómo depurar un Alemania personalizado.  
  
## <a name="see-also"></a>Vea también  
 [Extensibilidad del depurador de Visual Studio](../../extensibility/debugger/visual-studio-debugger-extensibility.md)