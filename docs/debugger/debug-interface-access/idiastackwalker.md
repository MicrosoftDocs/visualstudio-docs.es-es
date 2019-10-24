---
title: IDiaStackWalker | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalker interface
ms.assetid: 4a61a22a-9cf8-4ea1-9e6e-b42f96872d40
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2366c933bf072c295b29d06ff5610bd3735c0077
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/22/2019
ms.locfileid: "72741520"
---
# <a name="idiastackwalker"></a>IDiaStackWalker
Proporciona métodos para realizar un recorrido de pila utilizando la información del archivo. pdb.

## <a name="syntax"></a>Sintaxis

```
IDiaStackWalker: IUnknown
```

## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable
En la tabla siguiente se muestran los métodos de `IDiaStackWalker`.

|Método|Descripción|
|------------|-----------------|
|[IDiaStackWalker::getEnumFrames](../../debugger/debug-interface-access/idiastackwalker-getenumframes.md)|Recupera un enumerador de marcos de pila para las plataformas x86.|
|[IDiaStackWalker::getEnumFrames2](../../debugger/debug-interface-access/idiastackwalker-getenumframes2.md)|Recupera un enumerador de marcos de pila para un tipo de plataforma específico.|

## <a name="remarks"></a>Comentarios
Esta interfaz se usa para obtener una lista de marcos de pila para un módulo cargado. A cada uno de los métodos se le pasa un objeto [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md) (implementado por la aplicación cliente) que proporciona la información necesaria para crear la lista de marcos de pila.

## <a name="notes-for-callers"></a>Notas para llamadores
Esta interfaz se obtiene llamando al método `CoCreateInstance` con el identificador de clase `CLSID_DiaStackWalker` y el ID. de interfaz de `IID_IDiaStackWalker`. En el ejemplo se muestra cómo se obtiene esta interfaz.

## <a name="example"></a>Ejemplo
En este ejemplo se muestra cómo obtener la interfaz `IDiaStackWalker`.

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
Encabezado: Dia2. h

Biblioteca: diaguids. lib

DLL: msdia80.dll

## <a name="see-also"></a>Vea también
- [Interfaces (Debug Interface Access SDK)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)
- [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)
