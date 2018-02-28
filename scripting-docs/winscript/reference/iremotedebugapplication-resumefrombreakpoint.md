---
title: IRemoteDebugApplication::ResumeFromBreakPoint | Documentos de Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- IRemoteDebugApplication.ResumeFromBreakPoint
apilocation:
- pdm.dll
helpviewer_keywords:
- IRemoteDebugApplication::ResumeFromBreakPoint
ms.assetid: a613cc2b-1d69-4713-a235-64372c253b4a
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5da5fdbaaf74f463161f1a98bbad7d4d147b418d
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="iremotedebugapplicationresumefrombreakpoint"></a>IRemoteDebugApplication::ResumeFromBreakPoint
Continúa una aplicación que está actualmente en un punto de interrupción.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
HRESULT ResumeFromBreakPoint(  
   IRemoteDebugApplicationThread*  prptFocus,  
   BREAKRESUMEACTION               bra,  
   ERRORRESUMEACTION               era  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `prptFocus`  
 [in] Para seguir los pasos modos, el subproceso que se verán afectados por el modo de ejecución paso a paso.  
  
 `bra`  
 [in] La acción que se realizará al reanudar la aplicación.  
  
 `era`  
 [in] La acción que se realizará en el caso de que la aplicación se detiene debido a un error.  
  
## <a name="return-value"></a>Valor devuelto  
 El método devuelve un objeto `HRESULT`. Entre los valores posibles se incluyen los que se indican en la tabla siguiente, entre otros.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
  
## <a name="remarks"></a>Comentarios  
 Este método continúa una aplicación que está actualmente en un punto de interrupción.  
  
## <a name="see-also"></a>Vea también  
 [IRemoteDebugApplication (interfaz)](../../winscript/reference/iremotedebugapplication-interface.md)   
 [Enumeración BREAKRESUMEACTION](../../winscript/reference/breakresumeaction-enumeration.md)   
 [ERRORRESUMEACTION (Enumeración)](../../winscript/reference/errorresumeaction-enumeration.md)