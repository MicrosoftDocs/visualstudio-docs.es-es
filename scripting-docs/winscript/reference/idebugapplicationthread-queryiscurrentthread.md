---
title: IDebugApplicationThread::QueryIsCurrentThread | Documentos de Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- IDebugApplicationThread.QueryIsCurrentThread
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugApplicationThread::QueryIsCurrentThread
ms.assetid: 1580d3aa-3be8-4779-ac7b-41ab5c9edede
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3a291005a7c5b85230c55c736c68de82c0290d0e
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="idebugapplicationthreadqueryiscurrentthread"></a>IDebugApplicationThread::QueryIsCurrentThread
Determina si este subproceso es el subproceso actualmente en ejecución.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
HRESULT QueryIsCurrentThread();  
```  
  
#### <a name="parameters"></a>Parámetros  
 Este método no toma ningún parámetro.  
  
## <a name="return-value"></a>Valor devuelto  
 El método devuelve un objeto `HRESULT`. Entre los valores posibles se incluyen los que se indican en la tabla siguiente, entre otros.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente y se trata el subproceso actualmente en ejecución.|  
|`S_FALSE`|Esto no es el subproceso actualmente en ejecución.|  
  
## <a name="remarks"></a>Comentarios  
 Este método determina si este subproceso es el subproceso actualmente en ejecución.  
  
## <a name="see-also"></a>Vea también  
 [IDebugApplicationThread (Interfaz)](../../winscript/reference/idebugapplicationthread-interface.md)