---
title: Las descripciones de evento | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], events
ms.assetid: 09f61652-7e16-4bb0-8055-f61a84bf384e
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7267011c61a3b43c76db80a758a86f1af1dd228b
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/29/2019
ms.locfileid: "66315359"
---
# <a name="event-descriptions"></a>Descripciones de evento
Cada tipo de evento tiene un propósito específico.

## <a name="events-and-the-reasons-for-their-use"></a>Eventos y los motivos para su uso

|evento|Descripción|
|-----------|-----------------|
|Activar eventos de documentos|Se producen cuando el motor de depuración (DE) desea el IDE para abrir o recuperar un documento al primer plano.|
|Evento de error de punto de interrupción o punto de interrupción enlazado|Se envía cuando se enlaza a un punto de interrupción o cuando no se puede enlazar a un punto de interrupción y se devuelve un error.|
|Eventos de punto de interrupción no enlazado|Se producen cuando se desenlaza un punto de interrupción enlazado desde el código.|
|Puede dejar de eventos|Envía el IDE para determinar si el usuario desea detener en un punto especificado en el código.|
|Eventos de punto de interrupción|Se producen cuando se alcanza un punto de interrupción de datos o código.|
|Eventos de texto del documento|Se producen cuando se cambia el texto en un documento. Estos eventos no se envían a través de la `IDebugEventCallBack2::Event` método.|
|Motor de creación de eventos|Se envía cuando se crea por primera vez un motor.|
|Eventos de punto de entrada|Se envía cuando el programa que se está depurando ha ejecutar su código de inicialización y alcanza su primer punto de entrada de usuario.|
|Eventos de excepción|Se envía cuando un programa en ejecución produce una excepción.|
|Eventos de finalización de evaluación de expresión|Envía una vez completada la evaluación de expresiones asincrónicas.|
|Buscar eventos de símbolos|Envía cada vez que la DE debe preguntar al usuario a encontrar los símbolos para un módulo.|
|Eventos de carga completados|Envía solo cuando se complete la carga inicial del programa y el primer código está a punto de ejecutarse en el programa.|
|Eventos de mensajes|Se envía cuando se envían mensajes a los usuarios.|
|Eventos del módulo de carga|Se envía cuando se carga o descarga un módulo nuevo.|
|Eventos de la cadena de salida|Se envía cuando el programa escribe la salida de depuración.|
|Crear y destruir los eventos|Envía de anunciar la creación o la destrucción de subprocesos, programas, propiedades, sesiones y procesos para el IDE de Visual Studio puede realizar un seguimiento del estado de los programas que se está depurando.|
|Eventos de finalización del paso|Se envía cuando se completa un paso.|
|Eventos de cambio de nombre de subproceso|Se envía cuando el usuario cambia el nombre de un subproceso.|
|Eventos de cambio de nombre de programa|Se envía cuando el usuario cambia el nombre de un programa.|

## <a name="see-also"></a>Vea también
- [Envío de eventos](../../extensibility/debugger/sending-events.md)