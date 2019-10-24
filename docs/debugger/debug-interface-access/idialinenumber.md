---
title: IDiaLineNumber | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaLineNumber interface
ms.assetid: 1071f7d0-1f8c-4384-933f-c49c7eb930bd
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 819fe28b9ba3fb95e749f0be53702dd7fdccf008
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/22/2019
ms.locfileid: "72743107"
---
# <a name="idialinenumber"></a>IDiaLineNumber
Obtiene acceso a información que describe el proceso de asignación de un bloque de bytes de texto de imagen a un número de línea del archivo de código fuente.

## <a name="syntax"></a>Sintaxis

```
IDiaLineNumber : IUnknown
```

## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable
En la tabla siguiente se muestran los métodos de `IDiaLineNumber`.

|Método|Descripción|
|------------|-----------------|
|[IDiaLineNumber::get_compiland](../../debugger/debug-interface-access/idialinenumber-get-compiland.md)|Recupera una referencia al símbolo de la operación de compilación que contribuyó los bytes del texto de la imagen.|
|[IDiaLineNumber::get_sourceFile](../../debugger/debug-interface-access/idialinenumber-get-sourcefile.md)|Recupera una referencia al objeto de archivo de origen.|
|[IDiaLineNumber::get_lineNumber](../../debugger/debug-interface-access/idialinenumber-get-linenumber.md)|Recupera el número de línea del archivo de código fuente.|
|[IDiaLineNumber::get_lineNumberEnd](../../debugger/debug-interface-access/idialinenumber-get-linenumberend.md)|Recupera el número de línea de origen basado en uno en el que finaliza la instrucción o expresión.|
|[IDiaLineNumber::get_columnNumber](../../debugger/debug-interface-access/idialinenumber-get-columnnumber.md)|Recupera el número de columna donde comienza la expresión o instrucción.|
|[IDiaLineNumber::get_columnNumberEnd](../../debugger/debug-interface-access/idialinenumber-get-columnnumberend.md)|Recupera el número de columna donde finaliza la expresión o instrucción.|
|[IDiaLineNumber::get_addressSection](../../debugger/debug-interface-access/idialinenumber-get-addresssection.md)|Recupera la parte de la sección de la dirección de memoria donde comienza un bloque.|
|[IDiaLineNumber::get_addressOffset](../../debugger/debug-interface-access/idialinenumber-get-addressoffset.md)|Recupera la parte de desplazamiento de la dirección de memoria donde comienza un bloque.|
|[IDiaLineNumber::get_relativeVirtualAddress](../../debugger/debug-interface-access/idialinenumber-get-relativevirtualaddress.md)|Recupera la dirección virtual relativa (RVA) de la imagen de un bloque.|
|[IDiaLineNumber::get_virtualAddress](../../debugger/debug-interface-access/idialinenumber-get-virtualaddress.md)|Recupera la dirección virtual (VA) de un bloque.|
|[IDiaLineNumber::get_length](../../debugger/debug-interface-access/idialinenumber-get-length.md)|Recupera el número de bytes de un bloque.|
|[IDiaLineNumber::get_sourceFileId](../../debugger/debug-interface-access/idialinenumber-get-sourcefileid.md)|Recupera un identificador único del archivo de código fuente para el archivo de código fuente que ha contribuido a esta línea.|
|[IDiaLineNumber::get_statement](../../debugger/debug-interface-access/idialinenumber-get-statement.md)|Recupera una marca que indica que esta información de línea describe el principio de una instrucción en el origen del programa.|
|[IDiaLineNumber::get_compilandId](../../debugger/debug-interface-access/idialinenumber-get-compilandid.md)|Recupera el identificador único para la compilación que ha contribuido a esta línea.|

## <a name="remarks"></a>Comentarios

## <a name="notes-for-callers"></a>Notas para llamadores
Obtenga esta interfaz mediante una llamada a los métodos [IDiaEnumLineNumbers:: Item](../../debugger/debug-interface-access/idiaenumlinenumbers-item.md) o [IDiaEnumLineNumbers:: Next](../../debugger/debug-interface-access/idiaenumlinenumbers-next.md) .

## <a name="example"></a>Ejemplo
La siguiente función muestra los números de línea utilizados en una función (representada por `pSymbol`).

```C++
void dumpFunctionLines( IDiaSymbol* pSymbol, IDiaSession* pSession )
{
    ULONGLONG length = 0;
    DWORD     isect  = 0;
    DWORD     offset = 0;

    pSymbol->get_addressSection( &isect );
    pSymbol->get_addressOffset( &offset );
    pSymbol->get_length( &length );
    if ( isect != 0 && length > 0 )
    {
        CComPtr< IDiaEnumLineNumbers > pLines;
        if ( SUCCEEDED( pSession->findLinesByAddr(
                                      isect,
                                      offset,
                                      static_cast<DWORD>( length ),
                                      &pLines)
                      )
           )
        {
            CComPtr< IDiaLineNumber > pLine;
            DWORD celt      = 0;
            bool  firstLine = true;

            while ( SUCCEEDED( pLines->Next( 1, &pLine, &celt ) ) &&
                    celt == 1 )
            {
                DWORD offset;
                DWORD seg;
                DWORD linenum;
                CComPtr< IDiaSymbol >     pComp;
                CComPtr< IDiaSourceFile > pSrc;

                pLine->get_compiland( &pComp );
                pLine->get_sourceFile( &pSrc );
                pLine->get_addressSection( &seg );
                pLine->get_addressOffset( &offset );
                pLine->get_lineNumber( &linenum );
                printf( "\tline %d at 0x%x:0x%x\n", linenum, seg, offset );
                pLine = NULL;
                if ( firstLine )
                {
                    // sanity check
                    CComPtr< IDiaEnumLineNumbers > pLinesByLineNum;
                    if ( SUCCEEDED( pSession->findLinesByLinenum(
                                                  pComp,
                                                  pSrc,
                                                  linenum,
                                                  0,
                                                  &pLinesByLineNum)
                                  )
                       )
                    {
                        CComPtr< IDiaLineNumber > pLine;
                        DWORD celt;
                        while ( SUCCEEDED( pLinesByLineNum->Next( 1, &pLine, &celt ) ) &&
                                celt == 1 )
                        {
                            DWORD offset;
                            DWORD seg;
                            DWORD linenum;

                            pLine->get_addressSection( &seg );
                            pLine->get_addressOffset( &offset );
                            pLine->get_lineNumber( &linenum );
                            printf( "\t\tfound line %d at 0x%x:0x%x\n", linenum, seg, offset );
                            pLine = NULL;
                        }
                    }
                    firstLine = false;
                }
            }
        }
    }
}
```

## <a name="requirements"></a>Requisitos
Encabezado: Dia2. h

Biblioteca: diaguids. lib

DLL: msdia80.dll

## <a name="see-also"></a>Vea también
- [Interfaces (Debug Interface Access SDK)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)
- [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)
- [IDiaEnumLineNumbers::Item](../../debugger/debug-interface-access/idiaenumlinenumbers-item.md)
- [IDiaEnumLineNumbers::Next](../../debugger/debug-interface-access/idiaenumlinenumbers-next.md)
