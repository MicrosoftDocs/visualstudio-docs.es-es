---
title: Idiaframedata | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaFrameData::get_type method
ms.assetid: efca38b5-c479-4d0a-a164-f903f25c5509
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 0209a715ece3e1fa760080ad7ccf0803d11950df
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49834596"
---
# <a name="idiaframedatagettype"></a>IDiaFrameData::get_type
Recupera el tipo de marco específicas del compilador.  
  
## <a name="syntax"></a>Sintaxis  
  
```C++  
HRESULT get_type (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pRetVal`  
 [out] Devuelve un valor de la [StackFrameTypeEnum (enumeración)](../../debugger/debug-interface-access/stackframetypeenum.md) enumeración que indica el tipo de marco específicas del compilador.  
  
## <a name="return-value"></a>Valor devuelto  
 Si es correcto, devuelve `S_OK`. Devuelve `S_FALSE` si no se admite esta propiedad. De lo contrario, devuelve un código de error.  
  
## <a name="see-also"></a>Vea también  
 [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)   
 [Enumeración StackFrameTypeEnum](../../debugger/debug-interface-access/stackframetypeenum.md)