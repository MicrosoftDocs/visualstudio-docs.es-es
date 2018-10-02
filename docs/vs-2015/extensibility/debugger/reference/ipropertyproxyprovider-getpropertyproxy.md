---
title: IPropertyProxyProvider::GetPropertyProxy | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IPropertyProxyProvider::GetPropertyProxy
helpviewer_keywords:
- IPropertyProxyProvider::GetPropertyProxy
ms.assetid: 3ebb7515-5bfe-48f4-9b8d-721b8f664eb6
caps.latest.revision: 15
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 9478f9da9c54b950db77d442c1ab6cc4f72b7047
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47576536"
---
# <a name="ipropertyproxyprovidergetpropertyproxy"></a>IPropertyProxyProvider::GetPropertyProxy
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [IPropertyProxyProvider::GetPropertyProxy](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/ipropertyproxyprovider-getpropertyproxy).  
  
Recupera la interfaz de proxy de la propiedad para el identificador del proxy especificado.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp#  
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

