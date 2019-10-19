---
title: 'IDebugPropertyEnumType_All:: GetName | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugPropertyEnumType_All.GetName
apilocation:
- scrobj.dll
helpviewer_keywords:
- IDebugPropertyEnumType_All::GetName
ms.assetid: 24bbe4d5-4263-48d0-8e8d-bff957ffcad2
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ad5d8d1d1b9e2e7ee632ed3fec40b89df5b4bc07
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577387"
---
# <a name="idebugpropertyenumtype_allgetname"></a>IDebugPropertyEnumType_All::GetName
Devuelve un BSTR que contiene el nombre del `EnumType`.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
HRESULT GetName(  
   BSTR*  pname  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pname`  
 enuncia BSTR que contiene el nombre del `EnumType`.  
  
## <a name="return-value"></a>Valor devuelto  
 Devuelve un `HRESULT` válido, normalmente `S_OK`.  
  
## <a name="see-also"></a>Vea también  
 [IDebugPropertyEnumType_All (Interfaz)](../../winscript/reference/idebugpropertyenumtype-all-interface.md)