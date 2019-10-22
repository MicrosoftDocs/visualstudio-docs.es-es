---
title: 'Isimpleconnectionpoint (:: Advise | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: d7d08d4774dffbfd840c674b15abe82bedb37e5f
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/18/2019
ms.locfileid: "72571829"
---
# <a name="isimpleconnectionpointadvise"></a>ISimpleConnectionPoint::Advise
Establece una conexión entre el objeto de punto de conexión simple y el receptor del cliente.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
HRESULT Advise(  
   IDispatch*  pdisp,  
   DWORD*      pdwCookie  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pdisp`  
 de Puntero a la interfaz de `IDispatch` en el receptor de notificaciones del cliente. El receptor del cliente recibe llamadas salientes desde el punto de conexión simple.  
  
 `pdwCookie`  
 enuncia Puntero a un token devuelto que identifica de forma única esta conexión. El autor de la llamada utiliza este token más adelante para eliminar la conexión pasándola al método `ISimpleConnectionPoint::Unadvise`. Si la conexión no se estableció correctamente, este valor es cero.  
  
## <a name="return-value"></a>Valor devuelto  
 El método devuelve un objeto `HRESULT`. Entre los valores posibles se incluyen los que se indican en la tabla siguiente, entre otros.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
  
## <a name="remarks"></a>Comentarios  
 Este método establece una conexión entre el objeto de punto de conexión simple y el receptor del cliente.  
  
## <a name="see-also"></a>Vea también  
 @No__t_1 de la [interfaz isimpleconnectionpoint (](../../winscript/reference/isimpleconnectionpoint-interface.md)  
 [ISimpleConnectionPoint::Unadvise](../../winscript/reference/isimpleconnectionpoint-unadvise.md)