---
title: IEnumDebugExtendedPropertyInfo::Skip | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IEnumDebugExtendedPropertyInfo.Skip
apilocation:
- scrobj.dll
helpviewer_keywords:
- IEnumDebugExtendedPropertyInfo::Skip
ms.assetid: a0b4a9fc-e122-482b-9384-b83c460b61fe
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: cc88f41e1c75a2b6616cc6aba363b8824605a696
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/08/2019
ms.locfileid: "54094840"
---
# <a name="ienumdebugextendedpropertyinfoskip"></a>IEnumDebugExtendedPropertyInfo::Skip
Omite un número especificado de `ExtendedDebugPropertyInfo` estructuras en una secuencia de enumeración.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
HRESULT Skip(  
   ULONG celt  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `celt`  
 [in] El número de `ExtendedDebugPropertyInfo` estructuras en la secuencia de enumeración que se omitirán.  
  
## <a name="return-value"></a>Valor devuelto  
 Devuelve un válidas `HRESULT`, normalmente `S_OK`. Devuelve `S_FALSE` y establece el puntero del elemento actual al final de la enumeración si `celt` es mayor que el número de elementos a la izquierda en el enumerador.  
  
## <a name="see-also"></a>Vea también  
 [IEnumDebugExtendedPropertyInfo (interfaz)](../../winscript/reference/ienumdebugextendedpropertyinfo-interface.md)   
 [ExtendedDebugPropertyInfo (Estructura)](../../winscript/reference/extendeddebugpropertyinfo-structure.md)