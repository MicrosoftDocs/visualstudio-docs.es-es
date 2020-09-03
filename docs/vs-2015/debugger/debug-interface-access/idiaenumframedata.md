---
title: IDiaEnumFrameData | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumFrameData interface
ms.assetid: 2ca7fd5a-b2fa-4b3a-9492-0263eafc435b
caps.latest.revision: 16
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 3b3e2436d4b4eed6ac86591821090c89a538e06b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "68190785"
---
# <a name="idiaenumframedata"></a>IDiaEnumFrameData
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Enumera los distintos elementos de datos de marco incluidos en el origen de datos.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
IDiaEnumFrameData : IUnknown  
```  
  
## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable  
 En la tabla siguiente se muestran los métodos de `IDiaEnumFrameData` .  
  
|Método|Descripción|  
|------------|-----------------|  
|[IDiaEnumFrameData::get__NewEnum](../../debugger/debug-interface-access/idiaenumframedata-get-newenum.md)|Recupera la `IEnumVARIANT Interface` versión de este enumerador.|  
|[IDiaEnumFrameData::get_Count](../../debugger/debug-interface-access/idiaenumframedata-get-count.md)|Recupera el número de elementos de datos de marco.|  
|[IDiaEnumFrameData::Item](../../debugger/debug-interface-access/idiaenumframedata-item.md)|Recupera un elemento de datos de marco por medio de un índice.|  
|[IDiaEnumFrameData::Next](../../debugger/debug-interface-access/idiaenumframedata-next.md)|Recupera un número especificado de elementos de datos de marco en la secuencia de enumeración.|  
|[IDiaEnumFrameData::Skip](../../debugger/debug-interface-access/idiaenumframedata-skip.md)|Omite un número especificado de elementos de datos de marco en una secuencia de enumeración.|  
|[IDiaEnumFrameData::Reset](../../debugger/debug-interface-access/idiaenumframedata-reset.md)|Restablece una secuencia de enumeración al principio.|  
|[IDiaEnumFrameData::Clone](../../debugger/debug-interface-access/idiaenumframedata-clone.md)|Crea un enumerador que contiene el mismo estado de enumeración que el enumerador actual.|  
|[IDiaEnumFrameData::frameByRVA](../../debugger/debug-interface-access/idiaenumframedata-framebyrva.md)|Devuelve un marco por dirección virtual relativa (RVA).|  
|[IDiaEnumFrameData::frameByVA](../../debugger/debug-interface-access/idiaenumframedata-framebyva.md)|Devuelve un marco por dirección virtual (VA).|  
  
## <a name="remarks"></a>Observaciones  
  
## <a name="notes-for-callers"></a>Notas para llamadores  
 Obtenga esta interfaz del método [IDiaSession:: getEnumTables](../../debugger/debug-interface-access/idiasession-getenumtables.md) . Consulte el ejemplo para más información.  
  
## <a name="example"></a>Ejemplo  
 En este ejemplo se muestra cómo obtener (la `GetEnumFrameData` función) y usar (la `ShowFrameData` función) la `IDiaEnumFrameData` interfaz. Vea la interfaz [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md) para obtener un ejemplo de la `PrintFrameData` función.  
  
```cpp#  
  
      IDiaEnumFrameData* GetEnumFrameData(IDiaSession *pSession)  
{  
    IDiaEnumFrameData* pUnknown    = NULL;  
    REFIID             iid         = __uuidof(IDiaEnumFrameData);  
    IDiaEnumTables*    pEnumTables = NULL;  
    IDiaTable*         pTable      = NULL;  
    ULONG              celt        = 0;  
  
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
  
void ShowFrameData(IDiaSession *pSession)  
{  
    IDiaEnumFrameData* pEnumFrameData = GetEnumFrameData(pSession);;  
  
    if (pEnumFrameData != NULL)  
    {  
        IDiaFrameData* pFrameData;  
        ULONG celt = 0;  
  
        while(pEnumFrameData->Next(1, &pFrameData, &celt) == S_OK &&  
              celt == 1)  
        {  
            PrintFrameData(pFrameData);  
            pFrameData->Release();  
        }  
        pEnumFrameData->Release();   
    }  
}  
```  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** Dia2. h  
  
 **Biblioteca:** diaguids. lib  
  
 **DLL:** msdia80.dll  
  
## <a name="see-also"></a>Consulte también  
 [Interfaces (Debug Interface Access SDK)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [IDiaSession:: getEnumTables](../../debugger/debug-interface-access/idiasession-getenumtables.md)   
 [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)
