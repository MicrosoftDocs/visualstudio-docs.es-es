---
title: IDiaFrameData::get_functionStart | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaFrameData::get_functionStart method
ms.assetid: 49fd24fb-65c2-4812-8303-56a968353e1b
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 08029b3abc3ec054cd8244d22d17db7992fa3623
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "68186949"
---
# <a name="idiaframedataget_functionstart"></a>IDiaFrameData::get_functionStart
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Recupera una marca que indica si el bloque contiene el punto de entrada de una función.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp#  
HRESULT get_functionStart (   
   BOOL* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pRetVal`  
 enuncia Devuelve `TRUE` si el bloque contiene el punto de entrada; de lo contrario, devuelve `FALSE` .  
  
## <a name="return-value"></a>Valor devuelto  
 Si la operación se realiza correctamente, devuelve `S_OK`. Devuelve `S_FALSE` si no se admite esta propiedad. De lo contrario, devuelve un código de error.  
  
## <a name="remarks"></a>Observaciones  
 Es posible que un marco de pila no sea el inicio de una función porque el marco representa un método insertado o una función insertada en una función.  
  
## <a name="see-also"></a>Consulte también  
 [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)
