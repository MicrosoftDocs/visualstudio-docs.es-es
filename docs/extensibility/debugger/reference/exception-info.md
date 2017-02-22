---
title: "EXCEPTION_INFO | Microsoft Docs"
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
  - "EXCEPTION_INFO"
helpviewer_keywords: 
  - "Estructura EXCEPTION_INFO"
ms.assetid: d046957a-b97d-420b-b46b-c67cbaef709e
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# EXCEPTION_INFO
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Describe una excepción o un error en tiempo de ejecución produce el programa que se depura.  
  
## Sintaxis  
  
```cpp#  
typedef struct tagEXCEPTION_INFO {   
   IDebugProgram2* pProgram;  
   BSTR            bstrProgramName;  
   BSTR            bstrExceptionName;  
   DWORD           dwCode;  
   EXCEPTION_STATE dwState;  
   GUID            guidType;  
} EXCEPTION_INFO;  
```  
  
```c#  
public struct EXCEPTION_INFO {   
   public IDebugProgram2 pProgram;  
   public string         bstrProgramName;  
   public string         bstrExceptionName;  
   public uint           dwCode;  
   public uint           dwState;  
   public Guid           guidType;  
};  
```  
  
## Members  
 pProgram  
 El objeto de [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) que representa el programa en la que se ha producido la excepción.  
  
 bstrProgramName  
 El nombre del programa en la que se ha producido la excepción.  
  
 bstrExceptionName  
 Nombre de la excepción.  
  
 dwCode  
 el código de identificación para la excepción o el error en tiempo de ejecución.  
  
 dwState  
 Un valor de enumeración de [EXCEPTION\_STATE](../../../extensibility/debugger/reference/exception-state.md) que define el estado de la excepción.  
  
 guidType  
 El identificador de idioma de GUID, `guidLang` o `guidEng`.  
  
## Comentarios  
 Esta estructura se pasa como parámetro a [SetException](../../../extensibility/debugger/reference/idebugengine2-setexception.md) y métodos de [RemoveSetException](../../../extensibility/debugger/reference/idebugengine2-removesetexception.md) .  Esta estructura también se pasa al método de [GetException](../../../extensibility/debugger/reference/idebugexceptionevent2-getexception.md) que se completará.  
  
## Requisitos  
 encabezado: msdbg.h  
  
 espacio de nombres: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Vea también  
 [Estructuras y uniones](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [EXCEPTION\_STATE](../../../extensibility/debugger/reference/exception-state.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [SetException](../../../extensibility/debugger/reference/idebugengine2-setexception.md)   
 [RemoveSetException](../../../extensibility/debugger/reference/idebugengine2-removesetexception.md)   
 [GetException](../../../extensibility/debugger/reference/idebugexceptionevent2-getexception.md)