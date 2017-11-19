---
title: 'Idiaenumframedata:: Item | Documentos de Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaEnumFrameData::Item method
ms.assetid: 2761a72d-1868-4f5b-a32e-c2a1d9358c91
caps.latest.revision: "7"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a33a0dad9f315f929a2ca0b032f8907f9567435b
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="idiaenumframedataitem"></a>IDiaEnumFrameData::Item
Recupera un elemento de datos de marco por medio de un índice.  
  
## <a name="syntax"></a>Sintaxis  
  
```C++  
HRESULT Item (   
   DWORD           index,  
   IDiaFrameData** section  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 índice  
 [in] Índice de la [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md) objeto va a recuperar. El índice se encuentra en el intervalo de 0 a `count`-1, donde `count` devuelto por la [idiaenumframedata:: Get_count](../../debugger/debug-interface-access/idiaenumframedata-get-count.md) método.  
  
 section  
 [out] Devuelve un [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md) objeto que representa el elemento de datos de marco deseado.  
  
## <a name="return-value"></a>Valor devuelto  
 Si se realiza correctamente, devuelve `S_OK`; en caso contrario, devuelve un código de error.  
  
## <a name="see-also"></a>Vea también  
 [IDiaEnumFrameData](../../debugger/debug-interface-access/idiaenumframedata.md)   
 [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)