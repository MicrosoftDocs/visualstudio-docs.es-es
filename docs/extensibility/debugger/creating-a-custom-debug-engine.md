---
title: "Creaci&#243;n de un motor de depuraci&#243;n | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "motores de depuración, implementación"
  - "motores de depuración, personalizado"
  - "depurar [SDK de depuración], motores de depuración personalizados"
ms.assetid: 52794238-6fae-451c-bf1c-99f344c6f173
caps.latest.revision: 15
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 15
---
# Creaci&#243;n de un motor de depuraci&#243;n
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Un motor de depuración \(DE\) es un componente que permite la depuración de las arquitecturas concretas en tiempo de ejecución.  Normalmente hay sólo un OF implementation el entorno en tiempo de ejecución.  
  
> [!NOTE]
>  Cuando hay OF independiente implementations para Transact\-SQL y JScript, VBScript y JScript comparten un único OF.  
  
 Un OF ejecuta el intérprete o el sistema de la operación para proporcionar servicios tales de depuración como el control de ejecución, los puntos de interrupción, y la evaluación de la expresión.  Estos servicios se implementan a través de interfaces y pueden producir el depurador para la transición entre distintos modos operativos.  Para obtener más información, vea [Modos de funcionamiento](../../extensibility/debugger/operational-modes.md).  
  
 Crear un OF consta de los pasos siguientes:  
  
1.  Registrar un OF con Visual Studio  
  
2.  Habilitar un programa que se va a depurar  
  
3.  Control de ejecución y evaluación de estado  
  
4.  envío de eventos  
  
5.  Finalización y la desasociación  
  
## En esta sección  
 [Registrar un motor de depuración](../../extensibility/debugger/registering-a-custom-debug-engine.md)  
 Explica los pasos necesarios para registrar un motor de depuración con Visual Studio para que se pueda utilizar.  
  
 [Habilitación de un programa que se desea depurar](../../extensibility/debugger/enabling-a-program-to-be-debugged.md)  
 Explica antes del OF pueda depurar un programa, primero debe iniciar el OF o adjuntarlo a un programa existente.  
  
 [Control de ejecución y evaluación de estado](../../extensibility/debugger/execution-control-and-state-evaluation.md)  
 Explica por qué depurar una aplicación requiere implementar características de control de la ejecución.  
  
 [Enviar eventos](../../extensibility/debugger/sending-events.md)  
 Describe la comunicación entre el depurador y el OF como modelo de eventos basado en DCOM.  
  
 [Separar y terminación](../../extensibility/debugger/termination-and-detaching.md)  
 Explica cómo lograr la terminación normal, lo que significa que no hay puntos de interrupción, excepciones, errores en tiempo de ejecución, o los bucles sin fin en la aplicación para depurar.  
  
 [Llamar a eventos del depurador](../../extensibility/debugger/calling-debugger-events.md)  
 Documenta el orden de llamada de los eventos que se producen en una sesión de depuración.  
  
 [Cómo: Depurar un motor de depuración](../../extensibility/debugger/how-to-debug-a-custom-debug-engine.md)  
 Explica cómo depurar una personalizada OF.  
  
## Vea también  
 [Extensibilidad del depurador de Visual Studio](../../extensibility/debugger/visual-studio-debugger-extensibility.md)