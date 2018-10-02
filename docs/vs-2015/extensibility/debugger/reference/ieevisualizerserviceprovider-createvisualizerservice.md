---
title: IEEVisualizerServiceProvider::CreateVisualizerService | Documentos de Microsoft
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
- IEEVisualizerServiceProvider::CreateVisualizerService
helpviewer_keywords:
- IEEVisualizerServiceProvider::CreateVisualizerService method
ms.assetid: f366f7c9-358d-46c8-993f-32ff86539833
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 8cf31da1dab9e53a1c473ee8024a7fe1cb9a5f2d
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47579977"
---
# <a name="ieevisualizerserviceprovidercreatevisualizerservice"></a>IEEVisualizerServiceProvider::CreateVisualizerService
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [IEEVisualizerServiceProvider::CreateVisualizerService](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/ieevisualizerserviceprovider-createvisualizerservice).  
  
Este método crea un servicio de visualizador.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
HRESULT CreateVisualizerService(  
   IDebugBinder*              binder,  
   IDebugSymbolProvider*      pSymProv,  
   IDebugAddress*             pAddress,  
   IEEVisualizerDataProvider* dataProvider,  
   IEEVisualizerService**     ppService  
);  
```  
  
```csharp  
int CreateVisualizerService(  
   IDebugBinder binder,  
   IDebugSymbolProvider      pSymProv,  
   IDebugAddress             pAddress,  
   IEEVisualizerDataProvider dataProvider,  
   out IEEVisualizerService  ppService  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `binder`  
 [in] El [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md) objeto pasa a [EvaluateSync](../../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md).  
  
 `pSymProv`  
 [in] El [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md) objeto pasa a `IDebugParsedExpression::EvaluateSync`.  
  
 `pAddress`  
 [in] El [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) objeto pasa a `IDebugParsedExression::EvaluateSync`.  
  
 `dataProvider`  
 [in] Un objeto que implementa el [IEEVisualizerDataProvider](../../../extensibility/debugger/reference/ieevisualizerdataprovider.md) interfaz (proporcionado por el evaluador de expresiones).  
  
 `ppService`  
 [out] El servicio creado.  
  
## <a name="return-value"></a>Valor devuelto  
 Si es correcto, devuelve `S_OK`; en caso contrario, devuelve un código de error.  
  
## <a name="remarks"></a>Comentarios  
 El `binder`, `pSymProv`, y `pAddress` parámetros se pasaron a la `IDebugParsedExpression::EvaluateSync` método. `CreateVisualizerService` es que se llame solo desde `IDebugParsedExpression::EvaluateSync` como parte de compatibilidad con de un evaluador los visualizadores de tipo.  
  
## <a name="see-also"></a>Vea también  
 [IEEVisualizerServiceProvider](../../../extensibility/debugger/reference/ieevisualizerserviceprovider.md)   
 [EvaluateSync](../../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)   
 [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)   
 [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)   
 [IEEVisualizerDataProvider](../../../extensibility/debugger/reference/ieevisualizerdataprovider.md)

