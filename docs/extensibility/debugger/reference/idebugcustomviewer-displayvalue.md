---
title: "IDebugCustomViewer::DisplayValue | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugCustomViewer::DisplayValue"
helpviewer_keywords: 
  - "IDebugCustomViewer::DisplayValue"
ms.assetid: 7a538248-5ced-450e-97cd-13fabe35fb1c
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# IDebugCustomViewer::DisplayValue
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Se llama a este método para mostrar el valor especificado.  
  
## Sintaxis  
  
```cpp#  
HRESULT DisplayValue(  
   HWND             hwnd,  
   DWORD            dwID,  
   IUnknown *       pHostServices,  
   IDebugProperty3* pDebugProperty);  
);  
```  
  
```c#  
int DisplayValue(  
   IntPtr          hwnd,   
   uint            dwID,   
   object          pHostServices,   
   IDebugProperty3 pDebugProperty  
);  
```  
  
#### Parámetros  
 `hwnd`  
 \[in\]  ventana primaria  
  
 `dwID`  
 \[in\]  Identificador de los visores personalizados que admiten más de un tipo.  
  
 `pHostServices`  
 \[in\] Reservado.  Establezca siempre en null.  
  
 `pDebugProperty`  
 \[in\]  Interfaz que se puede utilizar para recuperar el valor que se va a mostrar.  
  
## Valor devuelto  
 Si finaliza correctamente, devuelve `S_OK`; si no devuelve un código de error.  
  
## Comentarios  
 La pantalla es “modal” en que este método creará la ventana necesaria, mostrará el valor, esperará entrada, y se cerrará la ventana, todos antes de volver al llamador.  Esto significa que el método debe controlar todos los aspectos de mostrar el valor de propiedad, para crear una ventana de salida, para a los datos proporcionados por el usuario que espera, a destruir la ventana.  
  
 Para poder modificar el valor del objeto especificado de [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) , puede utilizar el método de [SetValueAsStringWithError](../../../extensibility/debugger/reference/idebugproperty3-setvalueasstringwitherror.md) — si el valor se puede expresar como una cadena.  Si no, es necesario crear una personalizada interfaz\-exclusiva el evaluador de expresiones que implementa este `DisplayValue` método\-en el mismo objeto que implementa la interfaz de `IDebugProperty3` .  Esta interfaz personalizada suministraría métodos para cambiar los datos de un tamaño o una complejidad arbitrario.  
  
## Vea también  
 [IDebugCustomViewer](../../../extensibility/debugger/reference/idebugcustomviewer.md)   
 [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)   
 [SetValueAsStringWithError](../../../extensibility/debugger/reference/idebugproperty3-setvalueasstringwitherror.md)