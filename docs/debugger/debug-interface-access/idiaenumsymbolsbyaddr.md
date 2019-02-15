---
title: IDiaEnumSymbolsByAddr | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumSymbolsbyAddr interface
ms.assetid: 37d3dcdf-e4fa-4354-b5e1-8843566b52ac
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7ec61145d51ba383099d9b08fe0a50db10f97022
ms.sourcegitcommit: 34940a18f5b03a59567f54c7024a0b16d4272f1e
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 02/12/2019
ms.locfileid: "56155622"
---
# <a name="idiaenumsymbolsbyaddr"></a>IDiaEnumSymbolsByAddr
Enumera por dirección de los símbolos distintos contenidos en el origen de datos.

## <a name="syntax"></a>Sintaxis

```
IDiaEnumSymbolsByAddr : IUnknown
```

## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable
La tabla siguiente muestran los métodos de `IDiaEnumSymbolsByAddr`.

|Método|Descripción|
|------------|-----------------|
|[IDiaEnumSymbolsByAddr::symbolByAddr](../../debugger/debug-interface-access/idiaenumsymbolsbyaddr-symbolbyaddr.md)|Coloca el enumerador realizando una búsqueda por sección y el desplazamiento.|
|[IDiaEnumSymbolsByAddr::symbolByRVA](../../debugger/debug-interface-access/idiaenumsymbolsbyaddr-symbolbyrva.md)|Coloca el enumerador realizando una búsqueda por dirección virtual relativa (RVA).|
|[IDiaEnumSymbolsByAddr::symbolByVA](../../debugger/debug-interface-access/idiaenumsymbolsbyaddr-symbolbyva.md)|Coloca el enumerador realizando una búsqueda por dirección virtual (VA).|
|[IDiaEnumSymbolsByAddr::Next](../../debugger/debug-interface-access/idiaenumsymbolsbyaddr-next.md)|Recupera los símbolos en el orden siguientes por dirección. Actualiza la posición del enumerador por número de elementos que se capturan.|
|[IDiaEnumSymbolsByAddr::Prev](../../debugger/debug-interface-access/idiaenumsymbolsbyaddr-prev.md)|Recupera los símbolos anteriores en orden por dirección. Actualiza la posición del enumerador por número de elementos que se capturan.|
|[IDiaEnumSymbolsByAddr::Clone](../../debugger/debug-interface-access/idiaenumsymbolsbyaddr-clone.md)|Realiza una copia de un objeto.|

## <a name="remarks"></a>Comentarios
Esta interfaz proporciona símbolos agrupados por dirección. Para trabajar con símbolos agrupados por tipo, por ejemplo `SymTagUDT` (tipo definido por el usuario) o `SymTagBaseClass`, utilice el [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md) interfaz.

## <a name="notes-for-callers"></a>Notas para los llamadores
Esta interfaz se obtiene mediante una llamada a la [Getsymbolsbyaddr](../../debugger/debug-interface-access/idiasession-getsymbolsbyaddr.md) método.

## <a name="example"></a>Ejemplo
Esta función muestra el nombre y la dirección de todos los símbolos que se ordenan por la dirección virtual relativa.

```C++
void ShowSymbolsByAddress(IDiaSession *pSession)
{
    CComPtr<IDiaEnumSymbolsByAddr> pEnumByAddr;
    if ( FAILED( psession->getSymbolsByAddr( &pEnumByAddr ) ) )
    {
        Fatal( "getSymbolsByAddr" );
    }
    CComPtr<IDiaSymbol> pSym;
    if ( FAILED( pEnumByAddr->symbolByAddr( 1, 0, &pSym ) ) )
    {
        Fatal( "symbolByAddr" );
    }
    DWORD rvaLast = 0;
    if ( pSym->get_relativeVirtualAddress( &rvaLast ) == S_OK )
    {
        pSym = 0;
        if ( FAILED( pEnumByAddr->symbolByRVA( rvaLast, &pSym ) ) )
        {
            Fatal( "symbolByAddr" );
        }
        printf( "Symbols in order\n" );
        do
        {
            CDiaBSTR name;
            if ( pSym->get_name( &name ) != S_OK )
            {
                printf( "\t0x%08X (%ws) <no name>\n", rvaLast );
            }
            else
            {
                printf( "\t0x%08X %ws\n", rvaLast, name );
            }
            pSym = 0;
            celt = 0;
            if ( FAILED( hr = pEnumByAddr->Next( 1, &pSym, &celt ) ) )
            {
                break;
            }
        } while ( celt == 1 );
    }
}
```

## <a name="requirements"></a>Requisitos
Encabezado: Dia2.h

Biblioteca: diaguids.lib

DLL: msdia80.dll

## <a name="see-also"></a>Vea también
[Interfaces (Debug Interface Access SDK)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)  
[IDiaSession::getSymbolsByAddr](../../debugger/debug-interface-access/idiasession-getsymbolsbyaddr.md)  
[IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)
