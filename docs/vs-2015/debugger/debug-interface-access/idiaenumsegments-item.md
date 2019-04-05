---
title: IDiaEnumSegments::Item | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumSegments::Item method
ms.assetid: ee44dd55-39a0-4b7b-97ff-2e1226eeb2bd
caps.latest.revision: 10
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 1e69c8123af3ac9061141058d5eb41178e5cd0e4
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2019
ms.locfileid: "58997491"
---
# <a name="idiaenumsegmentsitem"></a>IDiaEnumSegments::Item
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Recupera un segmento por medio de un índice.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp#  
HRESULT Item (   
   DWORD         index,  
   IDiaSegment** segment  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 índice  
 [in] Índice de la [IDiaSegment](../../debugger/debug-interface-access/idiasegment.md) objeto va a recuperar. El índice está en el intervalo de 0 a `count`-1, donde `count` devuelto por la [Idiaenumsegments](../../debugger/debug-interface-access/idiaenumsegments-get-count.md) método.  
  
 segment  
 [out] Devuelve un [IDiaSegment](../../debugger/debug-interface-access/idiasegment.md) objeto que representa el segmento deseado.  
  
## <a name="return-value"></a>Valor devuelto  
 Si es correcto, devuelve `S_OK`; en caso contrario, devuelve un código de error.  
  
## <a name="see-also"></a>Vea también  
 [IDiaEnumSegments](../../debugger/debug-interface-access/idiaenumsegments.md)   
 [IDiaSegment](../../debugger/debug-interface-access/idiasegment.md)
