---
title: Put_loadaddress | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
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
- IDiaSession::put_loadAddress method
ms.assetid: b157b245-1ea0-4b80-8962-d8b278dbc742
caps.latest.revision: 14
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: cec66d9d7287c6432c02c0ec2a1c38f903811c44
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49259460"
---
# <a name="idiasessionputloadaddress"></a>IDiaSession::put_loadAddress
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Establece la dirección de carga del archivo ejecutable que corresponde a los símbolos en este almacén de símbolos.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp#  
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



