---
title: IDiaStackWalkFrame | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalkFrame interface
ms.assetid: 42d82845-d6f6-4846-9ecd-9dd169216077
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5b2657127726e387e81a5b28c639abbaa5399019
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/22/2019
ms.locfileid: "72741439"
---
# <a name="idiastackwalkframe"></a>IDiaStackWalkFrame
Mantiene el contexto de pila entre las invocaciones del método [IDiaFrameData:: Execute](../../debugger/debug-interface-access/idiaframedata-execute.md) .

## <a name="syntax"></a>Sintaxis

```
IDiaStackWalkFrame : IUnknown
```

## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable
 En la tabla siguiente se muestran los métodos de `IDiaStackWalkFrame`.

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
 La aplicación cliente implementa esta interfaz y pasa una instancia de la interfaz al método [IDiaFrameData:: Execute](../../debugger/debug-interface-access/idiaframedata-execute.md) . La misma instancia de esta interfaz se utiliza de nuevo y de nuevo para mantener el estado de los registros durante cada invocación del método `execute`. El método `execute` también utiliza esta interfaz para determinar la dirección de retorno.

## <a name="requirements"></a>Requisitos
 Encabezado: Dia2. h

 Biblioteca: diaguids. lib

 DLL: msdia80.dll

## <a name="see-also"></a>Vea también
- [Interfaces (Debug Interface Access SDK)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)
- [IDiaFrameData::execute](../../debugger/debug-interface-access/idiaframedata-execute.md)