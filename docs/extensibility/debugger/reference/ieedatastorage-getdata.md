---
title: "IEEDataStorage::GetData | Microsoft Docs"
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
  - "IEEDataStorage::GetData"
helpviewer_keywords: 
  - "IEEDataStorage::GetData"
ms.assetid: 4d384039-73d4-40b4-ace6-a2474c546397
caps.latest.revision: 7
caps.handback.revision: 7
ms.author: "gregvanl"
manager: "ghogen"
---
# IEEDataStorage::GetData
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Recupera el número de bytes especificado del objeto.  
  
## Sintaxis  
  
```cpp#  
HRESULT GetData(  
   ULONG  dataSize,  
   ULONG* sizeGotten,  
   BYTE*  data  
);  
```  
  
```c#  
int GetData(  
   uint     dataSize,  
   out uint sizeGotten,  
   byte[]   data  
);  
```  
  
#### Parámetros  
 `dataSize`  
 \[in\]  El número de bytes a recuperar \(la matriz de `data` debe contener por lo menos el número de bytes\).  
  
 `sizeGotten`  
 \[out\]  devuelve el número de bytes recuperados realmente.  
  
 `data`  
 \[in, out\]  Matriz que se completará con los datos solicitados.  
  
## Valor devuelto  
 Si finaliza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.  
  
## Comentarios  
 El uso recomendado de este método es recuperar todos los bytes de datos en una matriz local, dado que no hay forma de omitir sobre bytes en el proceso de extracción.  en este caso, el parámetro `dataSize` debe ser el valor devuelto por el método de [GetSize](../../../extensibility/debugger/reference/ieedatastorage-getsize.md) .  
  
## Vea también  
 [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)   
 [GetSize](../../../extensibility/debugger/reference/ieedatastorage-getsize.md)