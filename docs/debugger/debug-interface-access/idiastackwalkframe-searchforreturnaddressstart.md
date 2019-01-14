---
title: Idiastackwalkframe | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalkFrame::searchForReturnAddressStart method
ms.assetid: 47660b9b-6e4f-4dfa-88ab-63dce28f7412
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 1dd00d6e515e26ae5b2c7c8f90e29220ec1e1564
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53961717"
---
# <a name="idiastackwalkframesearchforreturnaddressstart"></a>IDiaStackWalkFrame::searchForReturnAddressStart
Busca el marco de pila especificado para una dirección de retorno en o cerca de la dirección especificada.  
  
## <a name="syntax"></a>Sintaxis  
  
```C++  
HRESULT searchForReturnAddressStart (   
   IDiaFrameData* frame,  
   ULONGLONG      startAddress,  
   ULONGLONG*     returnAddress  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `frame`  
 [in] Un [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md) objeto que representa el marco de pila actual.  
  
 `startAddress`  
 [in] Una dirección de memoria virtual desde el que se va a comenzar la búsqueda.  
  
 `returnAddress`  
 [out] Devuelve la función más cercana remite que `startAddress`.  
  
## <a name="return-value"></a>Valor devuelto  
 Si es correcto, devuelve `S_OK`; en caso contrario, devuelve un código de error.  
  
## <a name="see-also"></a>Vea también  
 [IDiaStackWalkFrame](../../debugger/debug-interface-access/idiastackwalkframe.md)   
 [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)