---
title: Idiaenumsegments | Documentos de Microsoft
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
- IDiaEnumSegments::Item method
ms.assetid: ee44dd55-39a0-4b7b-97ff-2e1226eeb2bd
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7f7d98e160f3a0723293ce8349f475bf6519ed51
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49913701"
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
  
 Segmento  
 [out] Devuelve un [IDiaSegment](../../debugger/debug-interface-access/idiasegment.md) objeto que representa el segmento deseado.  
  
## <a name="return-value"></a>Valor devuelto  
 Si es correcto, devuelve `S_OK`; en caso contrario, devuelve un código de error.  
  
## <a name="see-also"></a>Vea también  
 [IDiaEnumSegments](../../debugger/debug-interface-access/idiaenumsegments.md)   
 [IDiaSegment](../../debugger/debug-interface-access/idiasegment.md)



