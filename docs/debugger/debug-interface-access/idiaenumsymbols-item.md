---
title: 'Idiaenumsymbols:: Item | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumSymbols::Item method
ms.assetid: 2bd1ec04-e677-4e32-8e32-33334f1eed77
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: d5f919c8b4d3b4dfafa17a727892f92e1fc2c0ad
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
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
 [in] Índice de la [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) objeto va a recuperar. El índice se encuentra en el intervalo de 0 a `count`-1, donde `count` devuelto por la [idiaenumsymbols:: Get_count](../../debugger/debug-interface-access/idiaenumsymbols-get-count.md) método.  
  
 symbol  
 [out] Devuelve un [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) objeto que representa el símbolo que desee.  
  
## <a name="return-value"></a>Valor devuelto  
 Si se realiza correctamente, devuelve `S_OK`; en caso contrario, devuelve un código de error.  
  
## <a name="see-also"></a>Vea también  
 [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)