---
title: IDiaEnumInjectedSources::Clone | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumInjectedSources::Clone method
ms.assetid: 18038691-c140-426a-8617-27f0360650f3
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ece73b97ec0129b2acd26c8751ab8b10909ee4ed
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 01/25/2019
ms.locfileid: "55036126"
---
# <a name="idiaenuminjectedsourcesclone"></a>IDiaEnumInjectedSources::Clone
Crea un enumerador que contiene el mismo estado de enumeración que el enumerador actual.  
  
## <a name="syntax"></a>Sintaxis  
  
```C++  
HRESULT Clone (   
   IDiaEnumInjectedSources** ppenum  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `ppenum`  
 [out] Devuelve un [IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md) objeto que contiene un duplicado del enumerador. No se duplican los orígenes insertados, solo el enumerador.  
  
## <a name="return-value"></a>Valor devuelto  
 Si es correcto, devuelve `S_OK`; en caso contrario, devuelve un código de error.  
  
## <a name="see-also"></a>Vea también  
 [IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md)