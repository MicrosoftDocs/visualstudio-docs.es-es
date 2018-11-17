---
title: IDiaTable | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- IDiaTable interface
ms.assetid: c99a2c44-7b72-4e3c-b963-25fe3df3a555
caps.latest.revision: 18
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 03f93cb75ce675409adcceec3f08b172581a3d8b
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/16/2018
ms.locfileid: "51721992"
---
# <a name="idiatable"></a>IDiaTable
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Enumera una tabla de origen de datos DIA.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
IDiaTable : IEnumUnknown  
```  
  
## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable  
 La tabla siguiente muestran los métodos de `IDiaTable`.  
  
|Método|Descripción|  
|------------|-----------------|  
|[IDiaTable::get__NewEnum](../../debugger/debug-interface-access/idiatable-get-newenum.md)|Recupera el [interfaz IEnumVARIANT](http://msdn.microsoft.com/en-us/139e3c93-faef-4003-9079-e0e94494db3e) versión de este enumerador.|  
|[IDiaTable::get_name](../../debugger/debug-interface-access/idiatable-get-name.md)|Recupera el nombre de la tabla.|  
|[IDiaTable::get_Count](../../debugger/debug-interface-access/idiatable-get-count.md)|Recupera el número de elementos de la tabla.|  
|[IDiaTable::Item](../../debugger/debug-interface-access/idiatable-item.md)|Recupera una referencia a un índice de la entrada determinada.|  
  
## <a name="remarks"></a>Comentarios  
 Esta interfaz implementa la `IEnumUnknown` los métodos de enumeración en el espacio de nombres de ensamblados Microsoft.VisualStudio.OLE.Interop. El `IEnumUnknown` es mucho más eficaz para recorrer en iteración la tabla de contenido de la interfaz de enumeración el [Idiatable](../../debugger/debug-interface-access/idiatable-get-count.md) y [Idiatable](../../debugger/debug-interface-access/idiatable-item.md) métodos.  
  
 La interpretación de los `IUnknown` interfaz devuelto desde el `IDiaTable::Item` método o la `Next` método (en el espacio de nombres de ensamblados Microsoft.VisualStudio.OLE.Interop) es depende del tipo de tabla. Por ejemplo, si la `IDiaTable` interfaz representa una lista de orígenes insertados, el `IUnknown` se debe consultar la interfaz para el [IDiaInjectedSource](../../debugger/debug-interface-access/idiainjectedsource.md) interfaz.  
  
## <a name="notes-for-callers"></a>Notas para los llamadores  
 Esta interfaz se obtiene mediante una llamada a la [Idiaenumtables](../../debugger/debug-interface-access/idiaenumtables-item.md) o [Idiaenumtables](../../debugger/debug-interface-access/idiaenumtables-next.md) métodos.  
  
 Las interfaces siguientes se implementan con la `IDiaTable` interfaz (es decir, puede consultar el `IDiaTable` interfaz para una de las interfaces siguientes):  
  
-   [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)  
  
-   [IDiaEnumSourceFiles](../../debugger/debug-interface-access/idiaenumsourcefiles.md)  
  
-   [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)  
  
-   [IDiaEnumSectionContribs](../../debugger/debug-interface-access/idiaenumsectioncontribs.md)  
  
-   [IDiaEnumSegments](../../debugger/debug-interface-access/idiaenumsegments.md)  
  
-   [IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md)  
  
-   [IDiaEnumFrameData](../../debugger/debug-interface-access/idiaenumframedata.md)  
  
## <a name="example"></a>Ejemplo  
 La primera función, `ShowTableNames`, muestra los nombres de todas las tablas de la sesión. La segunda función, `GetTable`, busca en todas las tablas de una tabla que implementa la interfaz especificada. La tercera función, `UseTable`, se muestra cómo usar el `GetTable` función.  
  
> [!NOTE]
>  `CDiaBSTR` es una clase que encapsula un `BSTR` y controla automáticamente la liberación de la cadena de la creación de instancias se sale del ámbito.  
  
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
 Encabezado: Dia2.h  
  
 Biblioteca: diaguids.lib  
  
 Archivo DLL: msdia80.dll  
  
## <a name="see-also"></a>Vea también  
 [Interfaces (Debug Interface Access SDK)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [IDiaEnumTables](../../debugger/debug-interface-access/idiaenumtables.md)   
 [Idiaenumtables](../../debugger/debug-interface-access/idiaenumtables-item.md)   
 [IDiaEnumTables::Next](../../debugger/debug-interface-access/idiaenumtables-next.md)



