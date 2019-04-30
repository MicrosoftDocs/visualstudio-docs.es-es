---
title: ISimpleConnectionPoint::Advise | Microsoft Docs
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
ms.openlocfilehash: 98db9c92f682808ce8ecc9f6aa382a2eb2bd8495
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62786267"
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
 [in] Puntero a la `IDispatch` receptor de notificaciones de interfaz en el cliente. Receptor del cliente que recibe llamadas salientes desde el punto de conexión simple.  
  
 `pdwCookie`  
 [out] Puntero a un token devuelto que identifica esta conexión. El llamador utiliza este token posteriormente para eliminar la conexión pasándolo a la `ISimpleConnectionPoint::Unadvise` método. Si la conexión no se ha establecido correctamente, este valor es cero.  
  
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