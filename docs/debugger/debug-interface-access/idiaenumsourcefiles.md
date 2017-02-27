---
title: "IDiaEnumSourceFiles | Microsoft Docs"
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
  - "IDiaEnumSourceFiles (interfaz)"
ms.assetid: 5c0779a6-a2ea-408a-90da-ebdecf2b83c0
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# IDiaEnumSourceFiles
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Muestra los distintos archivos de código fuente contenidos en el origen de datos.  
  
## Sintaxis  
  
```  
IDiaEnumSourceFiles : IUknown  
```  
  
## métodos en el orden de Vtable  
 La tabla siguiente se muestran los métodos de `IDiaEnumSourceFiles`.  
  
|Método|Descripción|  
|------------|-----------------|  
|[IDiaEnumSourceFiles::get\_\_NewEnum](../../debugger/debug-interface-access/idiaenumsourcefiles-get-newenum.md)|recupera la versión de `IEnumVARIANT Interface` de este enumerador.|  
|[IDiaEnumSourceFiles::get\_Count](../../debugger/debug-interface-access/idiaenumsourcefiles-get-count.md)|recupera el número de archivos de código fuente.|  
|[IDiaEnumSourceFiles::Item](../../debugger/debug-interface-access/idiaenumsourcefiles-item.md)|recupera un archivo de código fuente mediante un índice.|  
|[IDiaEnumSourceFiles::Next](../../debugger/debug-interface-access/idiaenumsourcefiles-next.md)|Recupera un número especificado de archivos de código fuente de la secuencia de la enumeración.|  
|[IDiaEnumSourceFiles::Skip](../../debugger/debug-interface-access/idiaenumsourcefiles-skip.md)|Omite un número especificado de archivos de código fuente en una secuencia de enumeración.|  
|[IDiaEnumSourceFiles::Reset](../../debugger/debug-interface-access/idiaenumsourcefiles-reset.md)|Restaura una secuencia de enumeración al principio.|  
|[IDiaEnumSourceFiles::Clone](../../debugger/debug-interface-access/idiaenumsourcefiles-clone.md)|Crea un enumerador que contiene al mismo estado de enumeración que el enumerador actual.|  
  
## Comentarios  
  
## Notas para los llamadores  
 Obtiene esta interfaz llamando al método de `QueryInterface` en un objeto de [IDiaTable](../../debugger/debug-interface-access/idiatable.md) .  Vea el ejemplo para obtener detalles.  
  
## Ejemplo  
 Este ejemplo muestra cómo obtener la interfaz de `IDiaEnumSourceFiles` de la lista de tablas de un objeto de sesión del diámetro.  Para obtener un ejemplo de tener acceso a la información de archivo de código fuente, vea la interfaz de [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md) .  
  
```cpp#  
  
IDiaEnumSourceFiles* GetEnumSourceFiless(IDiaSession *pSession)  
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
  
## Requisitos  
 encabezado: Dia2.h  
  
 biblioteca: diaguids.lib  
  
 DLL: msdia80.dll  
  
## Vea también  
 [Interfaces \(Debug Interface Access SDK\)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [IDiaSession::findFile](../../debugger/debug-interface-access/idiasession-findfile.md)   
 [IDiaSession::findLinesByLinenum](../../debugger/debug-interface-access/idiasession-findlinesbylinenum.md)   
 [IDiaTable](../../debugger/debug-interface-access/idiatable.md)