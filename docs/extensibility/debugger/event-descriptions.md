---
title: Descripciones de eventos | Microsoft Docs
description: Obtenga información sobre los tipos de eventos y los motivos para su uso. Cada tipo de evento tiene un propósito específico.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], events
ms.assetid: 09f61652-7e16-4bb0-8055-f61a84bf384e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ea477d3d21cd3b7a1a5352c736dc2f78195b99a4
ms.sourcegitcommit: 8e9c38da7bcfbe9a461c378083846714933a0e1e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/09/2020
ms.locfileid: "96915614"
---
# <a name="event-descriptions"></a>Descripciones de eventos
Cada tipo de evento tiene un propósito específico.

## <a name="events-and-the-reasons-for-their-use"></a>Eventos y motivos para su uso

|Evento|Descripción|
|-----------|-----------------|
|Activar eventos de documento|Se produce cuando el motor DE depuración (DE) desea que el IDE abra o ponga un documento en primer plano.|
|Eventos de error de punto de interrupción o de punto de interrupción|Se envía cuando se enlaza un punto de interrupción o cuando no se puede enlazar un punto de interrupción y se devuelve un error.|
|Eventos sin enlazar de puntos de interrupción|Se produce cuando un punto de interrupción enlazado se desenlaza del código.|
|Puede detener eventos|Se envía al IDE para determinar si el usuario desea detenerse en un punto especificado del código.|
|Eventos de punto de interrupción|Se produce cuando se alcanza un punto de interrupción de código o de datos.|
|Eventos de texto de documento|Se produce cuando se cambia el texto de un documento. Estos eventos no se envían a través del `IDebugEventCallBack2::Event` método.|
|Eventos de creación del motor|Se envía cuando se crea un motor por primera vez.|
|Eventos de punto de entrada|Se envía cuando el programa que se está depurando ejecuta el código de inicialización y llegó a su primer punto de entrada del usuario.|
|Eventos de excepción|Se envía cuando un programa en ejecución alcanza una excepción.|
|Eventos de evaluación de expresión completa|Se envía cuando se completa la evaluación de expresiones asincrónicas.|
|Buscar eventos de símbolos|Se envía siempre que el DE necesita pedir al usuario que busque símbolos para un módulo.|
|Eventos de carga completada|Se envía solo cuando se completa la carga inicial del programa y el primer código está a punto de ejecutarse en el programa.|
|Eventos de mensaje|Se envía cuando se envían mensajes a los usuarios.|
|Eventos de carga de módulo|Se envía cuando se carga o descarga un nuevo módulo.|
|Eventos de cadena de salida|Se envía cuando el programa escribe la salida de depuración.|
|Crear y destruir eventos|Se envía para anunciar la creación o destrucción de procesos, programas, propiedades, sesiones y subprocesos para que el IDE de Visual Studio pueda realizar un seguimiento del estado de los programas que se están depurando.|
|Eventos de paso completo|Se envía cuando se completa un paso.|
|Eventos de cambio de nombre de subproceso|Se envía cuando el usuario cambia el nombre de un subproceso.|
|Eventos de cambio de nombre de programa|Se envía cuando el usuario cambia el nombre de un programa.|

## <a name="see-also"></a>Consulte también
- [Envío de eventos](../../extensibility/debugger/sending-events.md)
