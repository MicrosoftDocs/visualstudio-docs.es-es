---
title: Get_compiland | Documentos de Microsoft
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
- IDiaSectionContrib::get_compiland method
ms.assetid: c0496f6f-f8f2-435f-8674-6c32db6c5934
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e76fea45f5f18e4ab7b93daa40ab73bec431ea88
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47576737"
---
# <a name="idiasectioncontribgetcompiland"></a>IDiaSectionContrib::get_compiland
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [Get_compiland](https://docs.microsoft.com/visualstudio/debugger/debug-interface-access/idiasectioncontrib-get-compiland).  
  
Recupera una referencia al símbolo compiland que han contribuido en esta sección.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp#  
HRESULT get_compiland (   
   IDiaSymbol** pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pRetVal`  
 [out] Devuelve un [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) objeto que representa la operación de compilación que han contribuido en esta sección.  
  
## <a name="return-value"></a>Valor devuelto  
 Si es correcto, devuelve `S_OK`. Devuelve `S_FALSE` si no se admite esta propiedad. De lo contrario, devuelve un código de error.  
  
## <a name="see-also"></a>Vea también  
 [IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)



