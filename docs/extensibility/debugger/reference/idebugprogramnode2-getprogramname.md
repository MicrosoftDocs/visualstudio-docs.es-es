---
title: "IDebugProgramNode2::GetProgramName | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProgramNode2::GetProgramName"
helpviewer_keywords: 
  - "IDebugProgramNode2::GetProgramName"
ms.assetid: 510c7f5d-48ff-4d9f-ad79-fbad9f15239d
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugProgramNode2::GetProgramName
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Obtiene el nombre del programa.  
  
## Sintaxis  
  
```cpp#  
HRESULT GetProgramName (   
   BSTR* pbstrProgramName  
);  
```  
  
```c#  
int GetProgramName (   
   out string pbstrProgramName  
);  
```  
  
#### Parámetros  
 `pbstrProgramName`  
 \[out\]  Devuelve el nombre del programa.  
  
## Valor devuelto  
 Si finaliza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.  
  
## Comentarios  
 El nombre de un programa no es lo mismo que la ruta de acceso al programa, aunque el nombre del programa pueda ser parte de esta ruta.  
  
## Ejemplo  
 El ejemplo siguiente se muestra cómo implementar este método para un objeto simple de `CProgram` que implemente la interfaz de [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) .  La función de `MakeBstr` asigna una copia de la cadena especificada como BSTR.  
  
```cpp#  
HRESULT CProgram::GetProgramName(BSTR* pbstrProgramName) {    
   if (!pbstrProgramName)    
      return E_INVALIDARG;    
  
   // Assign the member program name to the passed program name.    
   *pbstrProgramName = MakeBstr(m_pszProgramName);    
   return NOERROR;    
}    
```  
  
## Vea también  
 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)