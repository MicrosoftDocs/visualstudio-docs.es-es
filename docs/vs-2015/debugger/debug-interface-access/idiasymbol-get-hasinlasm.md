---
title: Get_hasinlasm | Microsoft Docs
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
- IDiaSymbol::get_hasInlAsm method
ms.assetid: 7001c7cc-1459-4929-851b-a08066a803c6
caps.latest.revision: 10
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0cd376ccc2ac207206f3aa96fb1bc91aed1eb7dd
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/16/2018
ms.locfileid: "51757104"
---
# <a name="idiasymbolgethasinlasm"></a>IDiaSymbol::get_hasInlAsm
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Recupera una marca que especifica si la función contiene un ensamblado alineado.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
HRESULT get_hasInlAsm(  
   BOOL *pFlag  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pFlag`  
 [out] Devuelve `TRUE` si la función no tiene ningún ensamblado insertado; en caso contrario, devuelve `FALSE`.  
  
## <a name="return-value"></a>Valor devuelto  
 Si es correcto, devuelve `S_OK`; en caso contrario, devuelve `S_FALSE` o un código de error.  
  
> [!NOTE]
>  Un valor devuelto de `S_FALSE` significa que la propiedad no está disponible para el símbolo.  
  
## <a name="requirements"></a>Requisitos  
  
|Requisito|Descripción|  
|-----------------|-----------------|  
|Encabezado:|Dia2.h|  
|Versión:|SDK de DIA v8.0|  
  
## <a name="see-also"></a>Vea también  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)



