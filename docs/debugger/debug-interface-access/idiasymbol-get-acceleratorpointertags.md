---
title: IDiaSymbol::get_acceleratorPointerTags | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 30e13cee-e511-49ec-affd-99b0097071b2
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 5e65def0ac8e94b2f113332981f57c051896f6bd
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53875464"
---
# <a name="idiasymbolgetacceleratorpointertags"></a>IDiaSymbol::get_acceleratorPointerTags
Devuelve todos los valores de etiqueta de puntero acelerador que corresponden a una función de código auxiliar del Acelerador C++ AMP.  
  
## <a name="syntax"></a>Sintaxis  
  
```C++  
HRESULT get_acceleratorPointerTags(   
   DWORD          cnt,  
   DWORD*         pcnt,  
   DWORD*         pPointerTags);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `cnt`  
 [in] El tamaño de la matriz de salida `pPointerTags`.  
  
 `pcnt`  
 [out] El recuento de etiquetas de puntero de Acelerador de la función de código auxiliar del Acelerador C++ AMP.  
  
 `pPointerTags`  
 [out] Un `DWORD` puntero de matriz que se rellena con los valores de etiqueta del puntero de Acelerador de la función de código auxiliar de acelerador C++ AMP.  
  
## <a name="return-value"></a>Valor devuelto  
 Si es correcto, devuelve `S_OK`; en caso contrario, devuelve `S_FALSE` o un código de error.  
  
## <a name="remarks"></a>Comentarios  
 Se llama a este método en un `IDiaSymbol` interfaz que corresponde a una función de código auxiliar del Acelerador C++ AMP.  
  
## <a name="see-also"></a>Vea también  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)