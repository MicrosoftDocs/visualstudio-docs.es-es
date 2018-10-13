---
title: IDiaPropertyStorage::ReadBOOL | Microsoft Docs
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
- IDiaPropertyStorage::ReadBOOL
ms.assetid: ad1822db-4572-48f7-9919-f8137f6701f2
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 09e62534afac32fc1872f2e84fe9b05d75173a2e
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49212113"
---
# <a name="idiapropertystoragereadbool"></a>IDiaPropertyStorage::ReadBOOL
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Lee `BOOL` valores en un conjunto de propiedades.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp#  
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



