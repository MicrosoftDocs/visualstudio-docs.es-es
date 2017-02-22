---
title: "IDebugPortRequest2::GetPortName | Microsoft Docs"
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
  - "IDebugPortRequest2::GetPortName"
helpviewer_keywords: 
  - "IDebugPortRequest2::GetPortName"
ms.assetid: 53e2a3a4-bb34-4a02-a983-6bd84ea70587
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugPortRequest2::GetPortName
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Obtiene el nombre del puerto.  
  
## Sintaxis  
  
```cpp#  
HRESULT GetPortName(   
   BSTR* pbstrPortName  
);  
```  
  
```c#  
int GetPortName(   
   out string pbstrPortName  
);  
```  
  
#### Parámetros  
 `pbstrPortName`  
 \[out\]  Devuelve el nombre del puerto.  
  
## Valor devuelto  
 Si finaliza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.  
  
## Comentarios  
 La interfaz de [IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md) se suele pasar de un paquete de depuración \(el cliente\) a un proveedor de puerto \(el servidor\) para obtener una conexión a un puerto.  El paquete de depuración y el proveedor de puerto son conscientes de las opciones posibles del puerto.  Si una cadena simple puede describir el puerto, el método de `IDebugPortRequest2::GetPortName` tiene información suficiente para crear la conexión.  Si no, interfaces adicionales se pueden proporcionar al cliente, que puede obtenerse por el servidor mediante `IDebugPortRequest2::QueryInterface`.  
  
## Vea también  
 [IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md)