---
title: 'Idiasession:: Symsareequiv | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSession::symsAreEquiv method
ms.assetid: 9941d520-e203-46c0-83c3-b3a967f4fc59
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: cc92a38305e7cc8c74b4ada0d560b314ed92da8f
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2018
ms.locfileid: "31460048"
---
# <a name="idiasessionsymsareequiv"></a>IDiaSession::symsAreEquiv
Comprueba si dos símbolos son equivalentes.  
  
## <a name="syntax"></a>Sintaxis  
  
```C++  
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
 Si los símbolos son equivalentes, devuelve `S_OK`; en caso contrario, devuelve `S_FALSE`, los símbolos no son equivalentes. En caso contrario, devuelve un código de error.  
  
## <a name="see-also"></a>Vea también  
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)