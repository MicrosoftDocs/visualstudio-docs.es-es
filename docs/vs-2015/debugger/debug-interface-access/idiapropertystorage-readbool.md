---
title: IDiaPropertyStorage::ReadBOOL | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaPropertyStorage::ReadBOOL
ms.assetid: ad1822db-4572-48f7-9919-f8137f6701f2
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 64eee421a5ed5bd46a64b51694d913a4f2dc4d41
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "62538881"
---
# <a name="idiapropertystoragereadbool"></a>IDiaPropertyStorage::ReadBOOL
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Lee `BOOL` los valores de un conjunto de propiedades.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp#  
HRESULT ReadBOOL (   
   PROPID id,  
   BOOL*  pValue  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `id`  
 de Identificador de la propiedad que se va a leer ( `PROPID` se define en WTypes. h como `ULONG` ).  
  
 `pValue`  
 enuncia Devuelve el valor de propiedad.  
  
## <a name="return-value"></a>Valor devuelto  
 Si es correcto, devuelve `S_OK` ; de lo contrario, devuelve un código de error. Devuelve `E_INVALIDARG` si la propiedad no es de tipo `BOOL` .  
  
## <a name="remarks"></a>Comentarios  
 Para obtener resultados coherentes, interprete el `BOOL` valor para que los valores distintos de cero sean `TRUE` y cero sea `FALSE` .  
  
## <a name="see-also"></a>Consulte también  
 [IDiaPropertyStorage](../../debugger/debug-interface-access/idiapropertystorage.md)
