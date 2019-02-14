---
title: IDiaSession::put_loadAddress | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSession::put_loadAddress method
ms.assetid: b157b245-1ea0-4b80-8962-d8b278dbc742
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 488ae20ae4e38905b722f833a52676eea6ce0e81
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 01/25/2019
ms.locfileid: "55035775"
---
# <a name="idiasessionputloadaddress"></a>IDiaSession::put_loadAddress
Establece la dirección de carga del archivo ejecutable que corresponde a los símbolos en este almacén de símbolos.  
  
## <a name="syntax"></a>Sintaxis  
  
```C++  
HRESULT put_loadAddress (   
   ULONGLONG NewVal  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `NewVal`  
 [in] Carga la dirección del archivo ejecutable.  
  
## <a name="remarks"></a>Comentarios  
 Propiedades de dirección virtual (VA) de símbolos se calculan utilizando el valor de este método. No se calculan las direcciones virtuales a menos que esta propiedad se establece en cero.  
  
> [!NOTE]
>  Debe llamar a este método cuando llegue el [IDiaSession](../../debugger/debug-interface-access/idiasession.md) de objetos y antes de empezar a usar el objeto si tiene que usar las propiedades virtuales en los símbolos.  
  
## <a name="see-also"></a>Vea también  
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)