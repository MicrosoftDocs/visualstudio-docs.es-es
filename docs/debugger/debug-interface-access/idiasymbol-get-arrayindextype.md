---
title: IDiaSymbol::get_arrayIndexType | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_arrayIndexType method
ms.assetid: cd63b9ec-9694-406c-b37f-bde6bd5fcbf2
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 1a89afb7eb7d16f95ab5212d8cc081ac1cd84521
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "63402299"
---
# <a name="idiasymbolgetarrayindextype"></a>IDiaSymbol::get_arrayIndexType
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Recupera la interfaz de símbolo del tipo de índice de matriz del símbolo.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp#  
HRESULT get_arrayIndexType (   
   IDiaSymbol** pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pRetVal`  
 [out] Devuelve un [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) objeto que representa el tipo de índice de matriz del símbolo.  
  
## <a name="return-value"></a>Valor devuelto  
 Si es correcto, devuelve `S_OK`; en caso contrario, devuelve `S_FALSE` o código de error.  
  
> [!NOTE]
> Un valor devuelto de `S_FALSE` significa que la propiedad no está disponible para el símbolo.  
  
## <a name="remarks"></a>Comentarios  
 Algunos lenguajes pueden especificar el tipo utilizado como un índice de matriz. El símbolo devuelto por este método especifica ese tipo.  
  
## <a name="requirements"></a>Requisitos  
  
|Requisito|Descripción|  
|-----------------|-----------------|  
|Encabezado:|dia2.h|  
|Versión:|SDK de DIA v7.0|  
  
## <a name="see-also"></a>Vea también  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
