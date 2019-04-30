---
title: IDiaReadExeAtOffsetCallback | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaReadExeAtOffsetCallback interface
ms.assetid: 3c961641-3ce3-4bc3-bd6e-a802fa3bec49
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: df32012a100d36c8d288b6b988b9498ff4afd3b3
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62832560"
---
# <a name="idiareadexeatoffsetcallback"></a>IDiaReadExeAtOffsetCallback
Permite que una aplicación cliente proporcionar los bytes de un archivo ejecutable como especificado por la posición del archivo.

## <a name="syntax"></a>Sintaxis

```
IDiaReadExeAtOffsetCallback : IUnknown
```

## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable
 La tabla siguiente muestran los métodos de `IDiaReadExeAtOffsetCallback`.

|Método|Descripción|
|------------|-----------------|
|[IDiaReadExeAtOffsetCallback::ReadExecutableAt](../../debugger/debug-interface-access/idiareadexeatoffsetcallback-readexecutableat.md)|Lee el número especificado de bytes a partir del desplazamiento especificado desde un archivo ejecutable.|

## <a name="remarks"></a>Comentarios
 La aplicación cliente implementa esta interfaz para proporcionar los bytes del archivo ejecutable con un desplazamiento absoluto en el archivo del ejecutable. Para utilizar una dirección virtual relativa, implementar el [IDiaReadExeAtRVACallback](../../debugger/debug-interface-access/idiareadexeatrvacallback.md) interfaz.

## <a name="notes-for-callers"></a>Notas para los llamadores
 Este método es implementada por la aplicación cliente y pasa a la [Loaddataforexe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) método como un método alternativo para leer el archivo.

## <a name="requirements"></a>Requisitos
 Encabezado: Dia2.h

 Biblioteca: diaguids.lib

 DLL: msdia80.dll

## <a name="see-also"></a>Vea también
- [Interfaces (Debug Interface Access SDK)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)
- [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)
- [IDiaReadExeAtRVACallback](../../debugger/debug-interface-access/idiareadexeatrvacallback.md)