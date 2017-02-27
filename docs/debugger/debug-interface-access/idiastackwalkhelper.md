---
title: "IDiaStackWalkHelper | Microsoft Docs"
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
  - "IDiaStackWalkHelper2 (interfaz)"
ms.assetid: d66e5c84-565d-494e-8486-f91db9a34548
caps.latest.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 15
---
# IDiaStackWalkHelper
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Facilitates que recorre la pila utilizando el archivo de base de datos de depuración de programa \(.pdb\).  
  
## Sintaxis  
  
```  
  
IDiaStackWalkHelper: IUnknown  
  
```  
  
## métodos en el orden de VTable  
 La tabla siguiente muestra los métodos de `IDiaStackWalkHelper`:  
  
|Método|Descripción|  
|------------|-----------------|  
|[IDiaStackWalkHelper::get\_registerValue](../../debugger/debug-interface-access/idiastackwalkhelper-get-registervalue.md)|recupera el valor de un registro.|  
|[IDiaStackWalkHelper::put\_registerValue](../../debugger/debug-interface-access/idiastackwalkhelper-put-registervalue.md)|establece el valor de un registro.|  
|[IDiaStackWalkHelper::readMemory](../../debugger/debug-interface-access/idiastackwalkhelper-readmemory.md)|Lee un bloque de datos de la imagen del ejecutable en memoria.|  
|[IDiaStackWalkHelper::searchForReturnAddress](../../debugger/debug-interface-access/idiastackwalkhelper-searchforreturnaddress.md)|Busca el marco de pila especificado para el remite más próximo de la función.|  
|[IDiaStackWalkHelper::searchForReturnAddressStart](../../debugger/debug-interface-access/idiastackwalkhelper-searchforreturnaddressstart.md)|busca el marco de pila especificado para un remite en o cerca de la dirección especificada de la pila.|  
|[IDiaStackWalkHelper::frameForVA](../../debugger/debug-interface-access/idiastackwalkhelper-frameforva.md)|Recupera el marco de pila que contiene la dirección virtual especificada.|  
|[IDiaStackWalkHelper::symbolForVA](../../debugger/debug-interface-access/idiastackwalkhelper-symbolforva.md)|Recupera el token que contiene la dirección virtual especificada. **Note:**  El símbolo debe tener el tipo `SymTagFunctionType` \(un valor de enumeración de [SymTagEnum \(Enumeración\)](../../debugger/debug-interface-access/symtagenum.md) \).|  
|[IDiaStackWalkHelper::pdataForVA](../../debugger/debug-interface-access/idiastackwalkhelper-pdataforva.md)|devuelve el bloque de datos de PDATA asociado con la dirección virtual especificada.|  
|[IDiaStackWalkHelper::imageForVA](../../debugger/debug-interface-access/idiastackwalkhelper-imageforva.md)|Recupera la dirección virtual inicial de un ejecutable, dada una dirección virtual en alguna parte del espacio de memoria del ejecutable.|  
  
## Comentarios  
 Esta interfaz es denominada por el código del diámetro para obtener información sobre la aplicación ejecutable para generar una lista de marcos de pila durante la ejecución del programa.  
  
## Notas para los llamadores  
 Una aplicación cliente implementa esta interfaz para admitir recorra la pila durante la ejecución del programa.  una instancia de esta interfaz se pasa a los métodos de [IDiaStackWalker::getEnumFrames](../../debugger/debug-interface-access/idiastackwalker-getenumframes.md) o de [IDiaStackWalker::getEnumFrames2](../../debugger/debug-interface-access/idiastackwalker-getenumframes2.md) .  
  
## Requisitos  
 encabezado: Dia2.h  
  
 biblioteca: diaguids.lib  
  
 DLL: msdia80.dll  
  
## Vea también  
 [Interfaces \(Debug Interface Access SDK\)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)   
 [SymTagEnum \(Enumeración\)](../../debugger/debug-interface-access/symtagenum.md)   
 [IDiaStackWalker::getEnumFrames](../../debugger/debug-interface-access/idiastackwalker-getenumframes.md)   
 [IDiaStackWalker::getEnumFrames2](../../debugger/debug-interface-access/idiastackwalker-getenumframes2.md)