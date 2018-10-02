---
title: Get_informational | Microsoft Docs
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
- IDiaSectionContrib::get_informational method
ms.assetid: 5351e89f-7db1-4f8e-9e57-2dd1c74002e0
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7db3a2091e2a6b62a5393da5b87ffcd4a9ab55a4
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47577120"
---
# <a name="idiasectioncontribgetinformational"></a>IDiaSectionContrib::get_informational
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [Get_informational](https://docs.microsoft.com/visualstudio/debugger/debug-interface-access/idiasectioncontrib-get-informational).  
  
Recupera una marca que indica si una sección contiene comentarios o información similar.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp#  
HRESULT get_informational(  
   BOOL* pRetVal  
};  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pRetVal`  
 [out] Devuelve `TRUE` si la sección contiene comentarios u otra información; de lo contrario devuelve `FALSE`.  
  
## <a name="return-value"></a>Valor devuelto  
 Si es correcto, devuelve `S_OK`. Devuelve `S_FALSE` si no se admite esta propiedad. De lo contrario, devuelve un código de error.  
  
## <a name="remarks"></a>Comentarios  
 Normalmente, la sección .directive contiene información.  
  
## <a name="see-also"></a>Vea también  
 [IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md)



