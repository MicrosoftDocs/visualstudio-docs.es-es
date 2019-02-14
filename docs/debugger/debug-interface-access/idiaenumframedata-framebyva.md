---
title: IDiaEnumFrameData::frameByVA | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumFrameData::frameByVA method
ms.assetid: 0b1e441b-710a-46d8-8060-bed39071c834
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a5c6f6252c23069ffce01b9b790a44b24efbd80a
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 01/25/2019
ms.locfileid: "54949381"
---
# <a name="idiaenumframedataframebyva"></a>IDiaEnumFrameData::frameByVA
Devuelve una trama de dirección virtual (VA).  
  
## <a name="syntax"></a>Sintaxis  
  
```C++  
HRESULT frameByVA(   
   ULONGLONG       virtualAddress,  
   IDiaFrameData** frame  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 virtualAddress  
 [in] Evaluación de vulnerabilidad del marco de interés.  
  
 marco  
 [out] Devuelve un [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md) objeto que representa el marco que contiene la dirección proporcionada.  
  
## <a name="return-value"></a>Valor devuelto  
 Si la operación se realiza correctamente, devuelve `S_OK`. Devuelve `S_FALSE` si ningún dato de marco coincide con la dirección especificada. De lo contrario, devuelve un código de error.  
  
## <a name="see-also"></a>Vea también  
 [IDiaEnumFrameData](../../debugger/debug-interface-access/idiaenumframedata.md)   
 [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)