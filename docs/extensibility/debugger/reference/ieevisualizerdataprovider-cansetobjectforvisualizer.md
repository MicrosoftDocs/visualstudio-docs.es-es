---
title: "IEEVisualizerDataProvider::CanSetObjectForVisualizer | Microsoft Docs"
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
  - "IEEVisualizerDataProvider::CanSetObjectForVisualizer"
helpviewer_keywords: 
  - "IEEVisualizerDataProvider::CanSetObjectForVisualizer (método)"
ms.assetid: 70fd3c6f-2f82-43a3-993b-c1dc8aa080bf
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# IEEVisualizerDataProvider::CanSetObjectForVisualizer
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

este método determina si el visualizador puede tener el objeto de datos que representa actualizado.  
  
## Sintaxis  
  
```cpp  
HRESULT CanSetObjectForVisualizer(  
   BOOL* b  
);  
```  
  
```c#  
int CanSetObjectForVisualizer(  
   out int b  
);  
```  
  
#### Parámetros  
 `b`  
 \[out\]  Cero \(`TRUE`\) si el objeto en el visualizador puede actualizarse, cero \(`FALSE`\) si no puede.  
  
## Valor devuelto  
 Si finaliza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.  
  
## Comentarios  
 Un objeto podría no ser modificable si se enlaza a memoria de solo lectura, por ejemplo.  
  
## Vea también  
 [IEEVisualizerDataProvider](../../../extensibility/debugger/reference/ieevisualizerdataprovider.md)