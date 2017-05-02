---
title: "IDebugStackFrameSnifferEx (Interfaz) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IDebugStackFrameSnifferEx (interfaz)"
ms.assetid: fd6cf744-dee7-45f2-9a90-355b90372923
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugStackFrameSnifferEx (Interfaz)
Proporciona una manera de mostrar los marcos de pila lógicos conocidos por un componente.  Los motores de scripts implementan normalmente esta interfaz.  El administrador de la depuración utiliza esta interfaz para buscar todos los marcos de pila asociados a un subproceso determinado.  
  
> [!NOTE]
>  Esta interfaz se llama en el subproceso de interés.  La implementación de la interfaz debe identificar el subproceso actual y devolver un enumerador adecuado.  
  
 Además de los métodos heredados de `IDebugStackFrameSniffer`, la interfaz `IDebugStackFrameSnifferEx` expone los métodos siguientes.  
  
## métodos en el orden de Vtable  
  
|Método|Descripción|  
|------------|-----------------|  
|[IDebugStackFrameSnifferEx::EnumStackFramesEx](../../winscript/reference/idebugstackframesnifferex-enumstackframesex.md)|Devuelve un enumerador de los marcos de pila del subproceso actual.|