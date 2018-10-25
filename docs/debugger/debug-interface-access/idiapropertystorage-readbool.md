---
title: IDiaPropertyStorage::ReadBOOL | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaPropertyStorage::ReadBOOL
ms.assetid: ad1822db-4572-48f7-9919-f8137f6701f2
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 3df4ce44c0cf0b3b09442dc695f73c415035e84a
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49904185"
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