---
title: Descripciones de los eventos ? Microsoft Docs
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
ms.openlocfilehash: 3c2582717fd4da3b833da90a951f9b8f72a59f71
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738792"
---
# <a name="event-descriptions"></a>Descripciones de eventos
Cada tipo de evento tiene un propósito específico.

## <a name="events-and-the-reasons-for-their-use"></a>Eventos y las razones de su uso

|Evento|Descripción|
|-----------|-----------------|
|Activar eventos de documentos|Se produce cuando el motor de depuración (DE) desea que el IDE abra o lleve un documento al primer plano.|
|Eventos de error de punto de interrupción o de punto de interrupción|Se envía cuando se enlaza un punto de interrupción o cuando un punto de interrupción no se puede enlazar y se devuelve un error.|
|Eventos sin enlazar punto de interrupción|Se produce cuando un punto de interrupción enlazado se desenlaza del código.|
|Puede detener eventos|Se envía al IDE para determinar si el usuario desea detenerse en un punto especificado en el código.|
|Eventos de punto de interrupción|Se produce cuando se alcanza un punto de interrupción de datos o código.|
|Eventos de texto del documento|Se produce cuando se cambia el texto de un documento. Estos eventos no se `IDebugEventCallBack2::Event` envían a través del método.|
|El motor crea eventos|Se envía cuando se crea un motor por primera vez.|
|Eventos de punto de entrada|Se envía cuando el programa que se está depurando ha ejecutado su código de inicialización y ha alcanzado su primer punto de entrada de usuario.|
|Eventos de excepción|Se envía cuando un programa en ejecución alcanza una excepción.|
|Evaluación de expresiones eventos completos|Se envía cuando se completa la evaluación de expresiones asincrónicas.|
|Buscar eventos de símbolo|Se envía siempre que el DE necesita pedir al usuario que encuentre símbolos para un módulo.|
|Cargar eventos completos|Se envía solo cuando se completa la carga inicial del programa y el primer código está a punto de ejecutarse en el programa.|
|Eventos de mensajes|Se envía cuando se envían mensajes a los usuarios.|
|Eventos de carga de módulos|Se envía cuando se carga o descarga un nuevo módulo.|
|Eventos de cadena de salida|Se envía cuando el programa escribe la salida de depuración.|
|Crear y destruir eventos|Se envía para anunciar la creación o destrucción de procesos, programas, propiedades, sesiones y subprocesos para que el IDE de Visual Studio pueda realizar un seguimiento del estado de los programas que se están depurando.|
|Eventos completos paso a paso|Se envía cuando se completa un paso.|
|Eventos de cambio de nombre de subproceso|Se envía cuando el usuario cambia el nombre de un subproceso.|
|Eventos de cambio de nombre del programa|Se envía cuando el usuario cambia el nombre de un programa.|

## <a name="see-also"></a>Vea también
- [Envío de eventos](../../extensibility/debugger/sending-events.md)
