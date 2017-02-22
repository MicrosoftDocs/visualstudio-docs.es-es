---
title: "IDebugSettingsCallback2::GetEEMetricString | Microsoft Docs"
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
  - "IDebugSettingsCallback2::GetEEMetricString"
ms.assetid: 85e3c093-6a91-4101-ab32-d8ac6eed4918
caps.latest.revision: 8
caps.handback.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugSettingsCallback2::GetEEMetricString
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Recupera la cadena de valor de métrica del evaluador de expresiones dado su nombre.  
  
## Sintaxis  
  
```cpp#  
HRESULT GetEEMetricString(  
   REFGUID guidLang,  
   REFGUID guidVendor,  
   LPCWSTR pszMetric,  
   BSTR*   pbstrValue  
);  
```  
  
```c#  
private int GetEEMetricString(  
   ref Guid   guidLang,  
   ref Guid   guidVendor,  
   string     pszMetric,  
   out string pbstrValue  
);  
```  
  
#### Parámetros  
 `guidLang`  
 \[in\]  Identificador único del lenguaje de programación.  
  
 `guidVendor`  
 \[in\]  Identificador único del proveedor.  
  
 `pszMetric`  
 \[in\]  Nombre de la.  
  
 `pbstrValue`  
 \[out\]  Devuelve la cadena métricas de valor.  
  
## Valor devuelto  
 Si finaliza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.  
  
## Vea también  
 [IDebugSettingsCallback2](../../../extensibility/debugger/reference/idebugsettingscallback2.md)