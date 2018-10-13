---
title: Idiaenumdebugstreamdata | Microsoft Docs
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
- IDiaEnumDebugStreamData::Item method
ms.assetid: 761e61a5-44a6-4d5d-a98e-c2e9b89d2343
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0450871ce408477f4e324569df9617427c5e81d4
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49173100"
---
# <a name="idiaenumdebugstreamdataitem"></a>IDiaEnumDebugStreamData::Item
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Recupera el registro especificado.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp#  
HRESULT Item (   
   DWORD  index,  
   DWORD  cbData,  
   DWORD* pcbData,  
   BYTE   data[]  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 índice  
 [in] Índice del registro que va a recuperar. El índice está en el intervalo de 0 a `count`-1, donde `count` devuelto por [Idiaenumdebugstreamdata](../../debugger/debug-interface-access/idiaenumdebugstreamdata-get-count.md).  
  
 cbData  
 [in] Tamaño del búfer de datos, en bytes.  
  
 pcbData  
 [out] Devuelve el número de bytes devueltos. Si `data` es `NULL`, a continuación, `pcbData` contiene el número total de bytes de datos disponibles en el registro especificado.  
  
 datos]  
 [out] Un búfer que se rellena con los datos de registro de flujo de depuración.  
  
## <a name="return-value"></a>Valor devuelto  
 Si es correcto, devuelve `S_OK`; en caso contrario, devuelve un código de error. Devuelve `E_INVALIDARG` de parámetros no válidos y si el `index` parámetro está fuera de los límites.  
  
## <a name="see-also"></a>Vea también  
 [IDiaEnumDebugStreamData](../../debugger/debug-interface-access/idiaenumdebugstreamdata.md)   
 [Idiaenumdebugstreamdata](../../debugger/debug-interface-access/idiaenumdebugstreamdata-next.md)   
 [Idiaenumdebugstreams](../../debugger/debug-interface-access/idiaenumdebugstreams-item.md)   
 [Idiaenumdebugstreamdata](../../debugger/debug-interface-access/idiaenumdebugstreamdata-get-count.md)   
 [IDiaEnumDebugStreamData::Skip](../../debugger/debug-interface-access/idiaenumdebugstreamdata-skip.md)



