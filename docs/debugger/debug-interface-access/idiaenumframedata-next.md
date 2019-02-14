---
title: IDiaEnumFrameData::Next | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumFrameData::Next method
ms.assetid: 546e2e23-efb2-425a-96a1-808c67c519fb
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e7905a9226d120c14a4b9e6472e14714167c1b09
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 01/25/2019
ms.locfileid: "54949394"
---
# <a name="idiaenumframedatanext"></a>IDiaEnumFrameData::Next
Recupera un número especificado de elementos de datos de marco de la secuencia de enumeración.  
  
## <a name="syntax"></a>Sintaxis  
  
```C++  
HRESULT Next (   
   ULONG           celt,   
   IDiaFrameData** rgelt,  
   ULONG*          pceltFetched  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 celt  
 [in] El número de elementos de datos de marco en el enumerador que se va a recuperar.  
  
 rgelt  
 [out] Una matriz de [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md) objetos que se rellena con los elementos de datos del marco solicitado.  
  
 pceltFetched  
 [out] Devuelve el número de elementos de datos del marco en el enumerador capturado.  
  
## <a name="return-value"></a>Valor devuelto  
 Si la operación se realiza correctamente, devuelve `S_OK`. Devuelve `S_FALSE` si no hay más registros. De lo contrario, devuelve un código de error.  
  
## <a name="see-also"></a>Vea también  
 [IDiaEnumFrameData](../../debugger/debug-interface-access/idiaenumframedata.md)   
 [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)