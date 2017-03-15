---
title: "Descripciones de eventos | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "depurar [SDK de depuración], eventos"
ms.assetid: 09f61652-7e16-4bb0-8055-f61a84bf384e
caps.latest.revision: 7
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 7
---
# Descripciones de eventos
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Cada tipo de evento tiene un propósito concreto.  
  
## Eventos y los Motivos para el uso de Su  
  
|Evento|Descripción|  
|------------|-----------------|  
|Provoca eventos de documento|Aparece cuando el motor de depuración \(DE\) desea el IDE para abrir o para poner un documento en primer plano.|  
|Límite del punto de interrupción o eventos de error de punto de interrupción|Enviado cuando se enlaza un punto de interrupción o a un punto de interrupción no puede enlazar y se devuelve un error.|  
|Eventos independientes de punto de interrupción|Aparece cuando un punto de interrupción enlazado desata de código.|  
|puede detener eventos|Enviado al IDE para determinar si el usuario desea detener en un punto especificado en código.|  
|Eventos de punto de interrupción|Aparece cuando un punto de interrupción de código o de los datos se alcance.|  
|Eventos de texto del documento|Aparece cuando el texto en un documento cambia.  estos eventos no se envían con el método de `IDebugEventCallBack2::Event` .|  
|el motor crea eventos|Enviado cuando un motor se crea por primera vez.|  
|Eventos de punto de entrada|Enviado al programa que se depura ha ejecutado el código de inicialización y ha alcanzado el primer punto de entrada de usuario.|  
|Eventos de excepción|Enviado cuando un programa en ejecución alcanza una excepción.|  
|Eventos completos evaluación de expresiones|Enviado cuando la evaluación asincrónica de la expresión.|  
|eventos de Buscar símbolo|Enviado siempre que el OF necesite pedir al usuario encuentre los símbolos para un módulo.|  
|Eventos completos carga|Enviado cuando se haya completado la carga de programas inicial y el primer código está a punto de ejecutarse en el programa.|  
|Eventos de mensaje|enviado cuando los mensajes se envían a los usuarios.|  
|Eventos de carga de módulos|Enviado cuando un nuevo módulo se carga o descargado.|  
|eventos de la cadena de salida|Enviado cuando escribe de programa de la salida.|  
|Crear y destruir los eventos|Enviados para anunciar la creación o destrucción de los procesos, programas, las propiedades, sesiones y subprocesos para que el IDE de Visual Studio puede hacer un seguimiento del estado de los programas que se están depurando.|  
|Eventos completos paso|enviado cuando se completa un paso.|  
|Eventos de cambio de nombre de subproceso|enviado cuando el usuario cambia el nombre de un subproceso.|  
|Eventos de cambio de nombre de programa|enviado cuando el usuario cambia el nombre de un programa.|  
  
## Vea también  
 [Enviar eventos](../../extensibility/debugger/sending-events.md)