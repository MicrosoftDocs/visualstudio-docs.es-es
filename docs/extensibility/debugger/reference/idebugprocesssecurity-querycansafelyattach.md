---
title: "IDebugProcessSecurity::QueryCanSafelyAttach | Microsoft Docs"
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
  - "IDebugProcessSecurity::QueryCanSafelyAttach"
ms.assetid: 63ec1ae8-27da-4574-aa15-1c986fe9fe58
caps.latest.revision: 4
caps.handback.revision: 4
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugProcessSecurity::QueryCanSafelyAttach
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Este método permite al proveedor de puerto muestra una advertencia antes de que el usuario asociado a un proceso seguro.  
  
## Sintaxis  
  
```cpp#  
HRESULT QueryCanSafelyAttach();  
```  
  
```c#  
int QueryCanSafelyAttach();  
```  
  
## Valor devuelto  
 Los valores devueltos son los siguientes:  
  
-   `S_OK`: Asociar el depurador a procesar es seguro y no se muestra ningún cuadro de diálogo de advertencia.  
  
-   `S_FALSE`: Asociar el depurador podría constituir un problema de seguridad y un cuadro de diálogo con una advertencia se muestra.  
  
-   `FAILURE`: Asociar el depurador para procesar errores.  
  
## Vea también  
 [IDebugProcessSecurity](../../../extensibility/debugger/reference/idebugprocesssecurity.md)