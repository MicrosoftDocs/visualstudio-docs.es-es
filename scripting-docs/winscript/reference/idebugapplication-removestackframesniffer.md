---
title: IDebugApplication::RemoveStackFrameSniffer | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: 1462ff1382f3ccb844ccc98c6e6eec676a86c669
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/19/2019
ms.locfileid: "58159262"
---
# <a name="idebugapplicationremovestackframesniffer"></a>IDebugApplication::RemoveStackFrameSniffer
Quita un proveedor de enumerador del marco de pila de esta aplicación.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
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