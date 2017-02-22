---
title: "IDebugProviderProgramNode2::UnmarshalDebuggeeInterface | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProviderProgramNode2::UnmarshalDebuggeeInterface"
helpviewer_keywords: 
  - "IDebugProviderProgramNode2::UnmarshalDebuggeeInterface"
ms.assetid: 2e4653c5-10f1-493c-9973-f31d266c5d48
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugProviderProgramNode2::UnmarshalDebuggeeInterface
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Obtiene una interfaz especificada a través de límites de procesos.  
  
## Sintaxis  
  
```cpp  
HRESULT UnmarshalDebuggeeInterface(  
   REFIID riid,  
   void** ppvObject  
);  
```  
  
```c#  
int UnmarshalDebuggeeInterface(  
   ref Guid   riid,  
   out IntPtr ppvObject  
);  
```  
  
#### Parámetros  
 `riid`  
 \[in\]  GUID de la interfaz a recopilar.  
  
 `ppvObject`  
 \[out\]  devuelve el objeto que implementa la interfaz deseada.  \[C\+\+\] puede ser conversión directamente al tipo de interfaz deseado.  \[C\#\] utilice el método de <xref:System.Runtime.InteropServices.Marshal.GetObjectForIUnknown%2A> para obtener la interfaz deseada.  
  
## Valor devuelto  
 Si finaliza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.  
  
## Comentarios  
 Se utiliza este método cuando el motor de depuración se ejecuta en el espacio del proceso de [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] y el programa que se está depurando se ejecuta en su propio espacio de proceso.  
  
## Vea también  
 [IDebugProviderProgramNode2](../../../extensibility/debugger/reference/idebugproviderprogramnode2.md)