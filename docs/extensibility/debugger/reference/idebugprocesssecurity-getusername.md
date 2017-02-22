---
title: "IDebugProcessSecurity::GetUserName | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "IDebugProcessSecurity::GetUserName"
ms.assetid: c73c60ac-da6e-45ae-8f04-95353a24ca3e
caps.latest.revision: 4
caps.handback.revision: 4
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugProcessSecurity::GetUserName
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Obtiene el nombre de usuario del proveedor de puerto.  
  
## Sintaxis  
  
```cpp#  
HRESULT GetUserName(  
    BSTR *pbstrUserName  
);  
```  
  
```c#  
int GetUserName (  
    string pbstrUserName  
);  
```  
  
#### Parámetros  
 `pbstrUserName`  
 \[out\]  Cadena que contiene el nombre de usuario.  
  
## Valor devuelto  
 si el método tiene éxito, devuelve `S_OK`.  si no devuelve un código de error.  
  
## Comentarios  
 `GetUserName` devuelve el nombre de usuario que se muestra en la columna de **Nombre de usuario** del cuadro de diálogo de **Adjuntar a procesar** .  Para ver el cuadro de diálogo de **Adjuntar a procesar** , haga clic en **Adjuntar a procesar** en el menú de **Herramientas** en el entorno de desarrollo integrado de \(IDE\) [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] .  
  
## Vea también  
 [IDebugProcessSecurity](../../../extensibility/debugger/reference/idebugprocesssecurity.md)