---
title: IDiaPropertyStorage::ReadULONGLONG | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaPropertyStorage::ReadULONGLONG
ms.assetid: f80a2e24-5744-4fec-bab0-3ed51aef6e58
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 6da509e226a612e80a10ca0759b5e264f31a1e13
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "62538686"
---
# <a name="idiapropertystoragereadulonglong"></a>IDiaPropertyStorage::ReadULONGLONG
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Lee `ULONGLONG` los valores de un conjunto de propiedades.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp#  
HRESULT ReadULONGLONG (   
   PROPID     id,  
   ULONGLONG* pValue  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `id`  
 de Identificador de la propiedad que se va a leer ( `PROPID` se define en WTypes. h como `ULONG` ).  
  
 `pValue`  
 enuncia Devuelve el valor de propiedad.  
  
## <a name="return-value"></a>Valor devuelto  
 Si es correcto, devuelve `S_OK` ; de lo contrario, devuelve un código de error. Devuelve `E_INVALIDARG` si la propiedad no es de tipo `ULONGLONG` .  
  
## <a name="remarks"></a>Comentarios  
 `ULONGLONG`Windows define un como un entero de 64 bits sin signo.  
  
## <a name="see-also"></a>Consulte también  
 [IDiaPropertyStorage](../../debugger/debug-interface-access/idiapropertystorage.md)
