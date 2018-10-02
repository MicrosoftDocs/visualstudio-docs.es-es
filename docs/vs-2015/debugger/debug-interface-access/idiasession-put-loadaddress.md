---
title: Put_loadaddress | Microsoft Docs
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
- IDiaSession::put_loadAddress method
ms.assetid: b157b245-1ea0-4b80-8962-d8b278dbc742
caps.latest.revision: 14
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e39ac68468113f371c032f2f29b4613fa229a3b7
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47573949"
---
# <a name="idiasessionputloadaddress"></a>IDiaSession::put_loadAddress
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [Put_loadaddress](https://docs.microsoft.com/visualstudio/debugger/debug-interface-access/idiasession-put-loadaddress).  
  
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



