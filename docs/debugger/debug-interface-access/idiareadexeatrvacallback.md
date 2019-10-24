---
title: IDiaReadExeAtRVACallback | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaReadExeAtRVACallback interface
ms.assetid: b2892513-3952-4f99-9b98-60cb9b1fdc91
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2aee44ff3acc1d7423e19de8fd64be0e46d8e372
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/22/2019
ms.locfileid: "72742807"
---
# <a name="idiareadexeatrvacallback"></a>IDiaReadExeAtRVACallback
Permite que una aplicación cliente suministre bytes de un archivo ejecutable según lo especificado por una dirección virtual relativa.

## <a name="syntax"></a>Sintaxis

```
IDiaReadExeAtRVACallback : IUnknown
```

## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable
 En la tabla siguiente se muestran los métodos de `IDiaReadExeAtRVACallback`.

|Método|Descripción|
|------------|-----------------|
|[IDiaReadExeAtRVACallback::ReadExecutableAtRVA](../../debugger/debug-interface-access/idiareadexeatrvacallback-readexecutableatrva.md)|Lee el número especificado de bytes a partir de la dirección virtual relativa (RVA) especificada del archivo ejecutable.|

## <a name="remarks"></a>Comentarios
 La aplicación cliente implementa esta interfaz para proporcionar los bytes del ejecutable usando una dirección virtual relativa en el archivo del ejecutable. Para usar un desplazamiento de archivo absoluto, implemente la interfaz [IDiaReadExeAtOffsetCallback](../../debugger/debug-interface-access/idiareadexeatoffsetcallback.md) .

## <a name="notes-for-callers"></a>Notas para llamadores
 La aplicación cliente implementa este método y se pasa al método [IDiaDataSource:: loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) como un método alternativo para leer el archivo.

## <a name="requirements"></a>Requisitos
 Encabezado: Dia2. h

 Biblioteca: diaguids. lib

 DLL: msdia80.dll

## <a name="see-also"></a>Vea también
- [Interfaces (Debug Interface Access SDK)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)
- [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)
- [IDiaReadExeAtOffsetCallback](../../debugger/debug-interface-access/idiareadexeatoffsetcallback.md)