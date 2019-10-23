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
ms.openlocfilehash: 39db3bc0e0107e734f5de3f6902a2ca0fcc55bb0
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/22/2019
ms.locfileid: "72741887"
---
# <a name="idiasessionput_loadaddress"></a>IDiaSession::put_loadAddress
Establece la dirección de carga del archivo ejecutable que corresponde a los símbolos de este almacén de símbolos.

## <a name="syntax"></a>Sintaxis

```C++
HRESULT put_loadAddress ( 
   ULONGLONG NewVal
);
```

#### <a name="parameters"></a>Parámetros
 `NewVal`

de Dirección de carga del archivo ejecutable.

## <a name="remarks"></a>Comentarios
 Las propiedades de la dirección virtual de símbolos (VA) se calculan utilizando el valor de este método. Las direcciones virtuales no se calculan a menos que esta propiedad se establezca en un valor distinto de cero.

> [!NOTE]
> Debe llamar a este método al obtener el objeto [IDiaSession](../../debugger/debug-interface-access/idiasession.md) y antes de empezar a usar el objeto si necesita usar cualquier propiedad virtual en los símbolos.

## <a name="see-also"></a>Vea también
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)