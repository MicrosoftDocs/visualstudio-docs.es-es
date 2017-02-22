---
title: "IDebugSettingsCallback2::GetMetricString | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "IDebugSettingsCallback2::GetMetricString"
  - "GetMetricString"
ms.assetid: ecc875a2-8ac6-444c-a839-5191a780fd6b
caps.latest.revision: 8
caps.handback.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugSettingsCallback2::GetMetricString
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Recupera la cadena del valor de medida dado su nombre.  
  
## Sintaxis  
  
```cpp#  
HRESULT GetMetricString(  
    LPCWSTR pszType,  
    REFGUID guidSection,  
    LPCWSTR pszMetric,  
    BSTR*   pbstrValue  
);  
```  
  
```c#  
private int GetMetricString(  
    string     pszType,  
    ref Guid   guidSection,  
    string     pszMetric,  
    out string pbstrValue  
);  
```  
  
#### Parámetros  
 `pszType`  
 \[in\]  Tipo de la.  
  
 `guidSection`  
 \[in\]  identificador único de la sección.  
  
 `pszMetric`  
 \[in\]  Nombre de la.  
  
 `pbstrValue`  
 \[out\]  Devuelve la cadena del valor de la.  
  
## Valor devuelto  
 Si finaliza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.  
  
## Vea también  
 [IDebugSettingsCallback2](../../../extensibility/debugger/reference/idebugsettingscallback2.md)