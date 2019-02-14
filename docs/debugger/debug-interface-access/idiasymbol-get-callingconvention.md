---
title: IDiaSymbol::get_callingConvention | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_callingConvention method
ms.assetid: 355d3877-b6b6-45fd-a1d8-baed428d8f96
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 59eee930f13cb7f2d870c62d6cd0b47704eb94db
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 01/25/2019
ms.locfileid: "54991338"
---
# <a name="idiasymbolgetcallingconvention"></a>IDiaSymbol::get_callingConvention
Devuelve un indicador de una convención de llamada de métodos.  
  
## <a name="syntax"></a>Sintaxis  
  
```C++  
HRESULT get_callingConvention (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pRetVal`  
 [out] Devuelve un valor de la [CV_call_e (enumeración)](../../debugger/debug-interface-access/cv-call-e.md) convención de llamada de enumeración que especifica un método.  
  
## <a name="return-value"></a>Valor devuelto  
 Si es correcto, devuelve `S_OK`; en caso contrario, devuelve `S_FALSE` o un código de error.  
  
> [!NOTE]
>  Un valor devuelto de `S_FALSE` significa que la propiedad no está disponible para el símbolo.  
  
## <a name="requirements"></a>Requisitos  
  
|Requisito|Descripción|  
|-----------------|-----------------|  
|Encabezado:|dia2.h|  
|Versión:|SDK de DIA v7.0|  
  
## <a name="see-also"></a>Vea también  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [Enumeración CV_call_e](../../debugger/debug-interface-access/cv-call-e.md)