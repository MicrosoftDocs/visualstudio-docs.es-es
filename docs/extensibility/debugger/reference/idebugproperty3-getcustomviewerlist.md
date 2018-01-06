---
title: IDebugProperty3::GetCustomViewerList | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugProperty3::GetCustomViewerList
helpviewer_keywords: IDebugProperty3::GetCustomViewerList
ms.assetid: 74490fd8-6f44-4618-beea-dab64961bb8a
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 1cd719891b4c0baec4d143c4a848e0c1d31ad6e3
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="idebugproperty3getcustomviewerlist"></a>IDebugProperty3::GetCustomViewerList
Obtiene una lista de visores personalizados asociados a esta propiedad.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
HRESULT GetCustomViewerList(  
   ULONG                celtSkip,  
   ULONG                celtRequested,  
   DEBUG_CUSTOM_VIEWER* rgViewers,  
   ULONG*               pceltFetched  
);  
```  
  
```csharp  
int GetCustomViewerList(  
   uint                  celtSkip,  
   uint                  celtRequested,  
   DEBUG_CUSTOM_VIEWER[] rgViewers,  
   out uint              pceltFetched  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `celtSkip`  
 [in] El número de lectores que omita las.  
  
 `celtRequested`  
 [in] El número de visores para recuperar (también especifica el tamaño de la `rgViewers` matriz).  
  
 `rgViewers`  
 [entrada, salida] Matriz de [DEBUG_CUSTOM_VIEWER](../../../extensibility/debugger/reference/debug-custom-viewer.md) estructuras que deben rellenarse.  
  
 `pceltFetched`  
 [out] Devuelve el número real de visores.  
  
## <a name="return-value"></a>Valor devuelto  
 Si se realiza correctamente, devuelve `S_OK`; en caso contrario, devuelve un código de error.  
  
## <a name="remarks"></a>Comentarios  
 Para admitir los visualizadores de tipo, este método reenvía la llamada a la [GetCustomViewerList](../../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewerlist.md) método. Si el evaluador de expresiones también admite visores personalizados para el tipo de esta propiedad, este método puede anexar los visores personalizados adecuados a la lista.  
  
 Vea [visualizador de tipo y el visor personalizado](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md) para obtener más información sobre las diferencias entre los visualizadores de tipo y visores personalizados.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra cómo implementar este método para un **CProperty** objeto que expone la [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) interfaz.  
  
```cpp  
STDMETHODIMP CProperty::GetCustomViewerList(ULONG celtSkip, ULONG celtRequested, DEBUG_CUSTOM_VIEWER* prgViewers, ULONG* pceltFetched)  
{  
    if (NULL == prgViewers)  
    {  
        return E_POINTER;  
    }  
  
    if (GetVisualizerService())  
    {  
        return m_pIEEVisualizerService->GetCustomViewerList(celtSkip, celtRequested, prgViewers, pceltFetched);  
    }  
    else  
    {  
        return E_NOTIMPL;  
    }  
}  
```  
  
## <a name="see-also"></a>Vea también  
 [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)   
 [DEBUG_CUSTOM_VIEWER](../../../extensibility/debugger/reference/debug-custom-viewer.md)   
 [GetCustomViewerList](../../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewerlist.md)   
 [Visualizador de tipo y visor personalizado](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md)