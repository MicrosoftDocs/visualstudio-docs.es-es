---
title: Get_registerid | Microsoft Docs
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
- IDiaSymbol::get_registerId method
ms.assetid: f881e793-eb9e-48dc-a847-dd61d77174fc
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e79b9f7b1a2c2f44c1b5a39b4daa3798e8566c4d
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49278972"
---
# <a name="idiasymbolgetregisterid"></a>IDiaSymbol::get_registerId
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Recupera el designador de registro de la ubicación cuando la [LocationType (enumeración)](../../debugger/debug-interface-access/locationtype.md) está establecido en `LocIsEnregistered`.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp#  
HRESULT get_registerId (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pRetVal`  
 [out] Devuelve el designador de registro de la ubicación.  
  
## <a name="return-value"></a>Valor devuelto  
 Si es correcto, devuelve `S_OK`; en caso contrario, devuelve `S_FALSE` o un código de error.  
  
> [!NOTE]
>  Un valor devuelto de `S_FALSE` significa que la propiedad no está disponible para el símbolo.  
  
## <a name="remarks"></a>Comentarios  
 Si el símbolo es relativa a un registro, es decir, si el símbolo [LocationType (enumeración)](../../debugger/debug-interface-access/locationtype.md) está establecido en `LocIsRegRel`, utilice el `get_registerId` método seguido por una llamada a la [Get_offset](../../debugger/debug-interface-access/idiasymbol-get-offset.md) método para obtener el desplazamiento desde el registro donde se encuentra el símbolo.  
  
## <a name="see-also"></a>Vea también  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [Enumeración LocationType](../../debugger/debug-interface-access/locationtype.md)



