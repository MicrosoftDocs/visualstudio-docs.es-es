---
title: IDiaStackWalkFrame | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalkFrame interface
ms.assetid: 42d82845-d6f6-4846-9ecd-9dd169216077
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f16d6f824b3b150406c23cce87e186fe9b120999
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2018
ms.locfileid: "31465634"
---
# <a name="idiastackwalkframe"></a>IDiaStackWalkFrame
Mantiene el contexto de la pila entre las distintas invocaciones de la [idiaframedata:: Execute](../../debugger/debug-interface-access/idiaframedata-execute.md) método.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
IDiaStackWalkFrame : IUnknown  
```  
  
## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable  
 La tabla siguiente muestran los métodos de `IDiaStackWalkFrame`.  
  
|Método|Descripción|  
|------------|-----------------|  
|[IDiaStackWalkFrame::get_registerValue](../../debugger/debug-interface-access/idiastackwalkframe-get-registervalue.md)|Recupera el valor de un registro.|  
|[IDiaStackWalkFrame::put_registerValue](../../debugger/debug-interface-access/idiastackwalkframe-put-registervalue.md)|Establece el valor de un registro.|  
|[IDiaStackWalkFrame::readMemory](../../debugger/debug-interface-access/idiastackwalkframe-readmemory.md)|Lee de la imagen de memoria.|  
|[IDiaStackWalkFrame::searchForReturnAddress](../../debugger/debug-interface-access/idiastackwalkframe-searchforreturnaddress.md)|Busca el marco de pila especificado para la dirección de devolución de función más cercano.|  
|[IDiaStackWalkFrame::searchForReturnAddressStart](../../debugger/debug-interface-access/idiastackwalkframe-searchforreturnaddressstart.md)|Busca el marco de pila especificado para una dirección de remite en o cerca de la dirección especificada.|  
  
## <a name="remarks"></a>Comentarios  
 Esta interfaz se utiliza durante la ejecución del programa para leer y escribir registros, así como obtener acceso a memoria y buscar direcciones de devolución.  
  
## <a name="notes-for-callers"></a>Notas para los llamadores  
 La aplicación cliente implementa esta interfaz y pasa una instancia de la interfaz para la [idiaframedata:: Execute](../../debugger/debug-interface-access/idiaframedata-execute.md) método. La misma instancia de esta interfaz se utiliza una y otra vez para mantener el estado de los registros durante cada invocación de la `execute` método. El `execute` método también utiliza esta interfaz para determinar la dirección de retorno.  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: Dia2.h  
  
 Biblioteca: diaguids.lib  
  
 DLL: msdia80.dll  
  
## <a name="see-also"></a>Vea también  
 [Interfaces (Debug Interface Access SDK)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [IDiaFrameData::execute](../../debugger/debug-interface-access/idiaframedata-execute.md)