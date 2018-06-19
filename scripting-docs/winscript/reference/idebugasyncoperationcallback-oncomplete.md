---
title: IDebugAsyncOperationCallBack::onComplete | Documentos de Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugAsyncOperationCallBack.onComplete
apilocation:
- jscript.dll
helpviewer_keywords:
- IDebugAsyncOperationCallBack::onComplete
ms.assetid: d4023f5a-41f9-4948-b0dc-3317d61bb783
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: bc55918c25da695f9eab470bf39fc648910ddc97
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
ms.locfileid: "24725925"
---
# <a name="idebugasyncoperationcallbackoncomplete"></a>IDebugAsyncOperationCallBack::onComplete
Indica que un resultado está disponible en una operación asincrónica de depuración.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
HRESULT onComplete();  
```  
  
#### <a name="parameters"></a>Parámetros  
 Este método no toma ningún parámetro.  
  
## <a name="return-value"></a>Valor devuelto  
 El método devuelve un objeto `HRESULT`. Entre los valores posibles se incluyen los que se indican en la tabla siguiente, entre otros.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
  
## <a name="remarks"></a>Comentarios  
 Este método indica que un resultado está disponible en un `IDebugAsyncOperation` objeto. El evento se desencadena en el subproceso del depurador.  
  
## <a name="see-also"></a>Vea también  
 [IDebugAsyncOperationCallBack (interfaz)](../../winscript/reference/idebugasyncoperationcallback-interface.md)   
 [IDebugAsyncOperation (Interfaz)](../../winscript/reference/idebugasyncoperation-interface.md)