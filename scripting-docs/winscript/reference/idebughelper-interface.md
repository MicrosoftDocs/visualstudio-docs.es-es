---
title: "IDebugHelper (Interfaz) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IDebugHelper (interfaz)"
ms.assetid: ef5691e0-1d82-42c2-997c-888e31c478dd
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugHelper (Interfaz)
Servicios como generador para los examinadores de objetos y los puntos de conexión simples.  El administrador de proceso \(PDM\) de depuración implementa esta interfaz, que es utilizada por los motores de scripts.  
  
 Además de los métodos heredados de `IUnknown`, la interfaz `IDebugHelper` expone los métodos siguientes.  
  
## métodos en el orden de Vtable  
  
|Método|Descripción|  
|------------|-----------------|  
|[IDebugHelper::CreatePropertyBrowser](../../winscript/reference/idebughelper-createpropertybrowser.md)|Devuelve un explorador de propiedades que ajuste de VARIANT.|  
|[IDebugHelper::CreatePropertyBrowserEx](../../winscript/reference/idebughelper-createpropertybrowserex.md)|Devuelve un explorador de propiedades que ajuste de VARIANT, y permite la conversión personalizada de valores VARIANT o VARTYPE escribe en cadenas.|  
|[IDebugHelper::CreateSimpleConnectionPoint](../../winscript/reference/idebughelper-createsimpleconnectionpoint.md)|Devuelve una interfaz de eventos que contenga un objeto determinado de `IDispatch` .|