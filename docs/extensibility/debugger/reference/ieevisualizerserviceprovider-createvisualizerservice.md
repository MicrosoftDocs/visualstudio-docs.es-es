---
title: IEEVisualizerServiceProvider::CreateVisualizerService | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IEEVisualizerServiceProvider::CreateVisualizerService
helpviewer_keywords:
- IEEVisualizerServiceProvider::CreateVisualizerService method
ms.assetid: f366f7c9-358d-46c8-993f-32ff86539833
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 910265a63c9acc5f9835ff5006b6ac0c515a2d3e
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49926069"
---
# <a name="ieevisualizerserviceprovidercreatevisualizerservice"></a>IEEVisualizerServiceProvider::CreateVisualizerService
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