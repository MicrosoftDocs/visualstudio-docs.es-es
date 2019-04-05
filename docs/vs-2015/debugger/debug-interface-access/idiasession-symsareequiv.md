---
title: IDiaSession::symsAreEquiv | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSession::symsAreEquiv method
ms.assetid: 9941d520-e203-46c0-83c3-b3a967f4fc59
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: ba8c77d7d97da75ce82fcbe732db64acf633b8af
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2019
ms.locfileid: "58998444"
---
# <a name="idiasessionsymsareequiv"></a>IDiaSession::symsAreEquiv
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Comprueba si dos símbolos son equivalentes.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp#  
HRESULT symsAreEquiv (   
   IDiaSymbol* symbolA,  
   IDiaSymbol* symbolB  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `symbolA`  
 [in] La primera [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) objeto que se usa en la comparación.  
  
 `symbolB`  
 [in] El segundo `IDiaSymbol` objeto que se usa en la comparación.  
  
## <a name="return-value"></a>Valor devuelto  
 Devuelve si los símbolos son equivalentes, `S_OK`; en caso contrario, devuelve `S_FALSE`, los símbolos no son equivalentes. En caso contrario, devuelve un código de error.  
  
## <a name="see-also"></a>Vea también  
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
