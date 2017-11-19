---
title: IDebugApplicationThread::SetDescription | Documentos de Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IDebugApplicationThread.SetDescription
apilocation: pdm.dll
helpviewer_keywords: IDebugApplicationThread::SetDescription
ms.assetid: 084e5b74-af95-41b4-ae55-01f6f4d22168
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 941e2e5ac9843c8894a4dd83e23ab132620b8a02
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="idebugapplicationthreadsetdescription"></a>IDebugApplicationThread::SetDescription
Establece la descripción de este subproceso.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
HRESULT SetDescription(  
   LPCOLESTR  pstrDescription  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pstrDescription`  
 [in] La descripción de este subproceso.  
  
## <a name="return-value"></a>Valor devuelto  
 El método devuelve un objeto `HRESULT`. Entre los valores posibles se incluyen los que se indican en la tabla siguiente, entre otros.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
  
## <a name="remarks"></a>Comentarios  
 Este método establece la descripción de este subproceso.  
  
## <a name="see-also"></a>Vea también  
 [IDebugApplicationThread (Interfaz)](../../winscript/reference/idebugapplicationthread-interface.md)