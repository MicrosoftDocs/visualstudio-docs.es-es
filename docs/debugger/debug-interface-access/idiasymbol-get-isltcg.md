---
title: IDiaSymbol::get_isLTCG | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_isLTCG method
ms.assetid: 5f7f05b8-6b71-4958-9e1e-e4924ef9c59b
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 80f8218d67b16768f4e36c7a9a21839a5217f5ca
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 01/25/2019
ms.locfileid: "54977884"
---
# <a name="idiasymbolgetisltcg"></a>IDiaSymbol::get_isLTCG
Recupera una marca que especifica si el [Compiland](../../debugger/debug-interface-access/compiland.md) se ha vinculado con el modificador del vinculador [/LTCG (generación de código de tiempo de vínculo)](/cpp/build/reference/ltcg-link-time-code-generation), lo que contribuye en la optimización de todo el programa. Este modificador se aplica solo a código administrado.  
  
## <a name="syntax"></a>Sintaxis  
  
```C++  
HRESULT get_iSLTCG(  
   BOOL *pFlag  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 pFlag  
 [out] Devuelve `TRUE` si el `compiland` estaba vinculada con el modificador de vinculador/LTCG; en caso contrario, devuelve `FALSE`.  
  
## <a name="return-value"></a>Valor devuelto  
 Si es correcto, devuelve `S_OK`; en caso contrario, devuelve `S_FALSE` o un código de error.  
  
> [!NOTE]
>  Un valor devuelto de `S_FALSE` significa que la propiedad no está disponible para el símbolo.  
  
## <a name="requirements"></a>Requisitos  
  
|Requisito|Descripción|  
|-----------------|-----------------|  
|Encabezado:|dia2.h|  
|Versión:|SDK de DIA v8.0|  
  
## <a name="see-also"></a>Vea también  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)