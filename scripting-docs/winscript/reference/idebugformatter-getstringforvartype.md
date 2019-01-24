---
title: IDebugFormatter::GetStringForVarType | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugFormatter.GetStringForVarType
apilocation:
- jscript.dll
helpviewer_keywords:
- IDebugFormatter::GetStringForVarType
ms.assetid: 1c1a0499-ca57-47e0-8367-fdb4c902bca3
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 06c4833e2d9a88b63a80b2ee9437dc5547579380
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/08/2019
ms.locfileid: "54087548"
---
# <a name="idebugformattergetstringforvartype"></a>IDebugFormatter::GetStringForVarType
Devuelve una cadena que representa el valor VARTYPE especificado.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
HRESULT GetStringForVarType(  
   VARTYPE    vt,  
   TYPEDESC*  ptdescArrayType,  
   BSTR*      pbstr  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `vt`  
 [in] VARTYPE para representar como una cadena.  
  
 `ptdescArrayType`  
 [in] Matriz de estructuras que describen los tipos.  
  
 `pbstr`  
 [out] Cadena que representa `vt`.  
  
## <a name="return-value"></a>Valor devuelto  
 El método devuelve un objeto `HRESULT`. Entre los valores posibles se incluyen los que se indican en la tabla siguiente, entre otros.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
  
## <a name="remarks"></a>Comentarios  
 El método devuelve una cadena que representa el valor VARTYPE especificado.  
  
## <a name="see-also"></a>Vea también  
 [IDebugFormatter (Interfaz)](../../winscript/reference/idebugformatter-interface.md)