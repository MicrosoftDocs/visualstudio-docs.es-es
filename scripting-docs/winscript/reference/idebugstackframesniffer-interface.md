---
title: "IDebugStackFrameSniffer (Interfaz) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IDebugStackFrameSniffer (interfaz)"
ms.assetid: 5669598e-a6bd-4694-9cb2-bd908be72bed
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugStackFrameSniffer (Interfaz)
Proporciona una manera de mostrar los marcos de pila lógicos conocidos por un componente.  Los motores de scripts implementan normalmente esta interfaz.  El administrador de la depuración utiliza esta interfaz para buscar todos los marcos de pila asociados a un subproceso determinado.  
  
> [!NOTE]
>  El depurador llama a esta interfaz en el subproceso de interés.  El motor de scripts debe identificar el subproceso actual y devolver un enumerador adecuado.  
  
## Métodos  
 Además de los métodos heredados de `IUnknown`, la interfaz `IDebugStackFrameSniffer` expone los métodos siguientes.  
  
|Método|Descripción|  
|------------|-----------------|  
|[IDebugStackFrameSniffer::EnumStackFrames](../../winscript/reference/idebugstackframesniffer-enumstackframes.md)|Devuelve un enumerador de los marcos de pila del subproceso actual.|