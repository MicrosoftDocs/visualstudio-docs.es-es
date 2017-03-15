---
title: "EXCEPTION_STATE | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "EXCEPTION_STATE"
helpviewer_keywords: 
  - "Enumeración EXCEPTION_STATE"
ms.assetid: 597f4f4c-9b70-485c-b5dc-3c2e3aecc664
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# EXCEPTION_STATE
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Especifica el estado de la excepción.  
  
## Sintaxis  
  
```cpp#  
enum enum_EXCEPTION_STATE {   
   EXCEPTION_NONE                          = 0x0000,  
   EXCEPTION_STOP_FIRST_CHANCE             = 0x0001,  
   EXCEPTION_STOP_SECOND_CHANCE            = 0x0002,  
   EXCEPTION_STOP_USER_FIRST_CHANCE        = 0x0010,  
   EXCEPTION_STOP_USER_UNCAUGHT            = 0x0020,  
   EXCEPTION_STOP_ALL                      = 0x00FF,  
   EXCEPTION_CANNOT_BE_CONTINUED           = 0x0100,  
  
   // These are for exception types only  
   EXCEPTION_CODE_SUPPORTED                = 0x1000,  
   EXCEPTION_CODE_DISPLAY_IN_HEX           = 0x2000,  
   EXCEPTION_JUST_MY_CODE_SUPPORTED        = 0x4000,  
   EXCEPTION_MANAGED_DEBUG_ASSISTANT       = 0x8000,  
  
   // These are no longer used  
   EXCEPTION_STOP_FIRST_CHANCE_USE_PARENT      = 0x0004,  
   EXCEPTION_STOP_SECOND_CHANCE_USE_PARENT     = 0x0008,  
   EXCEPTION_STOP_USER_FIRST_CHANCE_USE_PARENT = 0x0040,  
   EXCEPTION_STOP_USER_UNCAUGHT_USE_PARENT     = 0x0080,  
};  
typedef DWORD EXCEPTION_STATE;  
```  
  
```c#  
public enum enum_EXCEPTION_STATE {   
   EXCEPTION_NONE                          = 0x0000,  
   EXCEPTION_STOP_FIRST_CHANCE             = 0x0001,  
   EXCEPTION_STOP_SECOND_CHANCE            = 0x0002,  
   EXCEPTION_STOP_USER_FIRST_CHANCE        = 0x0010,  
   EXCEPTION_STOP_USER_UNCAUGHT            = 0x0020,  
   EXCEPTION_STOP_ALL                      = 0x00FF,  
   EXCEPTION_CANNOT_BE_CONTINUED           = 0x0100,  
  
   // These are for exception types only  
   EXCEPTION_CODE_SUPPORTED                = 0x1000,  
   EXCEPTION_CODE_DISPLAY_IN_HEX           = 0x2000,  
   EXCEPTION_JUST_MY_CODE_SUPPORTED        = 0x4000,  
   EXCEPTION_MANAGED_DEBUG_ASSISTANT       = 0x8000,  
  
   // These are no longer used  
   EXCEPTION_STOP_FIRST_CHANCE_USE_PARENT      = 0x0004,  
   EXCEPTION_STOP_SECOND_CHANCE_USE_PARENT     = 0x0008,  
   EXCEPTION_STOP_USER_FIRST_CHANCE_USE_PARENT = 0x0040,  
   EXCEPTION_STOP_USER_UNCAUGHT_USE_PARENT     = 0x0080,  
};  
```  
  
## Members  
 EXCEPTION\_NONE  
 No detiene en la excepción.  
  
 EXCEPTION\_STOP\_FIRST\_CHANCE  
 Delimitador de la primera desencadenamiento de la excepción.  Al describir un evento de excepción, esta marca indica que el evento de excepciones es un evento de primera oportunidad.  
  
 EXCEPTION\_STOP\_SECOND\_CHANCE  
 Delimitador de la segunda desencadenamiento de la excepción.  Al describir un evento de excepción, indica que el evento de excepciones es un evento de segunda oportunidad de la excepción.  
  
 EXCEPTION\_STOP\_USER\_FIRST\_CHANCE  
 Delimitador de la primera desencadenamiento de una excepción en modo usuario.  Al describir un evento de excepción, indica que el evento de excepciones es un evento de excepción de primera oportunidad.  
  
 EXCEPTION\_STOP\_USER\_UNCAUGHT  
 Detenga cuando una excepción en modo usuario no se detecta.  Al describir un evento de excepción, indica que el evento de excepciones es un evento de excepción en modo usuario de no detectada.  
  
 EXCEPTION\_STOP\_ALL  
 Delimitador de cualquier excepción.  No se utiliza para describir un evento de excepción.  
  
 \_BE\_CONTINUED OF EXCEPTION\_CAN NO  
 Al describir un evento de excepción, indica que la excepción no se puede continuar de.  
  
 EXCEPTION\_CODE\_SUPPORTED  
 Indica que la excepción tiene código que lo admite.  Utilizado en mostrar una excepción  
  
 EXCEPTION\_CODE\_DISPLAY\_IN\_HEX  
 Indica que la excepción se debería mostrar en hexadecimal.  Utilizado en mostrar una excepción.  
  
 EXCEPTION\_JUST\_MY\_CODE\_SUPPORTED  
 Indica que la excepción admite JustMyCode.  Utilizado en mostrar una excepción.  
  
 EXCEPTION\_MANAGED\_DEBUG\_ASSISTANT  
 Indica que el depurador de código administrado debe controlar excepciones.  Si no establece, el depurador predeterminado controla las excepciones.  Esto se pasa al método de [SetAllExceptions](../../../extensibility/debugger/reference/idebugengine3-setallexceptions.md) y no se utiliza en la estructura de [EXCEPTION\_INFO](../../../extensibility/debugger/reference/exception-info.md) .  
  
 EXCEPTION\_STOP\_FIRST\_CHANCE\_USE\_PARENT  
 OBSOLETO, NO UTILICE.  
  
 EXCEPTION\_STOP\_SECOND\_CHANCE\_USE\_PARENT  
 OBSOLETO, NO UTILICE.  
  
 EXCEPTION\_STOP\_USER\_FIRST\_CHANCE\_USE\_PARENT  
 OBSOLETO, NO UTILICE.  
  
 EXCEPTION\_STOP\_USER\_SECOND\_CHANCE\_USE\_PARENT  
 OBSOLETO, NO UTILICE.  
  
## Comentarios  
 Utilizado como miembro de `dwState` de la estructura de [EXCEPTION\_INFO](../../../extensibility/debugger/reference/exception-info.md) para indicar el estado de la excepción y qué se puede hacer en él.  
  
 Esta configuración también se pasan al método de [SetAllExceptions](../../../extensibility/debugger/reference/idebugengine3-setallexceptions.md) para establecer el estado de todas las excepciones.  
  
 Estos marcadores pueden combinarse con una operación OR bit a bit.  
  
## Requisitos  
 encabezado: msdbg.h  
  
 espacio de nombres: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Vea también  
 [Enumeraciones](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [EXCEPTION\_INFO](../../../extensibility/debugger/reference/exception-info.md)   
 [SetAllExceptions](../../../extensibility/debugger/reference/idebugengine3-setallexceptions.md)