---
title: IDebugStackFrame::GetThread | Documentos de Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IDebugStackFrame.GetThread
apilocation: jscript.dll
helpviewer_keywords: IDebugStackFrame::GetThread
ms.assetid: ece24728-a6b2-4b01-a6f0-0a82b15be39b
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 888e15bdd154fbac444eb91fc31ad7f17c2981ca
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="idebugstackframegetthread"></a>IDebugStackFrame::GetThread
Devuelve el subproceso asociado a este marco de pila.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
HRESULT GetThread(  
   IDebugApplicationThread**  ppat  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `ppat`  
 [out] El subproceso asociado con este marco de pila.  
  
## <a name="return-value"></a>Valor devuelto  
 El método devuelve un objeto `HRESULT`. Entre los valores posibles se incluyen los que se indican en la tabla siguiente, entre otros.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
  
## <a name="remarks"></a>Comentarios  
 Este método devuelve el subproceso asociado a este marco de pila.  
  
## <a name="see-also"></a>Vea también  
 [IDebugStackFrame (Interfaz)](../../winscript/reference/idebugstackframe-interface.md)