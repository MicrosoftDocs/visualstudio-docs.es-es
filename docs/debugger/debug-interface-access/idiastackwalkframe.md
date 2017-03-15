---
title: "IDiaStackWalkFrame | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IDiaStackWalkFrame (interfaz)"
ms.assetid: 42d82845-d6f6-4846-9ecd-9dd169216077
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDiaStackWalkFrame
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Mantiene contexto de pila entre las invocaciones de método de [IDiaFrameData::execute](../../debugger/debug-interface-access/idiaframedata-execute.md) .  
  
## Sintaxis  
  
```  
IDiaStackWalkFrame : IUnknown  
```  
  
## métodos en el orden de Vtable  
 La tabla siguiente se muestran los métodos de `IDiaStackWalkFrame`.  
  
|Método|Descripción|  
|------------|-----------------|  
|[IDiaStackWalkFrame::get\_registerValue](../../debugger/debug-interface-access/idiastackwalkframe-get-registervalue.md)|recupera el valor de un registro.|  
|[IDiaStackWalkFrame::put\_registerValue](../../debugger/debug-interface-access/idiastackwalkframe-put-registervalue.md)|establece el valor de un registro.|  
|[IDiaStackWalkFrame::readMemory](../../debugger/debug-interface-access/idiastackwalkframe-readmemory.md)|memoria de lecturas de la imagen.|  
|[IDiaStackWalkFrame::searchForReturnAddress](../../debugger/debug-interface-access/idiastackwalkframe-searchforreturnaddress.md)|Busca el marco de pila especificado para el remite más próximo de la función.|  
|[IDiaStackWalkFrame::searchForReturnAddressStart](../../debugger/debug-interface-access/idiastackwalkframe-searchforreturnaddressstart.md)|busca el marco de pila especificado para un remite en o cerca de la dirección especificada.|  
  
## Comentarios  
 Esta interfaz se utiliza durante la ejecución del programa en los registros de lectura y escritura así como los remites de memoria y de búsqueda de acceso.  
  
## Notas para los llamadores  
 La aplicación cliente implementa esta interfaz y pasar una instancia de interfaz al método de [IDiaFrameData::execute](../../debugger/debug-interface-access/idiaframedata-execute.md) .  La misma instancia de esta interfaz se utiliza una y otra vez para mantener el estado de los registros durante cada invocación de método de `execute` .  El método de `execute` también utiliza esta interfaz para determinar el de.  
  
## Requisitos  
 encabezado: Dia2.h  
  
 biblioteca: diaguids.lib  
  
 DLL: msdia80.dll  
  
## Vea también  
 [Interfaces \(Debug Interface Access SDK\)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [IDiaFrameData::execute](../../debugger/debug-interface-access/idiaframedata-execute.md)