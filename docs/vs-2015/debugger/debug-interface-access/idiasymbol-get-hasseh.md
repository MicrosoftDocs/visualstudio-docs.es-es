---
title: Get_hasseh | Microsoft Docs
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
- IDiaSymbol::get_hasSEH method
ms.assetid: 1a709ded-22c8-464c-97be-eba5e464210c
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f8dd3eda1eaf992de0b38e26bde93ae3f4c1de05
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47577952"
---
# <a name="idiasymbolgethasseh"></a>IDiaSymbol::get_hasSEH
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [Get_hasseh](https://docs.microsoft.com/visualstudio/debugger/debug-interface-access/idiasymbol-get-hasseh).  
  
Recupera una marca que especifica si la función contiene cualquier [control de excepciones estructurado (C/C ++)](http://msdn.microsoft.com/library/dd3b647d-c269-43a8-aab9-ad1458712976) (por ejemplo, __try /\__except bloques).  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp#  
HRESULT get_hasSEH(  
   BOOL *pFlag  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pFlag`  
 [out] Devuelve `TRUE` si la función tiene; los bloques de control de excepciones estructurado en caso contrario, devuelve `FALSE`.  
  
## <a name="return-value"></a>Valor devuelto  
 Si es correcto, devuelve `S_OK`; en caso contrario, devuelve `S_FALSE` o código de error.  
  
> [!NOTE]
>  Un valor devuelto de `S_FALSE` significa que la propiedad no está disponible para el símbolo.  
  
## <a name="requirements"></a>Requisitos  
  
|Requisito|Descripción|  
|-----------------|-----------------|  
|Encabezado:|Dia2.h|  
|Versión:|SDK de DIA v8.0|  
  
## <a name="see-also"></a>Vea también  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [Control de excepciones estructurado (C/C++)](http://msdn.microsoft.com/library/dd3b647d-c269-43a8-aab9-ad1458712976)



