---
title: "IDebugSettingsCallback2::GetEEMetricDword | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "IDebugSettingsCallback2::GetEEMetricDword"
ms.assetid: c5f8f417-0ef0-4fd0-a779-b0a8ead4effe
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# IDebugSettingsCallback2::GetEEMetricDword
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Recupera un valor que corresponde a la especificada del evaluador de expresiones.  
  
## Sintaxis  
  
```cpp#  
HRESULT GetEEMetricDword(  
   REFGUID guidLang,  
   REFGUID guidVendor,  
   LPCWSTR pszMetric,  
   DWORD*  pdwValue  
);  
```  
  
```c#  
private int GetEEMetricDword(  
   ref Guid guidLang,  
   ref Guid guidVendor,  
   string   pszMetric,  
   out uint pdwValue  
);  
```  
  
#### Parámetros  
 `guidLang`  
 \[in\]  Identificador único del lenguaje de programación.  
  
 `guidVendor`  
 \[in\]  Identificador único del proveedor.  
  
 `pszMetric`  
 \[in\]  Nombre de la.  
  
 `pdwValue`  
 \[out\]  Devuelve el valor que corresponde a la cadena métricas.  
  
## Valor devuelto  
 Si finaliza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.  
  
## Vea también  
 [IDebugSettingsCallback2](../../../extensibility/debugger/reference/idebugsettingscallback2.md)