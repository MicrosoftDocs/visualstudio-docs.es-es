---
title: "IDebugCustomAttribute::GetAttributeBytes | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugCustomAttribute::GetAttributeBytes"
helpviewer_keywords: 
  - "IDebugCustomAttribute::GetAttributeBytes"
ms.assetid: cf34583b-6530-4dcc-89f8-eb27e4e8d594
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# IDebugCustomAttribute::GetAttributeBytes
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Obtiene la información de atributos como un objeto binario de bytes.  
  
## Sintaxis  
  
```cpp#  
HRESULT GetAttributeBytes(   
   BYTE*  ppBlob,  
   DWORD* pdwLen  
);  
```  
  
```c#  
int GetAttributeBytes(  
   ref byte[] ppBlob,   
   ref uint   pdwLen  
);  
```  
  
#### Parámetros  
 `ppBlob`  
 \[in, out\]  Una matriz que se completa con los bytes del atributo.  
  
 `pdwLen`  
 \[in, out\]  Especifica el número de bytes máximo para regresar a la matriz de `ppBlob` y devuelve el número de bytes escritos realmente en la matriz.  
  
## Valor devuelto  
 Si finaliza correctamente, devuelve S\_OK; de lo contrario, devuelve un código de error.  
  
## Comentarios  
 Establezca el parámetro de `ppBlob` en un valor nulo para devolver el número de bytes de los atributos disponibles.  Después asigna una matriz y pase esa matriz en para el parámetro de `ppBlob` .  
  
 Bytes del atributo representan los datos sin procesar del atributo personalizado.  
  
## Vea también  
 [IDebugCustomAttribute](../../../extensibility/debugger/reference/idebugcustomattribute.md)