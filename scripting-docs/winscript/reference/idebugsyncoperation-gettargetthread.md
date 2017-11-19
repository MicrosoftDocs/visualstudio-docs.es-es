---
title: IDebugSyncOperation::GetTargetThread | Documentos de Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IDebugSyncOperation.GetTargetThread
apilocation: jscript.dll
helpviewer_keywords: IDebugSyncOperation::GetTargetThread
ms.assetid: e6eeeb90-b5ed-4727-8434-fa3186c25013
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: df3e65d53e20dd51d045f26855c4f5e058dff159
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="idebugsyncoperationgettargetthread"></a>IDebugSyncOperation::GetTargetThread
Devuelve el subproceso de la aplicación de destino para esta operación sincrónica.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
HRESULT GetTargetThread(  
   IDebugApplicationThread**  ppatTarget  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `ppatTarget`  
 [out] El subproceso de la aplicación de destino para esta operación sincrónica.  
  
## <a name="return-value"></a>Valor devuelto  
 El método devuelve un objeto `HRESULT`. Entre los valores posibles se incluyen los que se indican en la tabla siguiente, entre otros.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
  
## <a name="remarks"></a>Comentarios  
 Este método devuelve el subproceso de la aplicación de destino para esta operación sincrónica.  
  
## <a name="see-also"></a>Vea también  
 [IDebugSyncOperation (Interfaz)](../../winscript/reference/idebugsyncoperation-interface.md)