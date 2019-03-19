---
title: IDebugApplication::CreateAsyncDebugOperation | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: c60c84dbd3be9248e2bd075e65d53f7f9361d0b5
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/19/2019
ms.locfileid: "58159314"
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