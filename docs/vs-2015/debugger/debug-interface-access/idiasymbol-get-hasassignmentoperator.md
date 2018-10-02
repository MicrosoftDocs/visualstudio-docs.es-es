---
title: Get_hasassignmentoperator | Documentos de Microsoft
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
- IDiaSymbol::get_hasAssignmentOperator method
ms.assetid: fb1acb9c-4500-4343-a590-0395789e4040
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f449818322516002f0000b3a3b4a20b11b4bd806
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47576698"
---
# <a name="idiasymbolgethasassignmentoperator"></a>IDiaSymbol::get_hasAssignmentOperator
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [Get_hasassignmentoperator](https://docs.microsoft.com/visualstudio/debugger/debug-interface-access/idiasymbol-get-hasassignmentoperator).  
  
Recupera una marca que especifica si el tipo de datos definido por el usuario tiene definido ningún operador de asignación.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp#  
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
|Encabezado:|Dia2.h|  
|Versión:|SDK de DIA v7.0|  
  
## <a name="see-also"></a>Vea también  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)



