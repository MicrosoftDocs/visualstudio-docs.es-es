---
title: "IDebugBinder3::GetEEService | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugBinder3::GetEEService"
helpviewer_keywords: 
  - "IDebugBinder3::GetEEService (método)"
ms.assetid: eb07aa40-8cd9-4a52-a4c7-4affd2307a01
caps.latest.revision: 12
caps.handback.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugBinder3::GetEEService
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

este método devuelve un servicio solicitado.  
  
## Sintaxis  
  
```cpp  
HRESULT GetEEService(  
   [in] GUID        vendor,  
   [in] GUID        language,  
   [in] GUID        iid,  
   [out] IUnknown** ppService  
);  
```  
  
```c#  
Int GetEEService(  
   Guid       vendor,  
   Guid       language,  
   Guid       iid,  
   out object ppService  
);  
```  
  
#### Parámetros  
 `vendor`  
 \[in\]  `GUID` de un proveedor \(un valor nulo es aceptable\).  
  
 `language`  
 \[in\]  `GUID` de un lenguaje \(un valor nulo es aceptable\).  
  
 `iid`  
 \[in\]  `IID` de servicio a recopilar.  
  
 `ppService`  
 \[out\]  Interfaz para el servicio solicitado.  
  
## Valor devuelto  
 Si finaliza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.  
  
## Comentarios  
 Pase `IID` para la interfaz de [IEEVisualizerServiceProvider](../../../extensibility/debugger/reference/ieevisualizerserviceprovider.md) \(`IID_IEEVisualizerServiceProvider`\) para ver si escribir el servicio del visualizador está disponible.  Si es así el evaluador de expresiones puede obtener la interfaz de [IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md) para admitir los visualizadores de tipo.  Para obtener información más detallada, vea [Visualizar y visualización de datos](../../../extensibility/debugger/visualizing-and-viewing-data.md).  
  
## Vea también  
 [IDebugBinder3](../../../extensibility/debugger/reference/idebugbinder3.md)   
 [IEEVisualizerServiceProvider](../../../extensibility/debugger/reference/ieevisualizerserviceprovider.md)   
 [IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md)   
 [Visualizar y visualización de datos](../../../extensibility/debugger/visualizing-and-viewing-data.md)