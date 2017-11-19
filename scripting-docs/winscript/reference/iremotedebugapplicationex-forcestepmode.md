---
title: IRemoteDebugApplicationEx:ForceStepMode | Documentos de Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IRemoteDebugApplicationEx:ForceStepMode
apilocation: scrobj.dll
helpviewer_keywords: IRemoteDebugApplicationEx:ForceStepMode
ms.assetid: 83e69a3e-e4c9-4ddd-b01b-1820e4177a03
caps.latest.revision: "5"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: add26689122ffe4944b4bbad15106a825d43ccf0
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="iremotedebugapplicationexforcestepmode"></a>IRemoteDebugApplicationEx:ForceStepMode
Fuerza al depurador en modo paso a paso.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
HRESULT ForceStepMode(  
   IRemoteDebugApplicationThread*  pStepThread  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pStepThread`  
 [in] Subproceso para el Monitor de depuración de proceso paso a paso. Si es null, el PDM borra su subproceso de ejecución paso a paso.  
  
## <a name="return-value"></a>Valor devuelto  
 El método devuelve un objeto `HRESULT`. Entre los valores posibles se incluyen los que se indican en la tabla siguiente, entre otros.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
  
## <a name="remarks"></a>Comentarios  
  
## <a name="see-also"></a>Vea también  
 [IRemoteDebugApplicationEx (Interfaz)](http://msdn.microsoft.com/en-us/2f65fa67-06b7-4053-8945-22383ab66343)