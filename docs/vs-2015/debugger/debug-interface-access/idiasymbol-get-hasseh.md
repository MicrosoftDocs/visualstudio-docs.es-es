---
title: IDiaSymbol::get_hasSEH | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_hasSEH method
ms.assetid: 1a709ded-22c8-464c-97be-eba5e464210c
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 72e8d428df4796c34c5ac20447e7bf8121f259d2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "65703766"
---
# <a name="idiasymbolget_hasseh"></a>IDiaSymbol::get_hasSEH
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Recupera una marca que especifica si la función contiene cualquier [control de excepciones estructurado (C/C++)](https://msdn.microsoft.com/library/dd3b647d-c269-43a8-aab9-ad1458712976) (por ejemplo, los bloques __try/ \_ _except).  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp#  
HRESULT get_hasSEH(  
   BOOL *pFlag  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pFlag`  
 enuncia Devuelve `TRUE` si la función tiene bloques de control de excepciones estructurados; de lo contrario, devuelve `FALSE` .  
  
## <a name="return-value"></a>Valor devuelto  
 Si es correcto, devuelve `S_OK` ; de lo contrario, devuelve `S_FALSE` o código de error.  
  
> [!NOTE]
> Un valor devuelto de `S_FALSE` significa que la propiedad no está disponible para el símbolo.  
  
## <a name="requirements"></a>Requisitos  
  
|Requisito|Descripción|  
|-----------------|-----------------|  
|Encabezado:|dia2.h|  
|Versión:|SDK de DIA v 8.0|  
  
## <a name="see-also"></a>Consulte también  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [Control de excepciones estructurado (C/C++)](https://msdn.microsoft.com/library/dd3b647d-c269-43a8-aab9-ad1458712976)
