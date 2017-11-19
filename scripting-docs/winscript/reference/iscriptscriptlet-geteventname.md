---
title: IScriptScriptlet::GetEventName | Documentos de Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IScriptScriptlet.GetEventName
apilocation: scrobj.dll
helpviewer_keywords: IScriptScriptlet::GetEventName
ms.assetid: 548fa650-808e-4c96-8253-5c72e67e8215
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 600eb4aff3bcefea31eb5fec76a2dc3cdce62a05
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="iscriptscriptletgeteventname"></a>IScriptScriptlet::GetEventName
Devuelve el nombre del evento asociado con el scriptlet.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
HRESULT GetEventName(  
   BSTR               *pbstr  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pbstr`  
 [out] Un búfer que contiene el nombre del evento que está asociado el `IScriptScriptlet` objeto.  
  
## <a name="return-value"></a>Valor devuelto  
 Interfaz `HRESULT`. Entre los valores posibles se incluyen los que se indican en la tabla siguiente, entre otros.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
  
## <a name="remarks"></a>Comentarios  
  
## <a name="see-also"></a>Vea también  
 [IScriptScriptlet (Interfaz)](../../winscript/reference/iscriptscriptlet-interface.md)