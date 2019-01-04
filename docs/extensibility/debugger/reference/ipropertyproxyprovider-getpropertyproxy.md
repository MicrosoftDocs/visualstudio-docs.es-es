---
title: IPropertyProxyProvider::GetPropertyProxy | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IPropertyProxyProvider::GetPropertyProxy
helpviewer_keywords:
- IPropertyProxyProvider::GetPropertyProxy
ms.assetid: 3ebb7515-5bfe-48f4-9b8d-721b8f664eb6
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: b97b1f3d9b2bbdd3611ea95a05da341fd7e081f3
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53934682"
---
# <a name="ipropertyproxyprovidergetpropertyproxy"></a>IPropertyProxyProvider::GetPropertyProxy
Recupera la interfaz de proxy de la propiedad para el identificador del proxy especificado.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
HRESULT GetPropertyProxy(  
   DWORD                  dwID,  
   IPropertyProxyEESide** proxy  
);  
```  
  
```csharp  
int GetPropertyProxy(  
   uint                     dwID,  
   out IPropertyProxyEESide proxy  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `dwID`  
 [in] Id. del proxy de la propiedad deseada.  
  
 `proxy`  
 [out] Devuelve un [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md) objeto.  
  
## <a name="return-value"></a>Valor devuelto  
 Si es correcto, devuelve `S_OK`; en caso contrario, devuelve un código de error.  
  
## <a name="remarks"></a>Comentarios  
 Para admitir los visualizadores de tipo externo, este método normalmente reenvía la llamada a la [GetPropertyProxy](../../../extensibility/debugger/reference/ieevisualizerservice-getpropertyproxy.md) método. Consulte [visualización y ver datos](../../../extensibility/debugger/visualizing-and-viewing-data.md) para obtener más información sobre cómo se obtiene el IEEVisualizerService.  
  
## <a name="see-also"></a>Vea también  
 [IPropertyProxyProvider](../../../extensibility/debugger/reference/ipropertyproxyprovider.md)   
 [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)   
 [GetPropertyProxy](../../../extensibility/debugger/reference/ieevisualizerservice-getpropertyproxy.md)   
 [Visualización de datos](../../../extensibility/debugger/visualizing-and-viewing-data.md)