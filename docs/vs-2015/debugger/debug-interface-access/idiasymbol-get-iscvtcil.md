---
title: IDiaSymbol::get_isCVTCIL | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_isCVTCIL method
ms.assetid: 711b81fd-9549-44dc-9761-5eb862ed64c0
caps.latest.revision: 10
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 34868f48cf330670c3c14b3979897d80b5525f40
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "63422052"
---
# <a name="idiasymbolgetiscvtcil"></a>IDiaSymbol::get_isCVTCIL
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Recupera una marca que indica si el módulo se convirtió desde un módulo de Common Intermediate Language (CIL) en un módulo nativo.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp#  
HRESULT get_isCVTCIL(  
   BOOL *pFlag  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pFlag`  
 [out] Devuelve `TRUE` si el módulo se convirtió de CIL en código nativo; de lo contrario, devuelve `FALSE`.  
  
## <a name="return-value"></a>Valor devuelto  
 Si es correcto, devuelve `S_OK`; en caso contrario, devuelve `S_FALSE` o un código de error.  
  
> [!NOTE]
> Un valor devuelto de `S_FALSE` significa que la propiedad no está disponible para el símbolo.  
  
## <a name="remarks"></a>Comentarios  
 Esta propiedad está disponible desde el `SymTagCompilandDetails` tipo de símbolos (consulte [CompilandDetails](../../debugger/debug-interface-access/compilanddetails.md).  
  
## <a name="requirements"></a>Requisitos  
  
|Requisito|Descripción|  
|-----------------|-----------------|  
|Encabezado:|dia2.h|  
|Versión:|SDK de DIA v8.0|  
  
## <a name="see-also"></a>Vea también  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [CompilandDetails](../../debugger/debug-interface-access/compilanddetails.md)
