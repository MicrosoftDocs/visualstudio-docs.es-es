---
title: Idiaframedata | Microsoft Docs
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
- IDiaFrameData::get_relativeVirtualAddress method
ms.assetid: de070ef4-6c9d-43ca-911c-5245cbcb8dbe
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 20735a9c7efc1ce9676dbd4e5ac187c6a0dbd789
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49904497"
---
# <a name="idiaframedatagetrelativevirtualaddress"></a>IDiaFrameData::get_relativeVirtualAddress
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Recupera la dirección virtual relativa (RVA) del código para el marco.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp#  
HRESULT get_relativeVirtualAddress (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pRetVal`  
 [out] Devuelve la dirección virtual relativa del código para el marco.  
  
## <a name="return-value"></a>Valor devuelto  
 Si es correcto, devuelve `S_OK`. Devuelve `S_FALSE` si no se admite esta propiedad. De lo contrario, devuelve un código de error.  
  
## <a name="see-also"></a>Vea también  
 [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)



