---
title: "IDebugMethodField::IsCustomAttributeDefined | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugMethodField::IsCustomAttributeDefined"
helpviewer_keywords: 
  - "IDebugMethodField::IsCustomAttributeDefined (método)"
ms.assetid: 1b5d95a8-cc87-4acb-9e6a-3928f3632b7c
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugMethodField::IsCustomAttributeDefined
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Determina si un atributo personalizado concreto ha sido definidas.  
  
## Sintaxis  
  
```cpp#  
HRESULT IsCustomAttributeDefined(   
   LPCOLESTR pszCustomAttributeName  
);  
```  
  
```c#  
int IsCustomAttributeDefined(  
   [In] string pszCustomAttributeName  
);  
```  
  
#### Parámetros  
 `pszCustomAttributeName`  
 \[in\]  Cadena que contiene el nombre del atributo personalizado para buscar.  
  
## Valor devuelto  
 Devuelve S\_OK si el atributo personalizado se define en este método, si no devuelve S\_FALSE.  
  
## Vea también  
 [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)