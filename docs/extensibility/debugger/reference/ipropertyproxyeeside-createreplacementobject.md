---
title: "IPropertyProxyEESide::CreateReplacementObject | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IPropertyProxyEESide::CreateReplacementObject"
helpviewer_keywords: 
  - "IPropertyProxyEESide::CreateReplacementObject"
ms.assetid: 0cfe79b8-c3f1-48b0-a225-e39dee2c92fe
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# IPropertyProxyEESide::CreateReplacementObject
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Crea una copia de un objeto específico de datos al evaluador \(EE\) de expresiones.  
  
## Sintaxis  
  
```cpp  
HRESULT CreateReplacementObject(  
   IEEDataStorage*  dataIn,  
   IEEDataStorage** dataOut  
);  
```  
  
```c#  
int CreateReplacementObject(  
   IEEDataStorage     dataIn,  
   out IEEDataStorage dataOut  
);  
```  
  
#### Parámetros  
 `dataIn`  
 \[in\]  Un objeto de [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md) que contiene los datos que se copiarán.  
  
 `dataOut`  
 \[out\]  devuelve un nuevo objeto de `IEEDataStorage` .  
  
## Valor devuelto  
 Si finaliza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.  
  
## Comentarios  
 Este método recibe un objeto de [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md) que representa una matriz de bytes.  Este objeto de datos entrantes no se implementan normalmente por aa.  Sin embargo, el objeto devuelto por este método se implementa siempre por aa, donde permite a aa implementar la interfaz de `IEEDataStorage` se desea cualquier clase.  
  
 Observe que los datos proporcionados por el objeto de entrada de `IEEDataStorage` deben ser los mismos datos en el objeto de salida de `IEEDataStorage` .  
  
## Vea también  
 [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)   
 [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)