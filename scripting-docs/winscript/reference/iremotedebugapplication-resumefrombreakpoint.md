---
title: IRemoteDebugApplication::ResumeFromBreakPoint | Documentos de Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IRemoteDebugApplication.ResumeFromBreakPoint
apilocation:
- pdm.dll
helpviewer_keywords:
- IRemoteDebugApplication::ResumeFromBreakPoint
ms.assetid: a613cc2b-1d69-4713-a235-64372c253b4a
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0603ef19426e27324daa39bf769e2c0667477be3
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/08/2019
ms.locfileid: "54089081"
---
# <a name="iremotedebugapplicationresumefrombreakpoint"></a>IRemoteDebugApplication::ResumeFromBreakPoint
Continúa una aplicación que está actualmente en un punto de interrupción.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
HRESULT ResumeFromBreakPoint(  
   IRemoteDebugApplicationThread*  prptFocus,  
   BREAKRESUMEACTION               bra,  
   ERRORRESUMEACTION               era  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `prptFocus`  
 [in] Para la ejecución paso a paso de los modos, el subproceso que se vea afectado por el modo de ejecución paso a paso.  
  
 `bra`  
 [in] La acción que se realizará al reanudar la aplicación.  
  
 `era`  
 [in] La acción que se realizará en el caso de que la aplicación se detuvo debido a un error.  
  
## <a name="return-value"></a>Valor devuelto  
 El método devuelve un objeto `HRESULT`. Entre los valores posibles se incluyen los que se indican en la tabla siguiente, entre otros.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
  
## <a name="remarks"></a>Comentarios  
 Este método sigue una aplicación que está actualmente en un punto de interrupción.  
  
## <a name="see-also"></a>Vea también  
 [IRemoteDebugApplication (interfaz)](../../winscript/reference/iremotedebugapplication-interface.md)   
 [BREAKRESUMEACTION (enumeración)](../../winscript/reference/breakresumeaction-enumeration.md)   
 [ERRORRESUMEACTION (Enumeración)](../../winscript/reference/errorresumeaction-enumeration.md)