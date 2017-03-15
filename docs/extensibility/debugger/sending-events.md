---
title: "Enviar eventos | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "depurar [SDK de depuración], eventos de envío"
ms.assetid: 064231e7-59b5-4437-8240-a23c0a7ec2a9
caps.latest.revision: 7
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 7
---
# Enviar eventos
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

El mecanismo de comunicación entre el depurador y el motor de depuración \(DE\) es un modelo de eventos basado en DCOM.  Los eventos se envían como objetos COM, y cada evento tiene parámetros que especifican el siguiente:  
  
-   El OF que llamó al evento.  
  
-   Una descripción de lo que ha sucedido.  
  
-   El proceso, el programa, y la información del subproceso que identifica el contexto de donde se produjo el evento.  El proceso no se envía para eventos enviados de un OF.  
  
-   tipo de evento que indica si el evento es sincrónico o asincrónico.  
  
 Todos los eventos de depuración se envían mediante el método [IDebugEventCallback2:: evento](../../extensibility/debugger/reference/idebugeventcallback2-event.md).  
  
## En esta sección  
 [Orígenes de evento](../../extensibility/debugger/event-sources-visual-studio-sdk.md)  
 explica los dos orígenes de eventos: el motor de depuración \(DE\) y la sesión del administrador \(SDM\).  
  
 [tipos de evento admitidos](../../extensibility/debugger/supported-event-types.md)  
 Describe los tipos de evento actualmente compatibles: asincrónico y sincrónico.  
  
 [descripciones de evento](../../extensibility/debugger/event-descriptions.md)  
 Define los eventos y las razones de su uso.  
  
## Secciones relacionadas  
 [Crear un motor de depuración](../../extensibility/debugger/creating-a-custom-debug-engine.md)  
 Describe cómo un OF ejecuta el intérprete o el sistema operativo para proporcionar servicios de depuración.