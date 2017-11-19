---
title: IRemoteDebugApplicationThread::SetNextStatement | Documentos de Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IRemoteDebugApplicationThread.SetNextStatement
apilocation: pdm.dll
helpviewer_keywords: IRemoteDebugApplicationThread::SetNextStatement
ms.assetid: 356766da-f7b7-4e8d-b4f3-2ab8da0609b8
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: fb23fa643f9a2333e17239a74d0da2f75e1ea791
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="iremotedebugapplicationthreadsetnextstatement"></a>IRemoteDebugApplicationThread::SetNextStatement
Ejecución de las fuerzas lo más cerca posible del contexto de código determinado, continúe en el contexto del marco especificado.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
HRESULT SetNextStatement(  
   IDebugStackFrame*   pStackFrame,  
   IDebugCodeContext*  pCodeContext  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pStackFrame`  
 [in] El objeto de marco de pila. Este argumento puede ser NULL, lo que implica que debe usarse el marco de pila actual.  
  
 `pCodeContext`  
 [in] El contexto del código. Este argumento puede ser NULL, lo que implica que debe usarse al contexto actual del código.  
  
## <a name="return-value"></a>Valor devuelto  
 El método devuelve un objeto `HRESULT`. Entre los valores posibles se incluyen los que se indican en la tabla siguiente, entre otros.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
  
## <a name="remarks"></a>Comentarios  
 Este método obliga a que continúe lo más cerca posible en el contexto del código especificado por la ejecución `pCodeContext`, en el contexto del marco especificado por `pStackFrame`. Cualquiera de estos argumentos puede ser `NULL`, que representa el contexto o el marco actual.  
  
## <a name="see-also"></a>Vea también  
 [IRemoteDebugApplicationThread (Interfaz)](../../winscript/reference/iremotedebugapplicationthread-interface.md)