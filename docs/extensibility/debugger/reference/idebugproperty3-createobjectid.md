---
title: "IDebugProperty3::CreateObjectID | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProperty3::CreateObjectID"
helpviewer_keywords: 
  - "IDebugProperty3::CreateObjectID"
ms.assetid: f2fa81e7-822f-456e-8729-a96a18eea771
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugProperty3::CreateObjectID
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Crea un identificador único para esta propiedad garantiza que es único entre las demás propiedades.  
  
## Sintaxis  
  
```cpp  
HRESULT CreateObjectID(  
   void  
);  
```  
  
```c#  
int CreateObjectID();  
```  
  
## Valor devuelto  
 Si finaliza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.  
  
## Comentarios  
 Se llama a este método cuando el administrador de depuración de sesión desea asegurarse de que esta propiedad se identifica de forma exclusiva entre las demás propiedades.  El motor de depuración \(DE\) admite este método a menos que las propiedades que trata de ya se identifican de forma exclusiva.  Si el OF no admite este método, devuelve `E_NOTIMPL`.  
  
 Cualquier identificador único creado con `CreateObjectID` se destruye cuando se llama al método de [DestroyObjectID](../../../extensibility/debugger/reference/idebugproperty3-destroyobjectid.md) ; esto también señala el final de la necesidad de forma exclusiva de identificar esta propiedad.  
  
> [!NOTE]
>  No hay ningún método para recuperar este identificador único, por lo que el OF puede hacer lo que desee para los identificadores. únicos cuando se llama al método de `CreateObjectID` .  
  
## Vea también  
 [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)   
 [DestroyObjectID](../../../extensibility/debugger/reference/idebugproperty3-destroyobjectid.md)