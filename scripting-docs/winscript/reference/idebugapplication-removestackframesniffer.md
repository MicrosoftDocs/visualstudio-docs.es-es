---
title: IDebugApplication::RemoveStackFrameSniffer | Documentos de Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugApplication.RemoveStackFrameSniffer
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugApplication::RemoveStackFrameSniffer
ms.assetid: 00304b88-e435-4b87-a331-44e7492eb32d
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 11289972dbd39d2e6221fb223a0d933ed90589c2
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
ms.locfileid: "24725725"
---
# <a name="idebugapplicationremovestackframesniffer"></a>IDebugApplication::RemoveStackFrameSniffer
Quita un proveedor de enumerador del marco de pila de esta aplicación.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
HRESULT RemoveStackFrameSniffer(  
   DWORD  dwCookie  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `dwCookie`  
 [in] La cookie devuelta por la `AddStackFrameSniffer` método cuando se agregó el proveedor de enumerador del marco de pila.  
  
## <a name="return-value"></a>Valor devuelto  
 El método devuelve un objeto `HRESULT`. Entre los valores posibles se incluyen los que se indican en la tabla siguiente, entre otros.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
  
## <a name="remarks"></a>Comentarios  
 El `RemoveStackFrameSniffer` método quita un proveedor de enumerador del marco de pila de esta aplicación.  
  
## <a name="see-also"></a>Vea también  
 [IDebugApplication::AddStackFrameSniffer](../../winscript/reference/idebugapplication-addstackframesniffer.md)   
 [IDebugApplication (interfaz)](../../winscript/reference/idebugapplication-interface.md)   
 [IDebugStackFrameSniffer (Interfaz)](../../winscript/reference/idebugstackframesniffer-interface.md)