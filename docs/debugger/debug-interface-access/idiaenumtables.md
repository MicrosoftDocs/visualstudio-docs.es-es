---
title: "IDiaEnumTables | Microsoft Docs"
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
  - "IDiaEnumTables (interfaz)"
ms.assetid: 016190c5-09e4-48f2-bf60-9b02603a03e0
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# IDiaEnumTables
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Muestra las distintas tablas contenidas en el origen de datos.  
  
## Sintaxis  
  
```  
IDiaEnumTables : IUnknown  
```  
  
## métodos en el orden de Vtable  
 La tabla siguiente se muestran los métodos de `IDiaEnumTables`.  
  
|Método|Descripción|  
|------------|-----------------|  
|[IDiaEnumTables::get\_\_NewEnum](../../debugger/debug-interface-access/idiaenumtables-get-newenum.md)|recupera la versión de [IEnumVARIANT Interface](http://msdn.microsoft.com/es-es/139e3c93-faef-4003-9079-e0e94494db3e) de este enumerador.|  
|[IDiaEnumTables::get\_Count](../../debugger/debug-interface-access/idiaenumtables-get-count.md)|recupera el número de tablas.|  
|[IDiaEnumTables::Item](../../debugger/debug-interface-access/idiaenumtables-item.md)|Recupera una tabla mediante un índice o nombre.|  
|[IDiaEnumTables::Next](../../debugger/debug-interface-access/idiaenumtables-next.md)|recupera un número especificado de tablas en la secuencia de la enumeración.|  
|[IDiaEnumTables::Skip](../../debugger/debug-interface-access/idiaenumtables-skip.md)|Omite un número especificado de tablas en una secuencia de enumeración.|  
|[IDiaEnumTables::Reset](../../debugger/debug-interface-access/idiaenumtables-reset.md)|Restaura una secuencia de enumeración al principio.|  
|[IDiaEnumTables::Clone](../../debugger/debug-interface-access/idiaenumtables-clone.md)|Crea un enumerador que contiene al mismo estado de enumeración que el enumerador actual.|  
  
## Comentarios  
  
## Notas para los llamadores  
 Obtiene esta interfaz llamando al método de [IDiaSession::getEnumTables](../../debugger/debug-interface-access/idiasession-getenumtables.md) .  
  
## Ejemplo  
 este ejemplo muestra cómo obtener la interfaz de `IDiaEnumTables` de una sesión.  Para obtener un ejemplo completo de tablas mediante, vea la interfaz de [IDiaTable](../../debugger/debug-interface-access/idiatable.md) .  
  
```cpp#  
void ShowTableNames(IDiaSession *pSession)  
{  
    CComPtr<IDiaEnumTables> pTables;  
    if ( FAILED( psession->getEnumTables( &pTables ) ) )  
    {  
        Fatal( "getEnumTables" );  
    }  
    // Do something with table  
}  
```  
  
## Requisitos  
 encabezado: Dia2.h  
  
 biblioteca: diaguids.lib  
  
 DLL: msdia80.dll  
  
## Vea también  
 [Interfaces \(Debug Interface Access SDK\)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [IDiaSession::getEnumTables](../../debugger/debug-interface-access/idiasession-getenumtables.md)