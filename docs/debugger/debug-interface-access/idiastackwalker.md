---
title: IDiaStackWalker | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalker interface
ms.assetid: 4a61a22a-9cf8-4ea1-9e6e-b42f96872d40
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 68cf4cf206d243762247b36161f349cc2a1387cc
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="idiastackwalker"></a>IDiaStackWalker
Proporciona métodos para realizar una pila del recorrido con información en el archivo .pdb.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
IDiaStackWalker: IUnknown  
```  
  
## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable  
 La tabla siguiente muestran los métodos de `IDiaStackWalker`.  
  
|Método|Descripción|  
|------------|-----------------|  
|[IDiaStackWalker::getEnumFrames](../../debugger/debug-interface-access/idiastackwalker-getenumframes.md)|Recupera un enumerador de marco de pila para x86 plataformas.|  
|[IDiaStackWalker::getEnumFrames2](../../debugger/debug-interface-access/idiastackwalker-getenumframes2.md)|Recupera un enumerador de marco de pila para un tipo de plataforma concreta.|  
  
## <a name="remarks"></a>Comentarios  
 Esta interfaz se utiliza para obtener una lista de los marcos de pila para un módulo cargado. Se pasa a cada uno de los métodos de un [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md) objeto (implementada por la aplicación cliente) que proporciona la información necesaria para crear la lista de marcos de pila.  
  
## <a name="notes-for-callers"></a>Notas para los llamadores  
 Esta interfaz se obtiene mediante una llamada a la `CoCreateInstance` método con el identificador de clase `CLSID_DiaStackWalker` y el identificador de interfaz de `IID_IDiaStackWalker`. En el ejemplo se muestra cómo se obtiene esta interfaz.  
  
## <a name="example"></a>Ejemplo  
 Este ejemplo muestra cómo obtener el `IDiaStackWalker` interfaz.  
  
```C++  
  
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
  
## <a name="requirements"></a>Requisitos  
 Encabezado: Dia2.h  
  
 Biblioteca: diaguids.lib  
  
 DLL: msdia80.dll  
  
## <a name="see-also"></a>Vea también  
 [Interfaces (Debug Interface Access SDK)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)