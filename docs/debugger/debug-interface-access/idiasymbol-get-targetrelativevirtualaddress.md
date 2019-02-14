---
title: IDiaSymbol::get_targetRelativeVirtualAddress | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_targetRelativeVirtualAddress method
ms.assetid: 49a159f3-6943-44d3-90a3-0dba51e8a7ec
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c6f38b983945b7182f0e0822133f6542922dc1f0
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 01/25/2019
ms.locfileid: "55016294"
---
# <a name="idiasymbolgettargetrelativevirtualaddress"></a>IDiaSymbol::get_targetRelativeVirtualAddress
Recupera la dirección virtual relativa (RVA) de un destino del código thunk.  
  
## <a name="syntax"></a>Sintaxis  
  
```C++  
HRESULT get_targetRelativeVirtualAddress (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pRetVal`  
 [out] Devuelve la dirección RVA del destino de un código thunk.  
  
## <a name="return-value"></a>Valor devuelto  
 Si es correcto, devuelve `S_OK`; en caso contrario, devuelve `S_FALSE` o un código de error.  
  
> [!NOTE]
>  Un valor devuelto de `S_FALSE` significa que la propiedad no está disponible para el símbolo.  
  
## <a name="remarks"></a>Comentarios  
 Esta propiedad es válida solo si el símbolo como un [SymTagEnum (enumeración)](../../debugger/debug-interface-access/symtagenum.md) valor `SymTagThunk`.  
  
 Un "código thunk" es un fragmento de código que convierte entre un espacio de direcciones de memoria de 32 bits (también conocido como espacio de direcciones sin formato) y un espacio de direcciones de 16 bits (conocido como un espacio de direcciones segmentados).  
  
## <a name="see-also"></a>Vea también  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [Enumeración SymTagEnum](../../debugger/debug-interface-access/symtagenum.md)