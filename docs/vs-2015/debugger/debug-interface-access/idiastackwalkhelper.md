---
title: IDiaStackWalkHelper | Documentos de Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalkHelper2 interface
ms.assetid: d66e5c84-565d-494e-8486-f91db9a34548
caps.latest.revision: 18
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 315af434271d57a8547963f2538ff1b799ef4fd3
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "68150022"
---
# <a name="idiastackwalkhelper"></a>IDiaStackWalkHelper
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Facilita el recorrido de la pila mediante el archivo de programa depuración (.pdb) de la base de datos.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
IDiaStackWalkHelper: IUnknown  
  
```  
  
## <a name="methods-in-vtable-order"></a>Métodos en orden de VTable  
 La siguiente tabla muestra los métodos de `IDiaStackWalkHelper`:  
  
|Método|DESCRIPCIÓN|  
|------------|-----------------|  
|[IDiaStackWalkHelper::get_registerValue](../../debugger/debug-interface-access/idiastackwalkhelper-get-registervalue.md)|Recupera el valor de un registro.|  
|[IDiaStackWalkHelper::put_registerValue](../../debugger/debug-interface-access/idiastackwalkhelper-put-registervalue.md)|Establece el valor de un registro.|  
|[IDiaStackWalkHelper::readMemory](../../debugger/debug-interface-access/idiastackwalkhelper-readmemory.md)|Lee un bloque de datos de imagen del archivo ejecutable en la memoria.|  
|[IDiaStackWalkHelper::searchForReturnAddress](../../debugger/debug-interface-access/idiastackwalkhelper-searchforreturnaddress.md)|Busca el marco de pila especificado para la dirección de devolución de función más cercano.|  
|[IDiaStackWalkHelper::searchForReturnAddressStart](../../debugger/debug-interface-access/idiastackwalkhelper-searchforreturnaddressstart.md)|Busca el marco de pila especificado para una dirección de retorno en o cerca de la dirección de pila especificado.|  
|[IDiaStackWalkHelper::frameForVA](../../debugger/debug-interface-access/idiastackwalkhelper-frameforva.md)|Recupera el marco de pila que contiene la dirección virtual especificada.|  
|[IDiaStackWalkHelper::symbolForVA](../../debugger/debug-interface-access/idiastackwalkhelper-symbolforva.md)|Recupera el símbolo que contiene la dirección virtual especificada. **Nota:**  Símbolo debe tener el tipo `SymTagFunctionType` (un valor de la [SymTagEnum (enumeración)](../../debugger/debug-interface-access/symtagenum.md) enumeración).|  
|[IDiaStackWalkHelper::pdataForVA](../../debugger/debug-interface-access/idiastackwalkhelper-pdataforva.md)|Devuelve el bloque de datos PDATA asociado con la dirección virtual especificada.|  
|[IDiaStackWalkHelper::imageForVA](../../debugger/debug-interface-access/idiastackwalkhelper-imageforva.md)|Recupera la dirección virtual a partir de un archivo ejecutable, dada una dirección virtual en algún lugar en el espacio de memoria del archivo ejecutable.|  
  
## <a name="remarks"></a>Comentarios  
 El código DIA para obtener información sobre el archivo ejecutable para construir una lista de marcos de pila durante la ejecución del programa llama a esta interfaz.  
  
## <a name="notes-for-callers"></a>Notas para los llamadores  
 Una aplicación cliente implementa esta interfaz para admitir recorrer la pila durante la ejecución del programa. Una instancia de esta interfaz se pasa a la [IDiaStackWalker::getEnumFrames](../../debugger/debug-interface-access/idiastackwalker-getenumframes.md) o [IDiaStackWalker::getEnumFrames2](../../debugger/debug-interface-access/idiastackwalker-getenumframes2.md) métodos.  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: Dia2.h  
  
 Biblioteca: diaguids.lib  
  
 DLL: msdia80.dll  
  
## <a name="see-also"></a>Vea también  
 [Interfaces (SDK de acceso a la interfaz de depuración)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)   
 [Enumeración SymTagEnum](../../debugger/debug-interface-access/symtagenum.md)   
 [IDiaStackWalker::getEnumFrames](../../debugger/debug-interface-access/idiastackwalker-getenumframes.md)   
 [IDiaStackWalker::getEnumFrames2](../../debugger/debug-interface-access/idiastackwalker-getenumframes2.md)
