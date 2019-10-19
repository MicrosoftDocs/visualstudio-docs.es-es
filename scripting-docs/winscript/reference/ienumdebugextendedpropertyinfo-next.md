---
title: 'Ienumdebugextendedpropertyinfo (:: Next | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IEnumDebugExtendedPropertyInfo.Next
apilocation:
- scrobj.dll
helpviewer_keywords:
- IEnumDebugExtendedPropertyInfo::Next
ms.assetid: ac41c9a3-19d1-4596-8a87-01c10b131be3
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 23ebc3e3fd1f7802f4630be42a594d73f8657e43
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574258"
---
# <a name="ienumdebugextendedpropertyinfonext"></a>IEnumDebugExtendedPropertyInfo::Next
Recupera un número especificado de estructuras `ExtendedDebugPropertyInfo` en una secuencia de enumeración.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
HRESULT Next (  
   ULONGcelt,  
   ExtendedDebugPropertyInfo *rgelt,  
   ULONG* pceltFetched  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `celt`  
 de Número de `ExtendedDebugPropertyInfo`structures que se van a recuperar.  
  
 `rgelt`  
 enuncia Matriz de estructuras `ExtendedDebugPropertyInfo` recuperadas.  
  
 `pceltFetched`  
 enuncia El número de estructuras `ExtendedDebugPropertyInfo` recuperadas realmente.  
  
## <a name="return-value"></a>Valor devuelto  
 Devuelve un `HRESULT` válido, normalmente `S_OK`.  
  
## <a name="see-also"></a>Vea también  
 @No__t_1 de la [interfaz ienumdebugextendedpropertyinfo (](../../winscript/reference/ienumdebugextendedpropertyinfo-interface.md)  
 [ExtendedDebugPropertyInfo (Estructura)](../../winscript/reference/extendeddebugpropertyinfo-structure.md)