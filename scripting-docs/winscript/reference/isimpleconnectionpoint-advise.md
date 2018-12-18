---
title: ISimpleConnectionPoint::Advise | Documentos de Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- ISimpleConnectionPoint.Advise
apilocation:
- pdm.dll
helpviewer_keywords:
- ISimpleConnectionPoint::Advise
ms.assetid: 59ded60d-b938-4110-aca3-e69ba234ca9a
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7ec43d135401386a3f54f2c047040897f038ba19
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
ms.locfileid: "24733795"
---
# <a name="isimpleconnectionpointadvise"></a>ISimpleConnectionPoint::Advise
Establece una conexión entre el objeto de punto de conexión simple y el receptor del cliente.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
HRESULT Advise(  
   IDispatch*  pdisp,  
   DWORD*      pdwCookie  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pdisp`  
 [in] Puntero a la `IDispatch` interfaz en el cliente del aconseje receptor. Receptor del cliente recibe las llamadas salientes desde el punto de conexión simple.  
  
 `pdwCookie`  
 [out] Puntero a un token devuelto que identifica de forma única esta conexión. El llamador usa este token más adelante para eliminar la conexión y la transfiere a la `ISimpleConnectionPoint::Unadvise` método. Si la conexión no se ha establecido correctamente, este valor es cero.  
  
## <a name="return-value"></a>Valor devuelto  
 El método devuelve un objeto `HRESULT`. Entre los valores posibles se incluyen los que se indican en la tabla siguiente, entre otros.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
  
## <a name="remarks"></a>Comentarios  
 Este método establece una conexión entre el objeto de punto de conexión simple y el receptor del cliente.  
  
## <a name="see-also"></a>Vea también  
 [ISimpleConnectionPoint (interfaz)](../../winscript/reference/isimpleconnectionpoint-interface.md)   
 [ISimpleConnectionPoint::Unadvise](../../winscript/reference/isimpleconnectionpoint-unadvise.md)