---
title: "IDebugSettingsCallback2::GetEEMetricFile | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "IDebugSettingsCallback2::GetEEMetricFile"
ms.assetid: 3a0bf9e5-bbd2-4d15-840d-8244732787fc
caps.latest.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugSettingsCallback2::GetEEMetricFile
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Recupera el archivo métrica del evaluador de expresiones dado el nombre o la métrica.  
  
## Sintaxis  
  
```cpp#  
HRESULT GetEEMetricFile(  
   REFGUID guidLang,  
   REFGUID guidVendor,  
   LPCWSTR pszMetric,  
   BSTR*   pbstrValue  
);  
```  
  
```c#  
private int GetEEMetricFile(  
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
 \[out\]  Devuelve el contenido del archivo métrica como cadena.  
  
## Valor devuelto  
 Si finaliza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.  
  
## Vea también  
 [IDebugSettingsCallback2](../../../extensibility/debugger/reference/idebugsettingscallback2.md)