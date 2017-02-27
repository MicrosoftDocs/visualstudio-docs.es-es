---
title: "IDebugProperty3::GetCustomViewerCount | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProperty3::GetCustomViewerCount"
helpviewer_keywords: 
  - "IDebugProperty3::GetCustomViewerCount"
ms.assetid: dc5bb3e4-dc85-46e4-98fa-c6be8583b985
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# IDebugProperty3::GetCustomViewerCount
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Obtiene el número de visores personalizados que estén disponibles para esta propiedad.  
  
## Sintaxis  
  
```cpp  
HRESULT GetCustomViewerCount(  
   ULONG* pcelt  
);  
```  
  
```c#  
int GetCustomViewerCount(  
   out uint pcelt  
);  
```  
  
#### Parámetros  
 `pcelt`  
 \[out\]  El número de visores personalizados disponibles para esta propiedad.  
  
## Valor devuelto  
 Si finaliza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.  
  
## Comentarios  
 Para admitir los visualizadores de tipo, este método reenvía la llamada al método de [GetCustomViewerCount](../../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewercount.md) .  Si el evaluador de expresiones también admite los visores personalizados para el tipo de propiedad, este método agrega el número de visores personalizados al valor devuelto.  
  
 Para obtener información detallada sobre las diferencias entre los visualizadores y visores escritos personalizados de, vea [Visualizador de tipo y el visor personalizado](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md).  
  
## Ejemplo  
 El ejemplo siguiente se muestra cómo implementar este método para un objeto **de CProperty** que expone la interfaz de [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) .  
  
```cpp#  
STDMETHODIMP CProperty::GetCustomViewerCount(ULONG* pcelt)  
{  
    if (pcelt == NULL)  
    {  
        return E_POINTER;  
    }  
  
    if (GetVisualizerService())  
    {  
        return m_pIEEVisualizerService->GetCustomViewerCount(pcelt);  
    }  
    else  
    {  
        return E_NOTIMPL;  
    }  
}  
```  
  
## Vea también  
 [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)   
 [GetCustomViewerCount](../../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewercount.md)   
 [Visualizador de tipo y el visor personalizado](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md)