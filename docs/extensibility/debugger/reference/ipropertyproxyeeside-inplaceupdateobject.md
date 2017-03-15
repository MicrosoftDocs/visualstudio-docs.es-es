---
title: "IPropertyProxyEESide::InPlaceUpdateObject | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IPropertyProxyEESide::InPlaceUpdateObject"
helpviewer_keywords: 
  - "IPropertyProxyEESide::InPlaceUpdateObject"
ms.assetid: abf89411-1853-4f23-b244-d5e0afa197b1
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# IPropertyProxyEESide::InPlaceUpdateObject
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Actualiza los datos de objeto con el objeto de datos especificado y devuelve un nuevo objeto de datos que representa los nuevos datos de objeto.  
  
## Sintaxis  
  
```cpp#  
HRESULT InPlaceUpdateObject(  
   [in] IEEDataStorage*   dataIn,  
   [out] IEEDataStorage** dataOut  
);  
```  
  
```c#  
int InPlaceUpdateObject(  
   IEEDataStorage     dataIn,  
   out IEEDataStorage dataOut  
);  
```  
  
#### Parámetros  
 `dataIn`  
 \[in\]  un objeto de [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md) que contiene los nuevos datos.  
  
 `dataOut`  
 \[out\]  devuelve un nuevo objeto de `IEEDataStorage` que contiene los datos reemplazados.  
  
## Valor devuelto  
 Si finaliza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.  
  
## Comentarios  
 Este método actualiza realmente los datos de objeto.  Los datos del objeto devuelto de [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md) no necesita ser iguales que los datos del objeto de entrada de `IEEDataStorage` , pero el objeto devuelto deben reflejar el valor actual de la propiedad.  
  
 El objeto de datos entrantes no se implementan normalmente por aa.  Sin embargo, el objeto devuelto por este método se implementa siempre por aa, donde permite a aa implementar la interfaz de `IEEDataStorage` se desea cualquier clase.  
  
 el método de [CreateReplacementObject](../../../extensibility/debugger/reference/ipropertyproxyeeside-createreplacementobject.md) crea un objeto de datos basado en el objeto de datos entrantes pero no afecta a los datos originales de la propiedad.  
  
## Vea también  
 [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)   
 [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)   
 [CreateReplacementObject](../../../extensibility/debugger/reference/ipropertyproxyeeside-createreplacementobject.md)