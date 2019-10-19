---
title: 'Isimpleconnectionpoint (:: Unadvise | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- ISimpleConnectionPoint.Unadvise
apilocation:
- pdm.dll
helpviewer_keywords:
- ISimpleConnectionPoint::Unadvise
ms.assetid: eae06a58-ed42-4839-aad4-14420b15343f
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e00c172fd33eb0ccf27aaf28e0e2f692c1a353ab
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/18/2019
ms.locfileid: "72571748"
---
# <a name="isimpleconnectionpointunadvise"></a>ISimpleConnectionPoint::Unadvise
Finaliza una conexión de consulta previamente establecida a través de `ISimpleConnectionPoint::Advise`.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
HRESULT Unadvise(  
   DWORD  dwCookie  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `dwCookie`  
 de Token de la conexión que se va a finalizar, tal como se devuelve desde `ISimpleConnectionPoint::Advise`.  
  
## <a name="return-value"></a>Valor devuelto  
 El método devuelve un objeto `HRESULT`. Entre los valores posibles se incluyen los que se indican en la tabla siguiente, entre otros.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
  
## <a name="remarks"></a>Comentarios  
 Cuando finaliza una conexión de consulta, el punto de conexión llama al método `Release` en el puntero que se guardó para la conexión durante el método `ISimpleConnectionPoint::Advise`. Esta llamada invierte el `AddRef` que se realizó durante la `ISimpleConnectionPoint::Advise` cuando el punto de conexión llama a la `QueryInterface` del receptor de consulta.  
  
## <a name="see-also"></a>Vea también  
 [ISimpleConnectionPoint (Interfaz)](../../winscript/reference/isimpleconnectionpoint-interface.md)