---
title: IDiaSymbol::get_locationType | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_locationType method
ms.assetid: fbb09c43-ebb7-4b4f-be53-ccff86eb183a
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 49d92f0891af725e8e17c673d975a300a1fa6bdf
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "90842742"
---
# <a name="idiasymbolget_locationtype"></a>IDiaSymbol::get_locationType
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Recupera el tipo de ubicación de un símbolo de datos.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp#  
HRESULT get_locationType (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pRetVal`  
 enuncia Devuelve un valor de la enumeración de [enumeración LocationType (](../../debugger/debug-interface-access/locationtype.md) que especifica el tipo de ubicación de un símbolo de datos, como `static` o `local` .  
  
## <a name="return-value"></a>Valor devuelto  
 Si es correcto, devuelve `S_OK` ; de lo contrario, devuelve `S_FALSE` o un código de error.  
  
> [!NOTE]
> Un valor devuelto de `S_FALSE` significa que la propiedad no está disponible para el símbolo.  
  
## <a name="see-also"></a>Consulte también  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [Enumeración LocationType](../../debugger/debug-interface-access/locationtype.md)
