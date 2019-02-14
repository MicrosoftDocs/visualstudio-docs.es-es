---
title: IDiaPropertyStorage::ReadBOOL | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaPropertyStorage::ReadBOOL
ms.assetid: ad1822db-4572-48f7-9919-f8137f6701f2
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: cf0e91e2d617877596798512140195b54f4d3f8e
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 01/25/2019
ms.locfileid: "54924553"
---
# <a name="idiapropertystoragereadbool"></a>IDiaPropertyStorage::ReadBOOL
Lee `BOOL` valores en un conjunto de propiedades.  
  
## <a name="syntax"></a>Sintaxis  
  
```C++  
HRESULT ReadBOOL (   
   PROPID id,  
   BOOL*  pValue  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `id`  
 [in] Identificador de la propiedad de lectura (`PROPID` se define en el archivo WTypes.h como un `ULONG`).  
  
 `pValue`  
 [out] Devuelve el valor de propiedad.  
  
## <a name="return-value"></a>Valor devuelto  
 Si es correcto, devuelve `S_OK`; en caso contrario, devuelve un código de error. Devuelve `E_INVALIDARG` si la propiedad no es de tipo `BOOL`.  
  
## <a name="remarks"></a>Comentarios  
 Para obtener resultados coherentes, interpretar el `BOOL` valor para que sean valores distintos de cero `TRUE` y cero es `FALSE`.  
  
## <a name="see-also"></a>Vea también  
 [IDiaPropertyStorage](../../debugger/debug-interface-access/idiapropertystorage.md)