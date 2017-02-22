---
title: "IDebugProperty3::DestroyObjectID | Microsoft Docs"
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
  - "IDebugProperty3::DestroyObjectID"
helpviewer_keywords: 
  - "IDebugProperty3::DestroyObjectID"
ms.assetid: bd08f356-cc67-4717-98c9-c3d00cad2040
caps.latest.revision: 9
caps.handback.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugProperty3::DestroyObjectID
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Destruye el identificador único asociado a esta propiedad, que indica que el llamador utiliza ya no identifiquen esta propiedad únicamente el resto de las propiedades.  
  
## Sintaxis  
  
```cpp  
HRESULT DestroyObjectID(  
   void  
);  
```  
  
```c#  
int DestroyObjectID();  
```  
  
## Valor devuelto  
 Si finaliza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.  
  
## Comentarios  
 Si el motor de depuración no necesita admitir los id. únicos para una propiedad \(porque contrólelos ya únicamente internamente\), puede devolver simplemente `E_NOTIMPL` para este método.  
  
 Los id. únicos se crean con una llamada al método de [CreateObjectID](../../../extensibility/debugger/reference/idebugproperty3-createobjectid.md) cuando el llamador desea asegurarse de que esta propiedad se identifica de forma exclusiva entre las demás propiedades.  
  
## Vea también  
 [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)   
 [CreateObjectID](../../../extensibility/debugger/reference/idebugproperty3-createobjectid.md)