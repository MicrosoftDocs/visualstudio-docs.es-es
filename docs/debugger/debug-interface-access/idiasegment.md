---
title: IDiaSegment | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaSegment interface
ms.assetid: 384ae0e1-077e-4d4f-98de-ac43c32c882f
caps.latest.revision: "13"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 12bc8e73457c1afc4b1799549ad43974d5771252
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="idiasegment"></a>IDiaSegment
Asigna datos desde el número de sección a segmentos del espacio de direcciones.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
IDiaSegment : IUnknown  
```  
  
## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable  
 La tabla siguiente muestran los métodos de `IDiaSegment`.  
  
|Método|Descripción|  
|------------|-----------------|  
|[IDiaSegment::get_frame](../../debugger/debug-interface-access/idiasegment-get-frame.md)|Recupera el número de segmento.|  
|[IDiaSegment::get_offset](../../debugger/debug-interface-access/idiasegment-get-offset.md)|Recupera el desplazamiento en segmentos donde comienza la sección.|  
|[IDiaSegment::get_length](../../debugger/debug-interface-access/idiasegment-get-length.md)|Recupera el número de bytes en el segmento.|  
|[IDiaSegment::get_read](../../debugger/debug-interface-access/idiasegment-get-read.md)|Recupera una marca que indica si se puede leer el segmento.|  
|[IDiaSegment::get_write](../../debugger/debug-interface-access/idiasegment-get-write.md)|Recupera una marca que indica si se puede modificar el segmento.|  
|[IDiaSegment::get_execute](../../debugger/debug-interface-access/idiasegment-get-execute.md)|Recupera una marca que indica si el segmento es ejecutable.|  
|[IDiaSegment::get_addressSection](../../debugger/debug-interface-access/idiasegment-get-addresssection.md)|Recupera el número de sección que se asigna a este segmento.|  
|[IDiaSegment::get_relativeVirtualAddress](../../debugger/debug-interface-access/idiasegment-get-relativevirtualaddress.md)|Recupera la dirección virtual relativa (RVA) del principio de la sección.|  
|[IDiaSegment::get_virtualAddress](../../debugger/debug-interface-access/idiasegment-get-virtualaddress.md)|Recupera la dirección virtual (VA) del principio de la sección.|  
  
## <a name="remarks"></a>Comentarios  
 Dado que el SDK de DIA ya realiza traducciones desde el desplazamiento de la sección para direcciones virtuales relativas, la mayoría de las aplicaciones no hará que el uso de la información de la asignación de segmentos.  
  
## <a name="notes-for-callers"></a>Notas para los llamadores  
 Obtener esta interfaz mediante una llamada a la [idiaenumsegments:: Item](../../debugger/debug-interface-access/idiaenumsegments-item.md) o [idiaenumsegments:: Next](../../debugger/debug-interface-access/idiaenumsegments-next.md) métodos. Vea el ejemplo para obtener más información.  
  
## <a name="example"></a>Ejemplo  
 Esta función muestra la dirección de todos los segmentos en una tabla y el símbolo más cercano.  
  
```C++  
void ShowSegments(IDiaTable *pTable, IDiaSession *pSession)  
{  
    CComPtr<IDiaEnumSegments> pSegments;  
    if ( SUCCEEDED( pTable->QueryInterface(  
                                _uuidof( IDiaEnumSegments ),  
                               (void**)&pSegments )  
                  )  
       )  
    {  
        CComPtr<IDiaSegment> pSegment;  
        while ( SUCCEEDED( hr = pSegments->Next( 1, &pSegment, &celt ) ) &&  
                celt == 1 )  
        {  
            DWORD rva;  
            DWORD seg;  
  
            pSegment->get_addressSection( &seg );  
            if ( pSegment->get_relativeVirtualAddress( &rva ) == S_OK )  
            {  
                printf( "Segment %i addr: 0x%.8X\n", seg, rva );  
                pSegment = NULL;  
  
                CComPtr<IDiaSymbol> pSym;  
                if ( psession->findSymbolByRVA( rva, SymTagNull, &pSym ) == S_OK )  
                {  
                    CDiaBSTR name;  
                    DWORD    tag;  
  
                    pSym->get_symTag( &tag );  
                    pSym->get_name( &name );  
                    printf( "\tClosest symbol: %ws (%ws)\n",  
                            name != NULL ? name : L"",  
                            szTags[ tag ] );  
                }  
            }  
        }  
    }  
}  
```  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: Dia2.h  
  
 Biblioteca: diaguids.lib  
  
 DLL: msdia80.dll  
  
## <a name="see-also"></a>Vea también  
 [Interfaces (Debug Interface Access SDK)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [Idiaenumsegments:: Item](../../debugger/debug-interface-access/idiaenumsegments-item.md)   
 [IDiaEnumSegments::Next](../../debugger/debug-interface-access/idiaenumsegments-next.md)