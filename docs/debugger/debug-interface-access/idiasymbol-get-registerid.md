---
title: 'Idiasymbol:: Get_registerid | Documentos de Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_registerId method
ms.assetid: f881e793-eb9e-48dc-a847-dd61d77174fc
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: c944869d48c484f7ddf234f4e00a5d10e96f70ae
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="idiasymbolgetregisterid"></a>IDiaSymbol::get_registerId
Recupera el designador de registro de la ubicación cuando el [LocationType (enumeración)](../../debugger/debug-interface-access/locationtype.md) está establecido en `LocIsEnregistered`.  
  
## <a name="syntax"></a>Sintaxis  
  
```C++  
HRESULT get_registerId (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pRetVal`  
 [out] Devuelve el designador de registro de la ubicación.  
  
## <a name="return-value"></a>Valor devuelto  
 Si se realiza correctamente, devuelve `S_OK`; en caso contrario, devuelve `S_FALSE` o un código de error.  
  
> [!NOTE]
>  Un valor devuelto de `S_FALSE` significa que la propiedad no está disponible para el símbolo.  
  
## <a name="remarks"></a>Comentarios  
 Si el símbolo es relativa a un registro, es decir, si el símbolo [LocationType (enumeración)](../../debugger/debug-interface-access/locationtype.md) está establecido en `LocIsRegRel`, use la `get_registerId` método seguido por una llamada a la [idiasymbol:: Get_offset](../../debugger/debug-interface-access/idiasymbol-get-offset.md) método para obtener el desplazamiento desde el registro donde se encuentra el símbolo.  
  
## <a name="see-also"></a>Vea también  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [LocationType (enumeración)](../../debugger/debug-interface-access/locationtype.md)