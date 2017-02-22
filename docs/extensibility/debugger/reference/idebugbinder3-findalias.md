---
title: "IDebugBinder3::FindAlias | Microsoft Docs"
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
  - "IDebugBinder3::FindAlias"
helpviewer_keywords: 
  - "IDebugBinder3::FindAlias (método)"
ms.assetid: b8333701-2718-4983-8513-0875fb7cb730
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugBinder3::FindAlias
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

este método localiza alias, dado un nombre.  esto buscará todos los alias en el programa.  
  
## Sintaxis  
  
```cpp  
HRESULT FindAlias(  
   LPCOLESTR     pcstrName,  
   IDebugAlias** ppAlias  
);  
```  
  
```c#  
int FindAlias(  
   string          pcstrName,  
   out IDebugAlias ppAlias  
);  
```  
  
#### Parámetros  
 `pcstrName`  
 \[in\]  Nombre de alias que se va a buscar.  
  
 `ppAlias`  
 \[out\]  Alias encontró \(si existe\) representado por la interfaz de [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md) .  
  
## Valor devuelto  
 Si finaliza correctamente, devuelve `S_OK`; de lo contrario, devuelve `S_FALSE` \(si el alias no se encuentra\) o un código de error.  
  
## Comentarios  
 Este método inicializa el objeto de destino a null antes de llamar a; a continuación prueba por un valor NULL después para determinar si alias se encontró.  
  
## Vea también  
 [IDebugBinder3](../../../extensibility/debugger/reference/idebugbinder3.md)   
 [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md)