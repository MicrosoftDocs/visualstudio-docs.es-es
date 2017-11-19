---
title: IDiaSymbol::get_isAcceleratorStubFunction | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: cc4ea375-76f6-4ba8-baed-c5fa82108137
caps.latest.revision: "3"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f6a7d2f27e776b37c392eb0116425ceeb6916031
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="idiasymbolgetisacceleratorstubfunction"></a>IDiaSymbol::get_isAcceleratorStubFunction
Indica si el símbolo corresponde a un símbolo de función de nivel superior de un sombreador que se compila para un acelerador que corresponde a un `parallel_for_each` llamar.  
  
## <a name="syntax"></a>Sintaxis  
  
```C++  
HRESULT get_isAcceleratorStubFunction(   
   BOOL* pFlag);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pFlag`  
 [out] Un puntero a un `BOOL` que indica si el símbolo corresponde a un símbolo de función de nivel superior de un sombreador que se compila para un acelerador que corresponde a un `parallel_for_each` llamar.  
  
## <a name="return-value"></a>Valor devuelto  
 Si se realiza correctamente, devuelve `S_OK`; en caso contrario, devuelve `S_FALSE` o un código de error.  
  
## <a name="see-also"></a>Vea también  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)