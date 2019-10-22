---
title: 'Iremotedebugapplication (:: ResumeFromBreakPoint | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: 7fead9c14efbe73bd006a5ff3e1cfb10ad40404b
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577459"
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
 de En el caso de los modos de ejecución, el subproceso que se verá afectado por el modo de ejecución.  
  
 `bra`  
 de Acción que se realizará al reanudar la aplicación.  
  
 `era`  
 de Acción que se debe llevar a cabo en caso de que la aplicación se detenga debido a un error.  
  
## <a name="return-value"></a>Valor devuelto  
 El método devuelve un objeto `HRESULT`. Entre los valores posibles se incluyen los que se indican en la tabla siguiente, entre otros.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
  
## <a name="remarks"></a>Comentarios  
 Este método continúa con una aplicación que está actualmente en un punto de interrupción.  
  
## <a name="see-also"></a>Vea también  
 @No__t_1 de la [interfaz iremotedebugapplication (](../../winscript/reference/iremotedebugapplication-interface.md)  
 @No__t_1 [enumeración breakresumeaction (](../../winscript/reference/breakresumeaction-enumeration.md)  
 [ERRORRESUMEACTION (Enumeración)](../../winscript/reference/errorresumeaction-enumeration.md)