---
title: IEEVisualizerServiceProvider::CreateVisualizerService | Documentos de Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IEEVisualizerServiceProvider::CreateVisualizerService
helpviewer_keywords:
- IEEVisualizerServiceProvider::CreateVisualizerService method
ms.assetid: f366f7c9-358d-46c8-993f-32ff86539833
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: ed8327690c42f54a33209b2f0acfa45a138ec51c
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "68155086"
---
# <a name="ieevisualizerserviceprovidercreatevisualizerservice"></a>IEEVisualizerServiceProvider::CreateVisualizerService
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Este método crea un servicio de visualizador.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
HRESULT CreateVisualizerService(  
   IDebugBinder*              binder,  
   IDebugSymbolProvider*      pSymProv,  
   IDebugAddress*             pAddress,  
   IEEVisualizerDataProvider* dataProvider,  
   IEEVisualizerService**     ppService  
);  
```  
  
```csharp  
int CreateVisualizerService(  
   IDebugBinder binder,  
   IDebugSymbolProvider      pSymProv,  
   IDebugAddress             pAddress,  
   IEEVisualizerDataProvider dataProvider,  
   out IEEVisualizerService  ppService  
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
