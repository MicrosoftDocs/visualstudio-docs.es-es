---
title: Symsareequiv | Documentos de Microsoft
ms.custom: ''
ms.date: 2018-06-30
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
- IDiaSession::symsAreEquiv method
ms.assetid: 9941d520-e203-46c0-83c3-b3a967f4fc59
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 08b091bfca65c2713f822e50a2bcacb5ac3df587
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47581257"
---
# <a name="idiasessionsymsareequiv"></a>IDiaSession::symsAreEquiv
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [Symsareequiv](https://docs.microsoft.com/visualstudio/debugger/debug-interface-access/idiasession-symsareequiv).  
  
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



