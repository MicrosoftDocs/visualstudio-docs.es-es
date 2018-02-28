---
title: Descripciones de eventos | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- debugging [Debugging SDK], events
ms.assetid: 09f61652-7e16-4bb0-8055-f61a84bf384e
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 6ec084c0d985ce5cc3cb0a886bd1fdcaf6cc3e54
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="event-descriptions"></a>Descripciones de eventos
Cada tipo de evento tiene un propósito específico.  
  
## <a name="events-and-the-reasons-for-their-use"></a>Eventos y los motivos para su uso  
  
|evento|Descripción|  
|-----------|-----------------|  
|Activar eventos de documento|Se producen cuando el motor de depuración (Alemania) desea el IDE para abrir o poner un documento al primer plano.|  
|Punto de interrupción enlazado o eventos de error de punto de interrupción|Enviar cuando se enlaza a un punto de interrupción o cuando no se puede enlazar a un punto de interrupción y se devuelve un error.|  
|Eventos de punto de interrupción sin enlazar|Se producen cuando un punto de interrupción enlazado desenlaza desde el código.|  
|Puede detener eventos|Envía el IDE para determinar si el usuario desea detener en un punto especificado en el código.|  
|Eventos de punto de interrupción|Se producen cuando se alcanza un punto de interrupción de código o datos.|  
|Eventos de texto del documento|Se producen cuando se cambia el texto de un documento. Estos eventos no se envían a través de la `IDebugEventCallBack2::Event` método.|  
|Motor de crear eventos|Se envía cuando se crea por primera vez un motor.|  
|Eventos de punto de entrada|Se envía cuando el programa que se está depurando haya ejecutado el código de inicialización y alcanza su primer punto de entrada de usuario.|  
|Eventos de excepción|Se envía cuando un programa en ejecución produce una excepción.|  
|Eventos completados de la evaluación de expresión|Envía una vez completada la evaluación de expresiones asincrónica.|  
|Buscar eventos de símbolos|Se envía siempre que la DE debe pedir al usuario que buscar símbolos para un módulo.|  
|Eventos de carga finalizada|Envía solo cuando se complete la carga de programa inicial y el primer código está a punto de ejecutarse en el programa.|  
|Eventos de mensajes|Se envía cuando se envían mensajes a los usuarios.|  
|Eventos del módulo de carga|Enviar cuando se carga o descarga un nuevo módulo.|  
|Eventos de la cadena de salida|Se envía cuando el programa escribe la salida de depuración.|  
|Crear y destruir eventos|Envía a anunciar la creación o la destrucción de procesos, programas, propiedades, las sesiones y los subprocesos, por lo que el IDE de Visual Studio puede realizar un seguimiento del estado de los programas que se está depurando.|  
|Eventos complete de paso|Se envía cuando se completa un paso.|  
|Eventos de cambio de nombre de subprocesos|Se envía cuando el usuario cambia el nombre de un subproceso.|  
|Eventos de cambio de nombre de programa|Se envía cuando el usuario cambia el nombre de un programa.|  
  
## <a name="see-also"></a>Vea también  
 [Envío de eventos](../../extensibility/debugger/sending-events.md)