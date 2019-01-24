---
title: IDebugApplication::CreateAsyncDebugOperation | Documentos de Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugApplication.CreateAsyncDebugOperation
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugApplication::CreateAsyncDebugOperation
ms.assetid: bc32b101-6364-4498-8458-bd5f3ab5ad94
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 30051276b682bdf906db72bc2682e1c5d58c455a
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/08/2019
ms.locfileid: "54090706"
---
# <a name="idebugapplicationcreateasyncdebugoperation"></a>IDebugApplication::CreateAsyncDebugOperation
Proporciona acceso asincrónico a una operación de depuración sincrónica determinada.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
HRESULT CreateAsyncDebugOperation(  
   IDebugSyncOperation*    psdo,  
   IDebugAsyncOperation**  ppado  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `psdo`  
 [in] El objeto de la operación de depuración sincrónica.  
  
 `ppado`  
 [out] El objeto de la operación de depuración asincrónica.  
  
## <a name="return-value"></a>Valor devuelto  
 El método devuelve un objeto `HRESULT`. Entre los valores posibles se incluyen los que se indican en la tabla siguiente, entre otros.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
  
## <a name="remarks"></a>Comentarios  
 Este método permite que los motores de lenguaje evaluar las expresiones de forma asincrónica sin sincronizar explícitamente con el subproceso del depurador. Para obtener más información, consulte [IDebugSyncOperation (interfaz)](../../winscript/reference/idebugsyncoperation-interface.md) y [IDebugAsyncOperation (interfaz)](../../winscript/reference/idebugasyncoperation-interface.md).  
  
## <a name="see-also"></a>Vea también  
 [IDebugApplication (interfaz)](../../winscript/reference/idebugapplication-interface.md)   
 [IDebugSyncOperation (interfaz)](../../winscript/reference/idebugsyncoperation-interface.md)   
 [IDebugAsyncOperation (Interfaz)](../../winscript/reference/idebugasyncoperation-interface.md)