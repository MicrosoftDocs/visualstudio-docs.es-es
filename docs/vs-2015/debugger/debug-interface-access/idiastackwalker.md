---
title: IDiaStackWalker | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalker interface
ms.assetid: 4a61a22a-9cf8-4ea1-9e6e-b42f96872d40
caps.latest.revision: 13
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: d6f5f5c3fa70c022175208cee492f3c0e752826e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "68144682"
---
# <a name="idiastackwalker"></a>IDiaStackWalker
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Proporciona métodos para realizar un recorrido de pila utilizando la información del archivo. pdb.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
IDiaStackWalker: IUnknown  
```  
  
## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable  
 En la tabla siguiente se muestran los métodos de `IDiaStackWalker` .  
  
|Método|Descripción|  
|------------|-----------------|  
|[IDiaStackWalker::getEnumFrames](../../debugger/debug-interface-access/idiastackwalker-getenumframes.md)|Recupera un enumerador de marcos de pila para las plataformas x86.|  
|[IDiaStackWalker::getEnumFrames2](../../debugger/debug-interface-access/idiastackwalker-getenumframes2.md)|Recupera un enumerador de marcos de pila para un tipo de plataforma específico.|  
  
## <a name="remarks"></a>Comentarios  
 Esta interfaz se usa para obtener una lista de marcos de pila para un módulo cargado. A cada uno de los métodos se le pasa un objeto [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md) (implementado por la aplicación cliente) que proporciona la información necesaria para crear la lista de marcos de pila.  
  
## <a name="notes-for-callers"></a>Notas para llamadores  
 Esta interfaz se obtiene llamando al `CoCreateInstance` método con el identificador `CLSID_DiaStackWalker` de clase y el identificador de interfaz de `IID_IDiaStackWalker` . En el ejemplo se muestra cómo se obtiene esta interfaz.  
  
## <a name="example"></a>Ejemplo  
 En este ejemplo se muestra cómo obtener la `IDiaStackWalker` interfaz.  
  
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
  
## <a name="requirements"></a>Requisitos  
 Encabezado: Dia2. h  
  
 Biblioteca: diaguids. lib  
  
 DLL: msdia80.dll  
  
## <a name="see-also"></a>Consulte también  
 [Interfaces (Debug Interface Access SDK)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)
