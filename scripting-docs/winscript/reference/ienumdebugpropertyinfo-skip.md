---
title: IEnumDebugPropertyInfo::Skip | Documentos de Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IEnumDebugPropertyInfo.Skip
apilocation:
- scrobj.dll
helpviewer_keywords:
- IEnumDebugPropertyInfo::Skip
ms.assetid: 2f6361fb-d66d-4fc0-8fe0-c859593a183f
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1d0f8ff65340edfac1c02e5b7e80b7be3fd257c4
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
ms.locfileid: "24727215"
---
# <a name="ienumdebugpropertyinfoskip"></a>IEnumDebugPropertyInfo::Skip
Omite un número especificado de `DebugPropertyInfo` estructuras en una secuencia de enumeración.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
HRESULT Skip(  
   ULONGcelt  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `celt`  
 [in] El número de `DebugPropertyInfo` estructuras en la secuencia de enumeración que se va a omitir.  
  
## <a name="return-value"></a>Valor devuelto  
 Devuelve un válidas `HRESULT`, normalmente `S_OK`. Devuelve `S_FALSE` y establece el puntero del elemento actual hasta el final de la enumeración si `celt` es mayor que el número de elementos a la izquierda en el enumerador.  
  
## <a name="see-also"></a>Vea también  
 [IEnumDebugPropertyInfo (interfaz)](../../winscript/reference/ienumdebugpropertyinfo-interface.md)   
 [DebugPropertyInfo (Estructura)](../../winscript/reference/debugpropertyinfo-structure.md)