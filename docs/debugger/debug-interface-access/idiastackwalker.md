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
ms.openlocfilehash: 5ad74f92765ee449eab1e3089511a063e70d96a0
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62831938"
---
# <a name="idiastackwalker"></a>IDiaStackWalker
Proporciona métodos para hacer una pila del recorrido con información en el archivo PDB.

## <a name="syntax"></a>Sintaxis

```
IDiaStackWalker: IUnknown
```

## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable
La tabla siguiente muestran los métodos de `IDiaStackWalker`.

|Método|Descripción|
|------------|-----------------|
|[IDiaStackWalker::getEnumFrames](../../debugger/debug-interface-access/idiastackwalker-getenumframes.md)|Recupera un enumerador de marco de pila para x86 plataformas.|
|[IDiaStackWalker::getEnumFrames2](../../debugger/debug-interface-access/idiastackwalker-getenumframes2.md)|Recupera un enumerador de marco de pila para un tipo específico de plataforma.|

## <a name="remarks"></a>Comentarios
Esta interfaz se utiliza para obtener una lista de marcos de pila para un módulo cargado. Cada uno de los métodos se pasa un [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md) objeto (implementado por la aplicación cliente) que proporciona la información necesaria para crear la lista de marcos de pila.

## <a name="notes-for-callers"></a>Notas para los llamadores
Esta interfaz se obtiene mediante una llamada a la `CoCreateInstance` método con el identificador de clase `CLSID_DiaStackWalker` y el identificador de interfaz de `IID_IDiaStackWalker`. El ejemplo muestra cómo se obtiene esta interfaz.

## <a name="example"></a>Ejemplo
En este ejemplo se muestra cómo obtener el `IDiaStackWalker` interfaz.

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
- [Interfaces (Debug Interface Access SDK)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)
- [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)
