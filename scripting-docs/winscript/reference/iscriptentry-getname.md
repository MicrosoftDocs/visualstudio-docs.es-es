---
title: IScriptEntry::GetName | Documentos de Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IScriptEntry.GetName
apilocation: scrobj.dll
helpviewer_keywords: IScriptEntry::GetName
ms.assetid: 56daa288-618f-497c-a360-7d443afd478b
caps.latest.revision: "11"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: fc518e87414d051e9b1393b60b5874a0204b78b2
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="iscriptentrygetname"></a>IScriptEntry::GetName
Para las entradas que representan un único objeto (por ejemplo, una función), devuelve el nombre del objeto.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
HRESULT GetName(  
   BSTR               *pbstr  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pbstr`  
 [out] El nombre del objeto representado por la `IScriptEntry` bloque de script. Si una entrada no representa un único objeto, se devuelve NULL.  
  
 Las entradas secundarias representan un objeto de función única.  
  
## <a name="return-value"></a>Valor devuelto  
 Interfaz `HRESULT`. Entre los valores posibles se incluyen los que se indican en la tabla siguiente, entre otros.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
  
## <a name="remarks"></a>Comentarios  
  
## <a name="see-also"></a>Vea también  
 [IScriptEntry (interfaz)](../../winscript/reference/iscriptentry-interface.md)   
 [IScriptNode:: CreateChildEntry](../../winscript/reference/iscriptnode-createchildentry.md)