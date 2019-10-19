---
title: 'Ienumdebugpropertyinfo (:: Next | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IEnumDebugPropertyInfo.Next
apilocation:
- scrobj.dll
helpviewer_keywords:
- IEnumDebugPropertyInfo::Next
ms.assetid: 052837ac-1599-49cc-9a5a-ba90f992eeff
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b99631c217ca56dce91512403dfb6623cd1e7641
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574199"
---
# <a name="ienumdebugpropertyinfonext"></a>IEnumDebugPropertyInfo::Next
Recupera un número especificado de estructuras `DebugPropertyInfo` en una secuencia de enumeración.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
HRESULT Next (  
   ULONGcelt,  
   DebugPropertyInfo*rgelt,  
   ULONG* pceltFetched  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `celt`  
 de Número de `DebugPropertyInfo`structures que se van a recuperar.  
  
 `rgelt`  
 enuncia Matriz de estructuras `DebugPropertyInfo` recuperadas.  
  
 `pceltFetched`  
 enuncia Devuelve el número de estructuras `DebugPropertyInfo` recuperadas realmente.  
  
## <a name="return-value"></a>Valor devuelto  
 Devuelve un `HRESULT` válido, normalmente `S_OK`.  
  
## <a name="see-also"></a>Vea también  
 @No__t_1 de la [interfaz ienumdebugpropertyinfo (](../../winscript/reference/ienumdebugpropertyinfo-interface.md)  
 [DebugPropertyInfo (Estructura)](../../winscript/reference/debugpropertyinfo-structure.md)