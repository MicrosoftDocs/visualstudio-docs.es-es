---
title: Creación de un archivo de motor de depuración | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- debug engines, implementing
- debug engines, custom
- debugging [Debugging SDK], custom debug engines
ms.assetid: 52794238-6fae-451c-bf1c-99f344c6f173
caps.latest.revision: 16
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: f071d15b0900fb256fba02502b2e31e72ad2222a
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47567752"
---
# <a name="creating-a-custom-debug-engine"></a>Creación de un motor de depuración personalizado
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [creación de un motor de depuración personalizado](https://docs.microsoft.com/visualstudio/extensibility/debugger/creating-a-custom-debug-engine).  
  
Un motor de depuración (DE) es un componente que permite la depuración de las arquitecturas de tiempo de ejecución determinadas. Normalmente hay solo una implementación DE cada entorno de tiempo de ejecución.  
  
> [!NOTE]
>  Aunque hay otras implementaciones DE para Transact-SQL y JScript, VBScript y JScript comparten una única DE.  
  
 A DE funciona con el sistema de operación o intérprete para proporcionar servicios depuración como la evaluación de expresión, los puntos de interrupción y control de ejecución. Estos servicios se implementan a través de las interfaces DE y pueden hacer que al depurador en la transición entre distintos modos de funcionamiento. Para obtener más información, consulte [modos operativos](../../extensibility/debugger/operational-modes.md).  
  
 Creación de una DE consta de los pasos siguientes:  
  
1.  Registrar un DE con Visual Studio  
  
2.  Habilitación de un programa que se desea depurar  
  
3.  Evaluación de control y el estado de ejecución  
  
4.  Envío de eventos  
  
5.  Terminación y separado  
  
## <a name="in-this-section"></a>En esta sección  
 [Registro de un motor de depuración personalizado](../../extensibility/debugger/registering-a-custom-debug-engine.md)  
 Explica los pasos necesarios para registrar un motor de depuración con Visual Studio para que se puede usar.  
  
 [Habilitación de un programa que se desea depurar](../../extensibility/debugger/enabling-a-program-to-be-debugged.md)  
 Se explica que antes de que la DE poder depurar un programa, primero debe iniciar la DE o adjuntarlo a un programa existente.  
  
 [Control de ejecución y evaluación de estado](../../extensibility/debugger/execution-control-and-state-evaluation.md)  
 Describe por qué depurar una aplicación requiere la implementación de características de control de ejecución.  
  
 [Envío de eventos](../../extensibility/debugger/sending-events.md)  
 Se describe la comunicación entre el depurador y la DE como un modelo de eventos en función de DCOM.  
  
 [Terminación y separado](../../extensibility/debugger/termination-and-detaching.md)  
 Explica cómo lograr la terminación normal, lo que significa que no hay ningún puntos de interrupción, excepciones, errores de tiempo de ejecución o bucles infinitos en la aplicación que se desea depurar.  
  
 [Llamada a eventos del depurador](../../extensibility/debugger/calling-debugger-events.md)  
 Documenta el orden de llamada de los eventos que se producen en una sesión de depuración.  
  
 [Depuración de un motor de depuración personalizado](../../extensibility/debugger/how-to-debug-a-custom-debug-engine.md)  
 Explica cómo depurar una personalizada DE.  
  
## <a name="see-also"></a>Vea también  
 [Extensibilidad del depurador de Visual Studio](../../extensibility/debugger/visual-studio-debugger-extensibility.md)

