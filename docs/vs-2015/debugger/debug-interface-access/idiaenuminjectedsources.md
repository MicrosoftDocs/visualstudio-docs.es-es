---
title: IDiaEnumInjectedSources | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumInjectedSources interface
ms.assetid: f97e2392-22e1-48da-b7ce-ad94c8b684b0
caps.latest.revision: 15
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: e710e586f3ece4fdf0cdbf9bee2bcc70f4ab87b5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "65687213"
---
# <a name="idiaenuminjectedsources"></a>IDiaEnumInjectedSources
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Enumerar los distintos orígenes insertados contenidos en el origen de datos.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
IDiaEnumInjectedSources : IUnknown  
```  
  
## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable  
 En la tabla siguiente se muestran los métodos de `IDiaEnumInjectedSources` .  
  
|Método|Descripción|  
|------------|-----------------|  
|[IDiaEnumInjectedSources::get__NewEnum](../../debugger/debug-interface-access/idiaenuminjectedsources-get-newenum.md)|Recupera la versión de la [interfaz IEnumVARIANT](https://msdn.microsoft.com/139e3c93-faef-4003-9079-e0e94494db3e) de este enumerador.|  
|[IDiaEnumInjectedSources::get_Count](../../debugger/debug-interface-access/idiaenuminjectedsources-get-count.md)|Recupera el número de orígenes insertados.|  
|[IDiaEnumInjectedSources::Item](../../debugger/debug-interface-access/idiaenuminjectedsources-item.md)|Recupera un origen insertado por medio de un índice.|  
|[IDiaEnumInjectedSources::Next](../../debugger/debug-interface-access/idiaenuminjectedsources-next.md)|Recupera un número especificado de orígenes insertados en la secuencia de enumeración.|  
|[IDiaEnumInjectedSources::Skip](../../debugger/debug-interface-access/idiaenuminjectedsources-skip.md)|Omite un número especificado de orígenes insertados en una secuencia de enumeración.|  
|[IDiaEnumInjectedSources::Reset](../../debugger/debug-interface-access/idiaenuminjectedsources-reset.md)|Restablece una secuencia de enumeración al principio.|  
|[IDiaEnumInjectedSources::Clone](../../debugger/debug-interface-access/idiaenuminjectedsources-clone.md)|Crea un enumerador que contiene el mismo estado de enumeración que el enumerador actual.|  
  
## <a name="remarks"></a>Observaciones  
  
## <a name="notes-for-callers"></a>Notas para llamadores  
 Esta interfaz se obtiene llamando al método [IDiaSession:: findInjectedSource](../../debugger/debug-interface-access/idiasession-findinjectedsource.md) con el nombre de un archivo de código fuente específico o llamando al método [IDiaSession:: GETENUMTABLES](../../debugger/debug-interface-access/idiasession-getenumtables.md) con el GUID de la `IDiaEnumInjectedSources` interfaz.  
  
## <a name="example"></a>Ejemplo  
 En este ejemplo se muestra cómo obtener (la `GetEnumInjectedSources` función) y usar (la `DumpAllInjectedSources` función) la `IDiaEnumInjectedSources` interfaz. Vea la interfaz [IDiaPropertyStorage](../../debugger/debug-interface-access/idiapropertystorage.md) para obtener una implementación de la `PrintPropertyStorage` función. Para obtener una salida alternativa, vea la interfaz [IDiaInjectedSource](../../debugger/debug-interface-access/idiainjectedsource.md) .  
  
```cpp#  
  
IDiaEnumInjectedSources* GetEnumInjectedSources(IDiaSession *pSession)  
{  
    IDiaEnumInjectedSources* pUnknown    = NULL;  
    REFIID                   iid         = __uuidof(IDiaEnumInjectedSources);  
    IDiaEnumTables*          pEnumTables = NULL;  
    IDiaTable*               pTable      = NULL;  
    ULONG                    celt        = 0;  
  
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
  
void DumpAllInjectedSources( IDiaSession* pSession)  
{  
    IDiaEnumInjectedSources* pEnumInjSources;  
  
    pEnumInjSources = GetEnumInjectedSources(pSession);  
    if (pEnumInjSources != NULL)  
    {  
        IDiaInjectedSource* pInjSource;  
        ULONG celt = 0;  
  
        while(pEnumInjSources->Next(1, &pInjSource, &celt) == S_OK &&  
              celt == 1)  
        {  
            IDiaPropertyStorage *pPropertyStorage;  
            if (pInjSource->QueryInterface(__uuidof(IDiaPropertyStorage),  
                                           (void **)&pPropertyStorage) == S_OK)  
            {  
                PrintPropertyStorage(pPropertyStorage);  
                pPropertyStorage->Release();  
            }  
            pInjSource->Release();  
        }  
        pEnumInjSources->Release();  
    }  
}  
```  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: Dia2. h  
  
 Biblioteca: diaguids. lib  
  
 DLL: msdia80.dll  
  
## <a name="see-also"></a>Consulte también  
 [Interfaces (Debug Interface Access SDK)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [IDiaSession:: findInjectedSource](../../debugger/debug-interface-access/idiasession-findinjectedsource.md)   
 [IDiaSession:: getEnumTables](../../debugger/debug-interface-access/idiasession-getenumtables.md)   
 [IDiaPropertyStorage](../../debugger/debug-interface-access/idiapropertystorage.md)   
 [IDiaInjectedSource](../../debugger/debug-interface-access/idiainjectedsource.md)
