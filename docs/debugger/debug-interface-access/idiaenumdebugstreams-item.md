---
title: "IDiaEnumDebugStreams::Item | Microsoft Docs"
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
  - "IDiaEnumDebugStreams::Item (método)"
ms.assetid: 6b388fe1-eabc-4720-9d59-dc09b0ceaeac
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDiaEnumDebugStreams::Item
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Recupera una secuencia de depuración por medio de un índice o nombre.  
  
## Sintaxis  
  
```cpp#  
HRESULT Item (   
   VARIANT                   index,  
   IDiaEnumDebugStreamData** stream  
);  
```  
  
#### Parámetros  
 índice  
 \[in\]  Índice o nombre de la secuencia de depuración que se recuperará.  Si se utiliza un tipo Variant entero, debe estar en el intervalo 0 a `count`\-1, donde es `count` que devuelve el método de [IDiaEnumDebugStreams::get\_Count](../../debugger/debug-interface-access/idiaenumdebugstreams-get-count.md) .  
  
 secuencia  
 \[out\]  Devuelve un objeto de [IDiaEnumDebugStreamData](../../debugger/debug-interface-access/idiaenumdebugstreamdata.md) que representa la secuencia especificada de depuración.  
  
## Valor devuelto  
 Si finaliza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.  
  
## Ejemplo  
  
```cpp#  
IDiaEnumDebugStreamData *GetStreamData(IDiaEnumDebugStreams *pStreamList,  
                                       LONG whichStream)  
{  
    IDiaEnumDebugStreamData *pStreamData = NULL;  
    if (pStreamList != NULL)  
    {  
        LONG numStreams = 0;  
        if (pStreamList->get_count(&numStreams) == S_OK &&  
            whichStream >= 0 && whichStream < numStreams)  
        {  
            VARIANT vIndex;  
            vIndex.vt   = VT_I4;  
            vIndex.lVal = whichStream;  
            if (pStreamList->Item(vIndex,&pStreamData) != S_OK)  
            {  
                 std::cerr << "Error retrieving stream " << whichStream << std::endl;  
            }  
        }  
    }  
    return(pStreamData);  
}  
```  
  
## Vea también  
 [IDiaEnumDebugStreamData](../../debugger/debug-interface-access/idiaenumdebugstreamdata.md)   
 [IDiaEnumDebugStreams](../../debugger/debug-interface-access/idiaenumdebugstreams.md)