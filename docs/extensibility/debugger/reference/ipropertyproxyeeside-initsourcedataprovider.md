---
title: "IPropertyProxyEESide::InitSourceDataProvider | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IPropertyProxyEESide::InitSourceDataProvider"
helpviewer_keywords: 
  - "IPropertyProxyEESide::InitSourceDataProvider"
ms.assetid: 5156f593-5052-4e3a-9d02-081916fb342d
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# IPropertyProxyEESide::InitSourceDataProvider
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Inicializa los datos de origen para este objeto y devuelven un objeto que contiene los datos iniciales.  
  
## Sintaxis  
  
```cpp#  
HRESULT InitSourceDataProvider(  
   IEEDataStorage** dataOut  
);  
```  
  
```c#  
int InitSourceDataProvider(  
   out IEEDataStorage dataOut  
);  
```  
  
#### Parámetros  
 `dataOut`  
 \[out\]  devuelve un objeto de [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)  
  
## Valor devuelto  
 Si finaliza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.  
  
## Comentarios  
 Este método hace aquello que es necesario inicializar un objeto de modo que puede devolver una interfaz de [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md) en los datos de objeto.  Esto permite que los datos de objeto se ven y, si se permite, cambia un visualizador de tipo.  
  
## Vea también  
 [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)   
 [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)