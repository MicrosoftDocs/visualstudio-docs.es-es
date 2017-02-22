---
title: "IDebugCustomAttributeQuery2::GetCustomAttributeByName | Microsoft Docs"
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
  - "IDebugCustomAttributeQuery2::GetCustomAttributeByName"
helpviewer_keywords: 
  - "IDebugCustomAttributeQuery2::GetCustomAttributeByName"
ms.assetid: 7428dfeb-8929-41b2-9b99-cb343a86c02d
caps.latest.revision: 9
caps.handback.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugCustomAttributeQuery2::GetCustomAttributeByName
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Obtiene los bytes de atributos personalizados con el nombre del atributo personalizado.  
  
## Sintaxis  
  
```cpp#  
HRESULT GetCustomAttributeByName(   
   LPCOLESTR pszCustomAttributeName,  
   BYTE*     ppBlob,  
   DWORD*    pdwLen  
);  
```  
  
```c#  
int GetCustomAttributeByName(  
   [In] string        pszCustomAttributeName,   
   [In, Out] byte[]   ppBlob,   
   [In, Out] ref uint pdwLen  
);  
```  
  
#### Parámetros  
 `pszCustomAttributeName`  
 \[in\]  Cadena que contiene el nombre del atributo personalizado para buscar.  
  
 `ppBlob`  
 \[in, out\]  Una matriz que se completa con los bytes del atributo personalizado.  
  
 `pdwLen`  
 \[in, out\]  Especifica el número de bytes máximo para regresar a la matriz de `ppBlob` y devuelve el número de bytes escritos realmente en la matriz.  
  
## Valor devuelto  
 Si finaliza correctamente, devuelve S\_OK o devuelve S\_FALSE si no existe el atributo personalizado.  De lo contrario, devuelve un código de error.  
  
## Comentarios  
 Establezca el parámetro de `ppBlob` en un valor nulo para devolver el número de bytes de los atributos disponibles.  Después asigna una matriz y pase esa matriz en para el parámetro de `ppBlob` .  
  
 Bytes del atributo representan los datos sin procesar del atributo personalizado.  
  
 Si los parámetros de `ppBlob` y de `pdwLen` se establecen un valor null, este método se puede utilizar para determinar si existe el atributo personalizado simplemente.  Una alternativa más sencilla, sin embargo, es llamar al método de [IsCustomAttributeDefined](../../../extensibility/debugger/reference/idebugcustomattributequery2-iscustomattributedefined.md) .  
  
## Vea también  
 [IDebugCustomAttributeQuery2](../../../extensibility/debugger/reference/idebugcustomattributequery2.md)   
 [IsCustomAttributeDefined](../../../extensibility/debugger/reference/idebugcustomattributequery2-iscustomattributedefined.md)