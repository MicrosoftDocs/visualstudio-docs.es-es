---
title: IDiaEnumSourceFiles | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumSourceFiles interface
ms.assetid: 5c0779a6-a2ea-408a-90da-ebdecf2b83c0
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7c3a6d3eb61f4e4a7504b184477ec1b3f2a8ba83
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 02/21/2019
ms.locfileid: "56641928"
---
# <a name="idiaenumsourcefiles"></a>IDiaEnumSourceFiles
Enumera los distintos archivos de origen contenidos en el origen de datos.

## <a name="syntax"></a>Sintaxis

```
IDiaEnumSourceFiles : IUnknown
```

## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable
La tabla siguiente muestran los métodos de `IDiaEnumSourceFiles`.

|Método|Descripción|
|------------|-----------------|
|[IDiaEnumSourceFiles::get__NewEnum](../../debugger/debug-interface-access/idiaenumsourcefiles-get-newenum.md)|Recupera el `IEnumVARIANT Interface` versión de este enumerador.|
|[IDiaEnumSourceFiles::get_Count](../../debugger/debug-interface-access/idiaenumsourcefiles-get-count.md)|Recupera el número de archivos de origen.|
|[IDiaEnumSourceFiles::Item](../../debugger/debug-interface-access/idiaenumsourcefiles-item.md)|Recupera un archivo de origen por medio de un índice.|
|[IDiaEnumSourceFiles::Next](../../debugger/debug-interface-access/idiaenumsourcefiles-next.md)|Recupera un número especificado de archivos de origen en la secuencia de enumeración.|
|[IDiaEnumSourceFiles::Skip](../../debugger/debug-interface-access/idiaenumsourcefiles-skip.md)|Omite un número especificado de archivos de origen en una secuencia de enumeración.|
|[IDiaEnumSourceFiles::Reset](../../debugger/debug-interface-access/idiaenumsourcefiles-reset.md)|Restablece una secuencia de enumeración al principio.|
|[IDiaEnumSourceFiles::Clone](../../debugger/debug-interface-access/idiaenumsourcefiles-clone.md)|Crea un enumerador que contiene el mismo estado de enumeración que el enumerador actual.|

## <a name="remarks"></a>Comentarios

## <a name="notes-for-callers"></a>Notas para los llamadores
Esta interfaz se obtiene mediante una llamada a la `QueryInterface` método en un [IDiaTable](../../debugger/debug-interface-access/idiatable.md) objeto. Vea el ejemplo para obtener más información.

## <a name="example"></a>Ejemplo
En este ejemplo se muestra cómo obtener el `IDiaEnumSourceFiles` interfaz desde la lista de tablas en un objeto de sesión DIA. Para obtener un ejemplo de acceso a la información del archivo de origen, consulte el [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md) interfaz.

```C++

IDiaEnumSourceFiles* GetEnumSourceFiles(IDiaSession *pSession)
{
    IDiaEnumSourceFiles * pUnknown    = NULL;
    REFIID                iid         = __uuidof(IDiaEnumSourceFiles);
    IDiaEnumTables*       pEnumTables = NULL;
    IDiaTable*            pTable      = NULL;
    ULONG                 celt        = 0;

    if (pSession->getEnumTables(&pEnumTables) != S_OK)
    {
        wprintf(L"ERROR - GetTable() getEnumTables\n");
        return NULL;
    }
    while (pEnumTables->Next(1, &pTable, &celt) == S_OK && celt == 1)
    {
        // There is only one table that matches the given iid
        HRESULT hr = pTable->QueryInterface(iid, (void**)&pUnknown);
        pTable->Release();
        if (hr == S_OK)
        {
            break;
        }
    }
    pEnumTables->Release();
    return pUnknown;
}
```

## <a name="requirements"></a>Requisitos
Encabezado: Dia2.h

Biblioteca: diaguids.lib

DLL: msdia80.dll

## <a name="see-also"></a>Vea también
- [Interfaces (Debug Interface Access SDK)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)
- [IDiaSession::findFile](../../debugger/debug-interface-access/idiasession-findfile.md)
- [IDiaSession::findLinesByLinenum](../../debugger/debug-interface-access/idiasession-findlinesbylinenum.md)
- [IDiaTable](../../debugger/debug-interface-access/idiatable.md)
