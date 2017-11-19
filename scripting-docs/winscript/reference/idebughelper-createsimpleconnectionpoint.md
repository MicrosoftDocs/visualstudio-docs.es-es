---
title: IDebugHelper::CreateSimpleConnectionPoint | Documentos de Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IDebugHelper.CreateSimpleConnectionPoint
apilocation: pdm.dll
helpviewer_keywords: IDebugHelper::CreateSimpleConnectionPoint
ms.assetid: 5e4798ce-6f9f-4184-9853-67bf8c8524ab
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: fcc598fa97d47a564ddb12aaa0480e42b6601118
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="idebughelpercreatesimpleconnectionpoint"></a>IDebugHelper::CreateSimpleConnectionPoint
Devuelve una interfaz de evento que contenga un determinado `IDispatch` objeto.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
HRESULT CreateSimpleConnectionPoint(  
   IDispatch*                pdisp  
   ISimpleConnectionPoint**  ppscp  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pdisp`  
 [in] La `IDispatch` objeto que se va a ajustar.  
  
 `ppscp`  
 [out] La interfaz de eventos que contiene `pdisp`.  
  
## <a name="return-value"></a>Valor devuelto  
 El método devuelve un objeto `HRESULT`. Entre los valores posibles se incluyen los que se indican en la tabla siguiente, entre otros.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
  
## <a name="remarks"></a>Comentarios  
 Devuelve una interfaz de evento que ajusta el determinado `IDispatch` (consulte [ISimpleConnectionPoint (interfaz)](../../winscript/reference/isimpleconnectionpoint-interface.md)).  
  
## <a name="see-also"></a>Vea también  
 [IDebugHelper (interfaz)](../../winscript/reference/idebughelper-interface.md)   
 [ISimpleConnectionPoint (Interfaz)](../../winscript/reference/isimpleconnectionpoint-interface.md)