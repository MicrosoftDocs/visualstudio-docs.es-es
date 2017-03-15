---
title: "IDiaTable | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IDiaTable (interfaz)"
ms.assetid: c99a2c44-7b72-4e3c-b963-25fe3df3a555
caps.latest.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 15
---
# IDiaTable
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Muestra una tabla de origen de datos del diámetro.  
  
## Sintaxis  
  
```  
IDiaTable : IEnumUnknown  
```  
  
## métodos en el orden de Vtable  
 La tabla siguiente se muestran los métodos de `IDiaTable`.  
  
|Método|Descripción|  
|------------|-----------------|  
|[IDiaTable::get\_\_NewEnum](../../debugger/debug-interface-access/idiatable-get-newenum.md)|recupera la versión de [IEnumVARIANT Interface](http://msdn.microsoft.com/es-es/139e3c93-faef-4003-9079-e0e94494db3e) de este enumerador.|  
|[IDiaTable::get\_name](../../debugger/debug-interface-access/idiatable-get-name.md)|recupera el nombre de la tabla.|  
|[IDiaTable::get\_Count](../../debugger/debug-interface-access/idiatable-get-count.md)|Recupera el número de elementos de la tabla.|  
|[IDiaTable::Item](../../debugger/debug-interface-access/idiatable-item.md)|recupera una referencia a un índice determinado de la entrada.|  
  
## Comentarios  
 Esta interfaz implementa los métodos de enumeración de `IEnumUnknown` en el espacio de nombres Microsoft.VisualStudio.OLE.Interop.  La interfaz de enumeración de `IEnumUnknown` es mucho más eficaz para iterar sobre tablas de contenido que los métodos de [IDiaTable::get\_Count](../../debugger/debug-interface-access/idiatable-get-count.md) y de [IDiaTable::Item](../../debugger/debug-interface-access/idiatable-item.md) .  
  
 La interpretación de la interfaz de `IUnknown` devuelto del método de `IDiaTable::Item` o método de `Next` \(en el espacio de nombres Microsoft.VisualStudio.OLE.Interop\) depende del tipo de tabla.  Por ejemplo, si la interfaz de `IDiaTable` representa una lista de orígenes insertados, la interfaz de `IUnknown` debe consultar la interfaz de [IDiaInjectedSource](../../debugger/debug-interface-access/idiainjectedsource.md) .  
  
## Notas para los llamadores  
 Obtiene esta interfaz llamando a los métodos de [IDiaEnumTables::Item](../../debugger/debug-interface-access/idiaenumtables-item.md) o de [IDiaEnumTables::Next](../../debugger/debug-interface-access/idiaenumtables-next.md) .  
  
 Las interfaces siguientes se implementan con la interfaz de `IDiaTable` \(es decir, puede ver la interfaz de `IDiaTable` para una de las interfaces siguientes\):  
  
-   [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)  
  
-   [IDiaEnumSourceFiles](../../debugger/debug-interface-access/idiaenumsourcefiles.md)  
  
-   [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)  
  
-   [IDiaEnumSectionContribs](../../debugger/debug-interface-access/idiaenumsectioncontribs.md)  
  
-   [IDiaEnumSegments](../../debugger/debug-interface-access/idiaenumsegments.md)  
  
-   [IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md)  
  
-   [IDiaEnumFrameData](../../debugger/debug-interface-access/idiaenumframedata.md)  
  
## Ejemplo  
 La primera función, `ShowTableNames`, muestra los nombres de todas las tablas en la sesión.  La segunda función, `GetTable`, busca en todas las tablas para una tabla que implementa una interfaz especificada.  La tercera función, `UseTable`, se muestra cómo utilizar la función de `GetTable` .  
  
> [!NOTE]
>  `CDiaBSTR` es una clase que contiene `BSTR` y automáticamente identificadores que liberan la cadena cuando la instancia sale del ámbito.  
  
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
  
## Requisitos  
 encabezado: Dia2.h  
  
 biblioteca: diaguids.lib  
  
 DLL: msdia80.dll  
  
## Vea también  
 [Interfaces \(Debug Interface Access SDK\)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [IDiaEnumTables](../../debugger/debug-interface-access/idiaenumtables.md)   
 [IDiaEnumTables::Item](../../debugger/debug-interface-access/idiaenumtables-item.md)   
 [IDiaEnumTables::Next](../../debugger/debug-interface-access/idiaenumtables-next.md)