---
title: IDiaEnumSymbols::Clone | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumSymbols::Clone method
ms.assetid: 5c542025-98cf-4307-901f-b9430f780cf0
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: baea8fb7d0bf43f648cd4201bef74c97e91db7ee
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 01/25/2019
ms.locfileid: "55042744"
---
# <a name="idiaenumsymbolsclone"></a>IDiaEnumSymbols::Clone
Crea un enumerador que contiene el mismo estado de enumeración que el enumerador actual.  
  
## <a name="syntax"></a>Sintaxis  
  
```C++  
HRESULT Clone (   
   IDiaEnumSymbols** ppenum  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 ppenum  
 [out] Devuelve un [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md) objeto que contiene un duplicado del enumerador. No se duplican los símbolos, solo el enumerador.  
  
## <a name="return-value"></a>Valor devuelto  
 Si es correcto, devuelve `S_OK`; en caso contrario, devuelve un código de error.  
  
## <a name="see-also"></a>Vea también  
 [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)