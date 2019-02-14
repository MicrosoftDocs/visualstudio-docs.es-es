---
title: IDiaEnumInjectedSources::Next | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumInjectedSources::Next method
ms.assetid: 38af80fc-748f-4b15-bff1-823db21dd4d0
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ba51ecbb1d47707dcfc8bd112a09deb170546d28
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 01/25/2019
ms.locfileid: "55036230"
---
# <a name="idiaenuminjectedsourcesnext"></a>IDiaEnumInjectedSources::Next
Recupera un número especificado de orígenes insertados en la secuencia de enumeración.  
  
## <a name="syntax"></a>Sintaxis  
  
```C++  
HRESULT Next (   
   ULONG                celt,   
   IDiaInjectedSource** rgelt,  
   ULONG*               pceltFetched  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 celt  
 [in] El número de orígenes insertados en el enumerador que se va a recuperar.  
  
 rgelt  
 [out] Devuelve una matriz de [IDiaInjectedSource](../../debugger/debug-interface-access/idiainjectedsource.md) objetos que representan los orígenes insertados deseados.  
  
 pceltFetched  
 [out] Devuelve el número de orígenes insertados en el enumerador capturado.  
  
## <a name="return-value"></a>Valor devuelto  
 Si la operación se realiza correctamente, devuelve `S_OK`. Devuelve `S_FALSE` si no hay origen insertado no hay más. De lo contrario, devuelve un código de error.  
  
## <a name="see-also"></a>Vea también  
 [IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md)   
 [IDiaInjectedSource](../../debugger/debug-interface-access/idiainjectedsource.md)