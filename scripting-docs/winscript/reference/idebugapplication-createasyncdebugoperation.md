---
title: IDebugApplication::CreateAsyncDebugOperation | Documentos de Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IDebugApplication.CreateAsyncDebugOperation
apilocation: pdm.dll
helpviewer_keywords: IDebugApplication::CreateAsyncDebugOperation
ms.assetid: bc32b101-6364-4498-8458-bd5f3ab5ad94
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8714f4401249d73cf09d241ebf4c2b2115911d6b
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="idebugapplicationcreateasyncdebugoperation"></a>IDebugApplication::CreateAsyncDebugOperation
Proporciona acceso asincrónico a una operación de depuración sincrónico determinado.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
HRESULT CreateAsyncDebugOperation(  
   IDebugSyncOperation*    psdo,  
   IDebugAsyncOperation**  ppado  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `psdo`  
 [in] El objeto de la operación sincrónica de depuración.  
  
 `ppado`  
 [out] El objeto de la operación asincrónica de depuración.  
  
## <a name="return-value"></a>Valor devuelto  
 El método devuelve un objeto `HRESULT`. Entre los valores posibles se incluyen los que se indican en la tabla siguiente, entre otros.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
  
## <a name="remarks"></a>Comentarios  
 Este método permite motores de idioma evaluar expresiones de forma asincrónica sin sincronizar explícitamente con el subproceso del depurador. Para obtener más información, consulte [IDebugSyncOperation (interfaz)](../../winscript/reference/idebugsyncoperation-interface.md) y [IDebugAsyncOperation (interfaz)](../../winscript/reference/idebugasyncoperation-interface.md).  
  
## <a name="see-also"></a>Vea también  
 [IDebugApplication (interfaz)](../../winscript/reference/idebugapplication-interface.md)   
 [IDebugSyncOperation (interfaz)](../../winscript/reference/idebugsyncoperation-interface.md)   
 [IDebugAsyncOperation (Interfaz)](../../winscript/reference/idebugasyncoperation-interface.md)