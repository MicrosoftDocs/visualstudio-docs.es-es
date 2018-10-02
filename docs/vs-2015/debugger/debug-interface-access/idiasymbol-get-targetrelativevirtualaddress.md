---
title: Get_targetrelativevirtualaddress | Documentos de Microsoft
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
- IDiaSymbol::get_targetRelativeVirtualAddress method
ms.assetid: 49a159f3-6943-44d3-90a3-0dba51e8a7ec
caps.latest.revision: 13
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 673146a4af83100e5ea6e92112fd66ec0cc45f15
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47579097"
---
# <a name="idiasymbolgettargetrelativevirtualaddress"></a>IDiaSymbol::get_targetRelativeVirtualAddress
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [Get_targetrelativevirtualaddress](https://docs.microsoft.com/visualstudio/debugger/debug-interface-access/idiasymbol-get-targetrelativevirtualaddress).  
  
Recupera la dirección virtual relativa (RVA) de un destino del código thunk.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp#  
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



