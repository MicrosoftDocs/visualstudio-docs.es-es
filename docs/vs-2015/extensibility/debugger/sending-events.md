---
title: Envío de eventos | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- debugging [Debugging SDK], sending events
ms.assetid: 064231e7-59b5-4437-8240-a23c0a7ec2a9
caps.latest.revision: 8
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 9099cfe070f3c572823f8aa07a51e4456190f7b6
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/16/2018
ms.locfileid: "51749432"
---
# <a name="sending-events"></a>Envío de eventos
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

El mecanismo para la comunicación entre el depurador y el motor de depuración (DE) es un modelo de eventos en función de DCOM. Los eventos se envían como objetos COM, y cada evento tiene parámetros que especifican lo siguiente:  
  
- La DE que llama el evento.  
  
- Una descripción de lo que sucedió.  
  
- El proceso, el programa y la información de subproceso que identifica el contexto de dónde se produjo el evento. El proceso no se envía para eventos enviados desde un DE.  
  
- El tipo de evento que indica si el evento es sincrónica o asincrónica.  
  
  Todos los eventos de depuración se envían mediante el método [IDebugEventCallback2::Event](../../extensibility/debugger/reference/idebugeventcallback2-event.md).  
  
## <a name="in-this-section"></a>En esta sección  
 [Orígenes de eventos](../../extensibility/debugger/event-sources-visual-studio-sdk.md)  
 Explica los dos orígenes de eventos: el motor de depuración (DE) y la sesión de depuración manager (SDM).  
  
 [Tipos de evento compatibles](../../extensibility/debugger/supported-event-types.md)  
 Describe los tipos de eventos actualmente admitidos: sincrónicas y asincrónicas.  
  
 [Descripciones de eventos](../../extensibility/debugger/event-descriptions.md)  
 Define los eventos y los motivos para su uso.  
  
## <a name="related-sections"></a>Secciones relacionadas  
 [Creación de un motor de depuración personalizado](../../extensibility/debugger/creating-a-custom-debug-engine.md)  
 Describe cómo funciona a DE con el sistema operativo o intérprete para proporcionar servicios de depuración.

