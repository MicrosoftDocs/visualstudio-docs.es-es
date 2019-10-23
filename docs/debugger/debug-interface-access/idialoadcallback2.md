---
title: IDiaLoadCallback2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaLoadCallback2 interface
ms.assetid: 9a44277d-cbed-4811-9bad-5a2aa0f09323
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7db8b6a115acdafeca2e7e0adbe11be97834cd6d
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/22/2019
ms.locfileid: "72742964"
---
# <a name="idialoadcallback2"></a>IDiaLoadCallback2
Recibe las devoluciones de llamada del procedimiento de búsqueda de símbolos de DIA, lo que permite imponer restricciones en el proceso de búsqueda.

## <a name="syntax"></a>Sintaxis

```
IDiaLoadCallback2 : IDiaLoadCallback
```

## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable
 Además de los métodos de la interfaz [IDiaLoadCallback](../../debugger/debug-interface-access/idialoadcallback.md) , esta interfaz expone los siguientes métodos:

|Método|Descripción|
|------------|-----------------|
|[IDiaLoadCallback2::RestrictOriginalPathAccess](../../debugger/debug-interface-access/idialoadcallback2-restrictoriginalpathaccess.md)|Determina si se busca un archivo. pdb en el directorio de depuración original.|
|[IDiaLoadCallback2::RestrictReferencePathAccess](../../debugger/debug-interface-access/idialoadcallback2-restrictreferencepathaccess.md)|Determina si se permite buscar un archivo. pdb en la ruta de acceso donde se encuentra el archivo. exe.|
|[IDiaLoadCallback2::RestrictDBGAccess](../../debugger/debug-interface-access/idialoadcallback2-restrictdbgaccess.md)|Determina si se permite la información de depuración de los archivos. dbg.|
|[IDiaLoadCallback2::RestrictSystemRootAccess](../../debugger/debug-interface-access/idialoadcallback2-restrictsystemrootaccess.md)|Determina si se permite la búsqueda de archivos. pdb en el directorio raíz del sistema.|

## <a name="remarks"></a>Comentarios
 La aplicación cliente implementa esta interfaz y proporciona una referencia a ella en la llamada al método [IDiaDataSource:: loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) . Recuerde implementar también todos los métodos en la interfaz [IDiaLoadCallback](../../debugger/debug-interface-access/idialoadcallback.md) .

## <a name="requirements"></a>Requisitos
 Encabezado: Dia2. h

 Biblioteca: diaguids. lib

 DLL: msdia80.dll

## <a name="see-also"></a>Vea también
- [Interfaces (Debug Interface Access SDK)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)
- [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)
- [IDiaReadExeAtOffsetCallback](../../debugger/debug-interface-access/idiareadexeatoffsetcallback.md)
- [IDiaReadExeAtRVACallback](../../debugger/debug-interface-access/idiareadexeatrvacallback.md)
- [IDiaLoadCallback](../../debugger/debug-interface-access/idialoadcallback.md)