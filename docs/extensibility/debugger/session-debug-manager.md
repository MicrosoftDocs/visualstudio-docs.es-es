---
title: "Administrador de depuraci&#243;n de sesi&#243;n | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Administrador de depuración de sesión, Unifique vistas de sesión"
  - "Administrador de depuración de sesión, de difusión"
  - "depurar [SDK de depuración], el Administrador de depuración de sesión"
  - "Administrador de sesión de depuración"
  - "Administrador de depuración de la sesión, multiplexación de motor de depuración"
  - "Administrador de depuración de sesión, delegar"
ms.assetid: fbb1928d-dddc-43d1-98a4-e23b0ecbae09
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# Administrador de depuraci&#243;n de sesi&#243;n
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

El administrador de depuración de la sesión \(SDM\) controla cualquier número de motores de depuración \(DE\) de depuración cualquier número de programas en varios procesos en cualquier número de equipos.  Además de ser un multiplexor del motor de depuración, el SDM proporciona una vista unificada la sesión de depuración al IDE.  
  
## Operación de administrador de depuración de sesión  
 El administrador de depuración de la sesión \(SDM\) controla el OF.  Puede haber más de una ejecución del motor de depuración en un equipo.  Para multiplexar el DES, los ajustes de SDM varias interfaces de DES y los exponen al IDE como una interfaz.  
  
 Para aumentar el rendimiento, algunas interfaces no se multiplexan.  En su lugar, se utilizan directamente de, y las llamadas a estas interfaces no pasan con el SDM.  Por ejemplo, las interfaces utilizadas con memoria, código, y contextos de documento no se multiplexan, ya que hacen referencia a una instrucción, en memoria, o un documento específica en un programa concreto depura por un OF concreto.  Ningún otro OF debe estar implicado en ese nivel de comunicación.  
  
 Esto no se aplica a todos los contextos.  Las llamadas a la interfaz del contexto de la evaluación de la expresión pasan con el SDM.  Durante la evaluación de la expresión, el SDM contiene la interfaz de [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) que da al IDE porque cuando se evalúa la expresión, puede incluir el DES múltiple que está depurando programas en el mismo proceso que se ejecute en el mismo subproceso.  
  
 El SDM actúa normalmente como mecanismo de delegación, pero podría representar como mecanismo de difusión.  Por ejemplo, durante la evaluación de la expresión, el SDM actúa como mecanismo de difusión para notificar todo el DES que puede ejecutar código en un subproceso especificado.  De igual forma, cuando el SDM recibe un evento que se detiene, se propaga a todos los programas que debe dejar de ejecutarse.  Cuando se llama a un paso, las difusiones de SDM todos los programas que pueden continuar ejecutándose.  Los puntos de interrupción también se propagan a cada OF.  
  
 El SDM no sigue el programa actual, el subproceso, o marco de pila.  El proceso, el programa, y la información del subproceso se envía al SDM junto con los eventos específicos de depuración.  
  
## Vea también  
 [Motor de depuración](../../extensibility/debugger/debug-engine.md)   
 [Componentes del depurador](../../extensibility/debugger/debugger-components.md)   
 [Contextos de depurador](../../extensibility/debugger/debugger-contexts.md)