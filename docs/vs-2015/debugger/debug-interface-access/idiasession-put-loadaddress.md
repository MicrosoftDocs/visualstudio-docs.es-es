---
title: IDiaSession::put_loadAddress | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSession::put_loadAddress method
ms.assetid: b157b245-1ea0-4b80-8962-d8b278dbc742
caps.latest.revision: 14
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: f697384874726904960fc5ba04733c3acfe1cd06
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "90842335"
---
# <a name="idiasessionput_loadaddress"></a>IDiaSession::put_loadAddress
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Establece la dirección de carga del archivo ejecutable que corresponde a los símbolos de este almacén de símbolos.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp#  
HRESULT put_loadAddress (   
   ULONGLONG NewVal  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `NewVal`  
 de Dirección de carga del archivo ejecutable.  
  
## <a name="remarks"></a>Notas  
 Las propiedades de la dirección virtual de símbolos (VA) se calculan utilizando el valor de este método. Las direcciones virtuales no se calculan a menos que esta propiedad se establezca en un valor distinto de cero.  
  
> [!NOTE]
> Debe llamar a este método al obtener el objeto [IDiaSession](../../debugger/debug-interface-access/idiasession.md) y antes de empezar a usar el objeto si necesita usar cualquier propiedad virtual en los símbolos.  
  
## <a name="see-also"></a>Consulte también  
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
