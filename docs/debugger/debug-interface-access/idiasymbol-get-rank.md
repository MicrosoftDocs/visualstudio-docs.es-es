---
title: Get_rank | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_rank method
ms.assetid: 14cc9c4b-a5ec-414a-b01f-4a142c17b7cc
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 6689694c3256ce463eaf70aa32215b39f907efe3
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53919831"
---
# <a name="idiasymbolgetrank"></a>IDiaSymbol::get_rank
Recupera el rango (número de dimensiones) de una matriz multidimensional de FORTRAN.  
  
## <a name="syntax"></a>Sintaxis  
  
```C++  
HRESULT get_rank (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pRetVal`  
 [out] Devuelve el número de dimensiones de una matriz multidimensional de FORTRAN.  
  
## <a name="return-value"></a>Valor devuelto  
 Si es correcto, devuelve `S_OK`; en caso contrario, devuelve `S_FALSE` o un código de error.  
  
> [!NOTE]
>  Un valor devuelto de `S_FALSE` significa que la propiedad no está disponible para el símbolo.  
  
## <a name="remarks"></a>Comentarios  
 Rango hace referencia al número de dimensiones de una matriz donde se declara la matriz como `myarray[1,2,3]`. En este ejemplo tiene un rango de 3 y 3 dimensiones. Rango no es aplicable a C++ que usa el concepto de una matriz de matrices para cada dimensión (es decir, `myarray[1][2][3]`).  
  
## <a name="see-also"></a>Vea también  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)