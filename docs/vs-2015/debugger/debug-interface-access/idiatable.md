---
title: IDiaTable | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaTable interface
ms.assetid: c99a2c44-7b72-4e3c-b963-25fe3df3a555
caps.latest.revision: 18
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 5b9c9f85ffbf4eed2fdc305a64bd3f32822dacd6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "65682787"
---
# <a name="idiatable"></a>IDiaTable
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Enumera una tabla de origen de datos DIA.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
IDiaTable : IEnumUnknown  
```  
  
## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable  
 En la tabla siguiente se muestran los métodos de `IDiaTable` .  
  
|Método|Descripción|  
|------------|-----------------|  
|[IDiaTable::get__NewEnum](../../debugger/debug-interface-access/idiatable-get-newenum.md)|Recupera la versión de la [interfaz IEnumVARIANT](https://msdn.microsoft.com/139e3c93-faef-4003-9079-e0e94494db3e) de este enumerador.|  
|[IDiaTable::get_name](../../debugger/debug-interface-access/idiatable-get-name.md)|Recupera el nombre de la tabla.|  
|[IDiaTable::get_Count](../../debugger/debug-interface-access/idiatable-get-count.md)|Recupera el número de elementos de la tabla.|  
|[IDiaTable::Item](../../debugger/debug-interface-access/idiatable-item.md)|Recupera una referencia a un índice de entrada determinado.|  
  
## <a name="remarks"></a>Observaciones  
 Esta interfaz implementa los `IEnumUnknown` métodos de enumeración en el espacio de nombres Microsoft. VisualStudio. OLE. Interop. La `IEnumUnknown` interfaz de enumeración es mucho más eficaz para recorrer en iteración el contenido de la tabla que los métodos [IDiaTable:: Get_Count](../../debugger/debug-interface-access/idiatable-get-count.md) y [IDiaTable:: Item](../../debugger/debug-interface-access/idiatable-item.md) .  
  
 La interpretación de la `IUnknown` interfaz devuelta por el `IDiaTable::Item` método o el `Next` método (en el espacio de nombres Microsoft. VisualStudio. OLE. Interop) depende del tipo de tabla. Por ejemplo, si la `IDiaTable` interfaz representa una lista de orígenes insertados, `IUnknown` se debe consultar la interfaz para la interfaz [IDiaInjectedSource](../../debugger/debug-interface-access/idiainjectedsource.md) .  
  
## <a name="notes-for-callers"></a>Notas para llamadores  
 Obtenga esta interfaz mediante una llamada a los métodos [IDiaEnumTables:: Item](../../debugger/debug-interface-access/idiaenumtables-item.md) o [IDiaEnumTables:: Next](../../debugger/debug-interface-access/idiaenumtables-next.md) .  
  
 Las siguientes interfaces se implementan con la `IDiaTable` interfaz (es decir, se puede consultar la `IDiaTable` interfaz para una de las interfaces siguientes):  
  
- [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)  
  
- [IDiaEnumSourceFiles](../../debugger/debug-interface-access/idiaenumsourcefiles.md)  
  
- [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)  
  
- [IDiaEnumSectionContribs](../../debugger/debug-interface-access/idiaenumsectioncontribs.md)  
  
- [IDiaEnumSegments](../../debugger/debug-interface-access/idiaenumsegments.md)  
  
- [IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md)  
  
- [IDiaEnumFrameData](../../debugger/debug-interface-access/idiaenumframedata.md)  
  
## <a name="example"></a>Ejemplo  
 La primera función, `ShowTableNames` , muestra los nombres de todas las tablas de la sesión. La segunda función, `GetTable` , busca en todas las tablas una tabla que implementa una interfaz especificada. La tercera función, `UseTable` , muestra cómo usar la `GetTable` función.  
  
> [!NOTE]
> `CDiaBSTR` es una clase que ajusta un `BSTR` y controla automáticamente la liberación de la cadena cuando la creación de instancias sale del ámbito.  
  
```cpp#  
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
  
## <a name="see-also"></a>Consulte también  
 [Interfaces (Debug Interface Access SDK)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [IDiaEnumTables](../../debugger/debug-interface-access/idiaenumtables.md)   
 [IDiaEnumTables:: Item](../../debugger/debug-interface-access/idiaenumtables-item.md)   
 [IDiaEnumTables::Next](../../debugger/debug-interface-access/idiaenumtables-next.md)
