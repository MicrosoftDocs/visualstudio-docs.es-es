---
title: IDiaPropertyStorage::ReadLONG | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaPropertyStorage::ReadLONG
ms.assetid: 32054cbc-db55-4513-a1b4-de80e77aac8a
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 08661272bea779ff0789619d58bf6f2837a21917
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "62538322"
---
# <a name="idiapropertystoragereadlong"></a>IDiaPropertyStorage::ReadLONG
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Lee `LONG` los valores de un conjunto de propiedades.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp#  
HRESULT ReadDLONG (   
   PROPID id,  
   LONG*  pValue  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `id`  
 de Identificador de la propiedad que se va a leer ( `PROPID` se define en WTypes. h como `ULONG` ).  
  
 `pValue`  
 enuncia Devuelve el valor de propiedad.  
  
## <a name="return-value"></a>Valor devuelto  
 Si es correcto, devuelve `S_OK` ; de lo contrario, devuelve un código de error. Devuelve `E_INVALIDARG` si la propiedad no es de tipo `LONG` .  
  
## <a name="remarks"></a>Comentarios  
 `LONG`Windows define un entero con signo de 32 bits.  
  
## <a name="see-also"></a>Consulte también  
 [IDiaPropertyStorage](../../debugger/debug-interface-access/idiapropertystorage.md)
