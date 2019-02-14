---
title: IDiaEnumSymbols::Item | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumSymbols::Item method
ms.assetid: 2bd1ec04-e677-4e32-8e32-33334f1eed77
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b3cc898d989c345ba7691252562fac820eec1c18
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 01/25/2019
ms.locfileid: "54924115"
---
# <a name="idiaenumsymbolsitem"></a>IDiaEnumSymbols::Item
Recupera un símbolo de por medio de un índice.  
  
## <a name="syntax"></a>Sintaxis  
  
```C++  
HRESULT Item (   
   DWORD        index,  
   IDiaSymbol** symbol  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 índice  
 [in] Índice de la [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) objeto va a recuperar. El índice está en el intervalo de 0 a `count`-1, donde `count` devuelto por la [Idiaenumsymbols](../../debugger/debug-interface-access/idiaenumsymbols-get-count.md) método.  
  
 symbol  
 [out] Devuelve un [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) objeto que representa el símbolo que desee.  
  
## <a name="return-value"></a>Valor devuelto  
 Si es correcto, devuelve `S_OK`; en caso contrario, devuelve un código de error.  
  
## <a name="see-also"></a>Vea también  
 [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)