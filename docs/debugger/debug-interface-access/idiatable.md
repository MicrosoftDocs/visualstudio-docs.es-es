---
title: IDiaTable | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaTable interface
ms.assetid: c99a2c44-7b72-4e3c-b963-25fe3df3a555
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: e95c469bb3a1d8747a7f1dabfadec24dc991730c
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2018
---
# <a name="idiatable"></a>IDiaTable
Enumera una tabla de origen de datos DIA.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
IDiaTable : IEnumUnknown  
```  
  
## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable  
 La tabla siguiente muestran los métodos de `IDiaTable`.  
  
|Método|Descripción|  
|------------|-----------------|  
|[IDiaTable::get__NewEnum](../../debugger/debug-interface-access/idiatable-get-newenum.md)|Recupera el [interfaz IEnumVARIANT](http://msdn.microsoft.com/en-us/139e3c93-faef-4003-9079-e0e94494db3e) versión de este enumerador.|  
|[IDiaTable::get_name](../../debugger/debug-interface-access/idiatable-get-name.md)|Recupera el nombre de la tabla.|  
|[IDiaTable::get_Count](../../debugger/debug-interface-access/idiatable-get-count.md)|Recupera el número de elementos de la tabla.|  
|[IDiaTable::Item](../../debugger/debug-interface-access/idiatable-item.md)|Recupera una referencia a un índice de entrada determinada.|  
  
## <a name="remarks"></a>Comentarios  
 Esta interfaz implementa la `IEnumUnknown` métodos de enumeración en el espacio de nombres de ensamblados Microsoft.VisualStudio.OLE.Interop. El `IEnumUnknown` interfaz de enumeración es mucho más eficaz para recorrer en iteración la tabla de contenido de la [idiatable:: Get_count](../../debugger/debug-interface-access/idiatable-get-count.md) y [idiatable:: Item](../../debugger/debug-interface-access/idiatable-item.md) métodos.  
  
 La interpretación de la `IUnknown` interfaz devuelto desde el `IDiaTable::Item` método o la `Next` método (en el espacio de nombres de ensamblados Microsoft.VisualStudio.OLE.Interop) es depende del tipo de tabla. Por ejemplo, si la `IDiaTable` interfaz representa una lista de orígenes insertados, la `IUnknown` interfaz se debe consultar para la [IDiaInjectedSource](../../debugger/debug-interface-access/idiainjectedsource.md) interfaz.  
  
## <a name="notes-for-callers"></a>Notas para los llamadores  
 Obtener esta interfaz mediante una llamada a la [idiaenumtables:: Item](../../debugger/debug-interface-access/idiaenumtables-item.md) o [idiaenumtables:: Next](../../debugger/debug-interface-access/idiaenumtables-next.md) métodos.  
  
 Las interfaces siguientes se implementan con la `IDiaTable` interfaz (es decir, puede consultar el `IDiaTable` interfaz para una de las interfaces siguientes):  
  
-   [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)  
  
-   [IDiaEnumSourceFiles](../../debugger/debug-interface-access/idiaenumsourcefiles.md)  
  
-   [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)  
  
-   [IDiaEnumSectionContribs](../../debugger/debug-interface-access/idiaenumsectioncontribs.md)  
  
-   [IDiaEnumSegments](../../debugger/debug-interface-access/idiaenumsegments.md)  
  
-   [IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md)  
  
-   [IDiaEnumFrameData](../../debugger/debug-interface-access/idiaenumframedata.md)  
  
## <a name="example"></a>Ejemplo  
 La primera función, `ShowTableNames`, muestra los nombres de todas las tablas de la sesión. La segunda función, `GetTable`, busca en todas las tablas de una tabla que implementa la interfaz especificada. La tercera función, `UseTable`, muestra cómo utilizar el `GetTable` función.  
  
> [!NOTE]
>  `CDiaBSTR` es una clase que encapsula un `BSTR` y controla automáticamente la cadena que libera cuando la creación de instancias se sale del ámbito.  
  
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
 Encabezado: Dia2.h  
  
 Biblioteca: diaguids.lib  
  
 DLL: msdia80.dll  
  
## <a name="see-also"></a>Vea también  
 [Interfaces (Debug Interface Access SDK)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [IDiaEnumTables](../../debugger/debug-interface-access/idiaenumtables.md)   
 [Idiaenumtables:: Item](../../debugger/debug-interface-access/idiaenumtables-item.md)   
 [IDiaEnumTables::Next](../../debugger/debug-interface-access/idiaenumtables-next.md)