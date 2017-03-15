---
title: "IDiaStackWalker | Microsoft Docs"
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
  - "IDiaStackWalker (interfaz)"
ms.assetid: 4a61a22a-9cf8-4ea1-9e6e-b42f96872d40
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# IDiaStackWalker
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Proporciona métodos para que un recorrido de pila con la información del archivo .pdb.  
  
## Sintaxis  
  
```  
IDiaStackWalker: IUnknown  
```  
  
## métodos en el orden de Vtable  
 La tabla siguiente se muestran los métodos de `IDiaStackWalker`.  
  
|Método|Descripción|  
|------------|-----------------|  
|[IDiaStackWalker::getEnumFrames](../../debugger/debug-interface-access/idiastackwalker-getenumframes.md)|Recupera un enumerador del marco de pila para las plataformas x86.|  
|[IDiaStackWalker::getEnumFrames2](../../debugger/debug-interface-access/idiastackwalker-getenumframes2.md)|Recupera un enumerador del marco de pila para un tipo específico de plataforma.|  
  
## Comentarios  
 esta interfaz se utiliza para obtener una lista de marcos de pila para un módulo cargado.  Cada uno de los métodos se pasa un objeto de [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md) \(implementado por la aplicación cliente\) que proporciona la información necesaria para crear la lista de marcos de pila.  
  
## Notas para los llamadores  
 Esta interfaz se obtiene llamando al método de `CoCreateInstance` con el identificador de clase `CLSID_DiaStackWalker` y el identificador de la interfaz de `IID_IDiaStackWalker`.  el ejemplo muestra cómo se obtiene esta interfaz.  
  
## Ejemplo  
 este ejemplo muestra cómo obtener la interfaz de `IDiaStackWalker` .  
  
```cpp#  
  
      IDiaStackWalker* pStackWalker;  
HRESULT hr = CoCreateInstance(CLSID_DiaStackWalker,  
                              NULL,  
                              CLSCTX_INPROC_SERVER,  
                              IID_IDiaStackWalker,  
                              (void**) &pStackWalker);  
if (FAILED(hr))  
{  
    // Report error and exit  
}  
```  
  
## Requisitos  
 encabezado: Dia2.h  
  
 biblioteca: diaguids.lib  
  
 DLL: msdia80.dll  
  
## Vea también  
 [Interfaces \(Debug Interface Access SDK\)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)