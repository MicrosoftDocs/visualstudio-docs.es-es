---
title: IDiaStackWalkFrame | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalkFrame interface
ms.assetid: 42d82845-d6f6-4846-9ecd-9dd169216077
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 27aab0ca87e589661798028ff38fb019dae815ed
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "68150135"
---
# <a name="idiastackwalkframe"></a>IDiaStackWalkFrame
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Mantiene el contexto de pila entre las invocaciones del método [IDiaFrameData:: Execute](../../debugger/debug-interface-access/idiaframedata-execute.md) .  
  
## <a name="syntax"></a>Sintaxis  
  
```  
IDiaStackWalkFrame : IUnknown  
```  
  
## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable  
 En la tabla siguiente se muestran los métodos de `IDiaStackWalkFrame` .  
  
|Método|Descripción|  
|------------|-----------------|  
|[IDiaStackWalkFrame::get_registerValue](../../debugger/debug-interface-access/idiastackwalkframe-get-registervalue.md)|Recupera el valor de un registro.|  
|[IDiaStackWalkFrame::put_registerValue](../../debugger/debug-interface-access/idiastackwalkframe-put-registervalue.md)|Establece el valor de un registro.|  
|[IDiaStackWalkFrame::readMemory](../../debugger/debug-interface-access/idiastackwalkframe-readmemory.md)|Lee la memoria de la imagen.|  
|[IDiaStackWalkFrame::searchForReturnAddress](../../debugger/debug-interface-access/idiastackwalkframe-searchforreturnaddress.md)|Busca la dirección de retorno de la función más cercana en el marco de pila especificado.|  
|[IDiaStackWalkFrame::searchForReturnAddressStart](../../debugger/debug-interface-access/idiastackwalkframe-searchforreturnaddressstart.md)|Busca en el marco de pila especificado una dirección de devolución en la dirección especificada o cerca de ella.|  
  
## <a name="remarks"></a>Comentarios  
 Esta interfaz se usa durante la ejecución del programa para leer y escribir registros, así como para obtener acceso a la memoria y buscar direcciones de devolución.  
  
## <a name="notes-for-callers"></a>Notas para llamadores  
 La aplicación cliente implementa esta interfaz y pasa una instancia de la interfaz al método [IDiaFrameData:: Execute](../../debugger/debug-interface-access/idiaframedata-execute.md) . La misma instancia de esta interfaz se utiliza de nuevo y de nuevo para mantener el estado de los registros durante cada invocación del `execute` método. El `execute` método también usa esta interfaz para determinar la dirección de devolución.  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: Dia2. h  
  
 Biblioteca: diaguids. lib  
  
 DLL: msdia80.dll  
  
## <a name="see-also"></a>Consulte también  
 [Interfaces (Debug Interface Access SDK)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [IDiaFrameData::execute](../../debugger/debug-interface-access/idiaframedata-execute.md)
