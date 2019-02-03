---
title: IDiaSymbol::get_hasAssignmentOperator | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_hasAssignmentOperator method
ms.assetid: fb1acb9c-4500-4343-a590-0395789e4040
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 726412304f40b652a33cfae0bc9958fa01fb3dec
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 01/25/2019
ms.locfileid: "54950694"
---
# <a name="idiasymbolgethasassignmentoperator"></a>IDiaSymbol::get_hasAssignmentOperator
Recupera una marca que especifica si el tipo de datos definido por el usuario tiene definido ningún operador de asignación.  
  
## <a name="syntax"></a>Sintaxis  
  
```C++  
HRESULT get_hasAssignmentOperator (   
   BOOL* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pRetVal`  
 [out] Devuelve `TRUE` si el tipo de datos definido por el usuario no tiene ningún operador de asignación definido; en caso contrario, devuelve `FALSE`.  
  
## <a name="return-value"></a>Valor devuelto  
 Si es correcto, devuelve `S_OK`; en caso contrario, devuelve `S_FALSE` o un código de error.  
  
> [!NOTE]
>  Un valor devuelto de `S_FALSE` significa que la propiedad no está disponible para el símbolo.  
  
## <a name="requirements"></a>Requisitos  
  
|Requisito|Descripción|  
|-----------------|-----------------|  
|Encabezado:|dia2.h|  
|Versión:|SDK de DIA v7.0|  
  
## <a name="see-also"></a>Vea también  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)