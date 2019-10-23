---
title: IDiaTable | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaTable interface
ms.assetid: c99a2c44-7b72-4e3c-b963-25fe3df3a555
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: bc7a573eb92d7c51079b0a7e97067abd155ae4fa
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/22/2019
ms.locfileid: "72738710"
---
# <a name="idiatable"></a>IDiaTable
Enumera una tabla de origen de datos DIA.

## <a name="syntax"></a>Sintaxis

```
IDiaTable : IEnumUnknown
```

## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable
En la tabla siguiente se muestran los métodos de `IDiaTable`.

|Método|Descripción|
|------------|-----------------|
|[IDiaTable::get__NewEnum](../../debugger/debug-interface-access/idiatable-get-newenum.md)|Recupera la versión de la [interfaz IEnumVARIANT](/previous-versions/windows/desktop/api/oaidl/nn-oaidl-ienumvariant) de este enumerador.|
|[IDiaTable::get_name](../../debugger/debug-interface-access/idiatable-get-name.md)|Recupera el nombre de la tabla.|
|[IDiaTable::get_Count](../../debugger/debug-interface-access/idiatable-get-count.md)|Recupera el número de elementos de la tabla.|
|[IDiaTable::Item](../../debugger/debug-interface-access/idiatable-item.md)|Recupera una referencia a un índice de entrada determinado.|

## <a name="remarks"></a>Comentarios
Esta interfaz implementa los métodos de enumeración de `IEnumUnknown` en el espacio de nombres Microsoft. VisualStudio. OLE. Interop. La interfaz de enumeración de `IEnumUnknown` es mucho más eficaz para recorrer en iteración el contenido de la tabla que los métodos [IDiaTable:: get_Count](../../debugger/debug-interface-access/idiatable-get-count.md) y [IDiaTable:: Item](../../debugger/debug-interface-access/idiatable-item.md) .

La interpretación de la interfaz `IUnknown` devuelta desde el método `IDiaTable::Item` o el método `Next` (en el espacio de nombres Microsoft. VisualStudio. OLE. Interop) depende del tipo de tabla. Por ejemplo, si la interfaz de `IDiaTable` representa una lista de orígenes insertados, se debe consultar la interfaz de `IUnknown` para la interfaz [IDiaInjectedSource](../../debugger/debug-interface-access/idiainjectedsource.md) .

## <a name="notes-for-callers"></a>Notas para llamadores
Obtenga esta interfaz mediante una llamada a los métodos [IDiaEnumTables:: Item](../../debugger/debug-interface-access/idiaenumtables-item.md) o [IDiaEnumTables:: Next](../../debugger/debug-interface-access/idiaenumtables-next.md) .

Las siguientes interfaces se implementan con la interfaz `IDiaTable` (es decir, se puede consultar la interfaz de `IDiaTable` para una de las interfaces siguientes):

- [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)

- [IDiaEnumSourceFiles](../../debugger/debug-interface-access/idiaenumsourcefiles.md)

- [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)

- [IDiaEnumSectionContribs](../../debugger/debug-interface-access/idiaenumsectioncontribs.md)

- [IDiaEnumSegments](../../debugger/debug-interface-access/idiaenumsegments.md)

- [IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md)

- [IDiaEnumFrameData](../../debugger/debug-interface-access/idiaenumframedata.md)

## <a name="example"></a>Ejemplo
La primera función, `ShowTableNames`, muestra los nombres de todas las tablas de la sesión. La segunda función, `GetTable`, busca en todas las tablas una tabla que implementa una interfaz especificada. La tercera función, `UseTable`, muestra cómo usar la función `GetTable`.

> [!NOTE]
> `CDiaBSTR` es una clase que contiene un `BSTR` y controla automáticamente la liberación de la cadena cuando la creación de instancias sale del ámbito.

```C++
void ShowTableNames(IDiaSession *pSession)
{
    CComPtr<IDiaEnumTables> pTables;
    if ( FAILED( psession->getEnumTables( &pTables ) ) )
    {
        Fatal( "getEnumTables" );
    }
    CComPtr< IDiaTable > pTable;
    while ( SUCCEEDED( hr = pTables->Next( 1, &pTable, &celt ) )
            && celt == 1 )
    {
        CDiaBSTR bstrTableName;
        if ( pTable->get_name( &bstrTableName ) != 0 )
        {
            Fatal( "get_name" );
        }
        printf( "Found table: %ws\n", bstrTableName );
    }

// Searches the list of all tables for a table that supports
// the specified interface.  Use this function to obtain an
// enumeration interface.
HRESULT GetTable(IDiaSession* pSession,
                 REFIID       iid,
                 void**       ppUnk)
{
    CComPtr<IDiaEnumTables> pEnumTables;
    HRESULT hResult;

    if (FAILED(pSession->getEnumTables(&pEnumTables)))
        Fatal("getEnumTables");

    CComPtr<IDiaTable> pTable;
    ULONG celt = 0;
    while (SUCCEEDED(hResult = pEnumTables->Next(1, &pTable, &celt)) &&
           celt == 1)
    {
        if (pTable->QueryInterface(iid, (void**)ppUnk) == S_OK)
        {
            return S_OK;
        }
        pTable = NULL;
    }

    if (FAILED(hResult))
        Fatal("EnumTables->Next");

    return E_FAIL;
}

// This function shows how to use the GetTable function.
void UseTable(IDiaSession *pSession)
{
    CComPtr<IDiaEnumSegments> pEnumSegments;
    if (SUCCEEDED(GetTable(pSession, __uuidof(IDiaEnumSegments), &pEnumSegments)))
    {
        // Do something with pEnumSegments.
    }
}
```

## <a name="requirements"></a>Requisitos
Encabezado: Dia2. h

Biblioteca: diaguids. lib

DLL: msdia80.dll

## <a name="see-also"></a>Vea también
- [Interfaces (Debug Interface Access SDK)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)
- [IDiaEnumTables](../../debugger/debug-interface-access/idiaenumtables.md)
- [IDiaEnumTables::Item](../../debugger/debug-interface-access/idiaenumtables-item.md)
- [IDiaEnumTables::Next](../../debugger/debug-interface-access/idiaenumtables-next.md)
