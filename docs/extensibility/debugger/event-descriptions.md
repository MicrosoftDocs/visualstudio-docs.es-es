---
title: Descripción de eventos | Microsoft Docs
description: Obtenga información sobre los tipos de eventos y las razones de su uso. Cada tipo de evento tiene un propósito específico.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- debugging [Debugging SDK], events
ms.assetid: 09f61652-7e16-4bb0-8055-f61a84bf384e
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: ee2eedac924b3bbd58fac6980da9151a88da9196
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/25/2021
ms.locfileid: "112902649"
---
# <a name="event-descriptions"></a>Descripciones de eventos
Cada tipo de evento tiene un propósito específico.

## <a name="events-and-the-reasons-for-their-use"></a>Eventos y las razones de su uso

|Evento|Descripción|
|-----------|-----------------|
|Activación de eventos de documento|Se produce cuando el motor de depuración (DE) quiere que el IDE abra o lleve un documento al primer plano.|
|Eventos de error de punto de interrupción o límite de punto de interrupción|Se envía cuando se enlaza un punto de interrupción o cuando un punto de interrupción no se puede enlazar y se devuelve un error.|
|Eventos sin enlazar de punto de interrupción|Se produce cuando un punto de interrupción enlazado se desenlazó del código.|
|Puede detener eventos|Se envía al IDE para determinar si el usuario desea detenerse en un punto especificado del código.|
|Eventos de punto de interrupción|Se produce cuando se encuentra un código o un punto de interrupción de datos.|
|Eventos de texto del documento|Se produce cuando se cambia el texto de un documento. Estos eventos no se envían a través del `IDebugEventCallBack2::Event` método .|
|Eventos de creación del motor|Se envía cuando se crea un motor por primera vez.|
|Eventos de punto de entrada|Se envía cuando el programa que se está depurando ha ejecutado su código de inicialización y ha alcanzado su primer punto de entrada de usuario.|
|Eventos de excepción|Se envía cuando un programa en ejecución alcanza una excepción.|
|Eventos completos de evaluación de expresiones|Se envía cuando se completa la evaluación de expresiones asincrónicas.|
|Buscar eventos de símbolos|Se envía siempre que el DE necesita pedir al usuario que busque símbolos para un módulo.|
|Carga de eventos completos|Solo se envía cuando se completa la carga inicial del programa y el primer código está a punto de ejecutarse en el programa.|
|Eventos de mensaje|Se envía cuando se envían mensajes a los usuarios.|
|Eventos de carga de módulos|Se envía cuando se carga o descarga un módulo nuevo.|
|Eventos de cadena de salida|Se envía cuando el programa escribe la salida de depuración.|
|Creación y destrucción de eventos|Se envía para anunciar la creación o destrucción de procesos, programas, propiedades, sesiones y subprocesos para que el IDE de Visual Studio pueda realizar un seguimiento del estado de los programas que se depuran.|
|Eventos de paso completo|Se envía cuando se completa un paso.|
|Eventos de cambio de nombre de subproceso|Se envía cuando el usuario cambia el nombre de un subproceso.|
|Eventos de cambio de nombre de programa|Se envía cuando el usuario cambia el nombre de un programa.|

## <a name="see-also"></a>Consulta también
- [Envío de eventos](../../extensibility/debugger/sending-events.md)
