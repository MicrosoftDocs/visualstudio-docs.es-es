---
title: EXCEPTION_STATE | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- EXCEPTION_STATE
helpviewer_keywords:
- EXCEPTION_STATE enumeration
ms.assetid: 597f4f4c-9b70-485c-b5dc-3c2e3aecc664
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 69c0f1f4f9396d57af1381962e12b0d3201aa3ef
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="exceptionstate"></a>EXCEPTION_STATE
Especifica el estado de excepción.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
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
  
```csharp  
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
  
## <a name="members"></a>Miembros  
 EXCEPTION_NONE  
 No se detendrá en la excepción.  
  
 EXCEPTION_STOP_FIRST_CHANCE  
 Se detiene en la primera activación de excepción. Para describir un evento de excepción, esta marca indica que el evento de excepción es un evento de excepciones de primera oportunidad.  
  
 EXCEPTION_STOP_SECOND_CHANCE  
 Detener en segundo activación de excepción. Para describir un evento de excepción, indica que el evento de excepción es un evento de excepción de segunda oportunidad.  
  
 EXCEPTION_STOP_USER_FIRST_CHANCE  
 Se detiene en la primera activación de una excepción de modo de usuario. Para describir un evento de excepción, indica que el evento de excepción es un evento de excepción de usuario de primera oportunidad.  
  
 EXCEPTION_STOP_USER_UNCAUGHT  
 Detenga la aplicación cuando no se detecta una excepción de modo de usuario. Para describir un evento de excepción, indica que el evento de excepción es un evento de excepción de modo de usuario no detectada.  
  
 EXCEPTION_STOP_ALL  
 Detener en cualquier excepción. No se usan para describir un evento de excepción.  
  
 EXCEPTION_CANNOT_BE_CONTINUED  
 Para describir un evento de excepción, indica que no se puede continuar la excepción de.  
  
 EXCEPTION_CODE_SUPPORTED  
 Indica que la excepción tiene código que lo respalda. Utilizado en la presentación de una excepción  
  
 EXCEPTION_CODE_DISPLAY_IN_HEX  
 Indica que el código de excepción se debe mostrar en formato hexadecimal. Se utilizan para mostrar una excepción.  
  
 EXCEPTION_JUST_MY_CODE_SUPPORTED  
 Indica que el código de excepción admite JustMyCode. Se utilizan para mostrar una excepción.  
  
 EXCEPTION_MANAGED_DEBUG_ASSISTANT  
 Indica que el depurador de código administrado debe controlar las excepciones. Si no es así conjunto, el depurador predeterminado controla las excepciones. Este argumento se pasa a la [SetAllExceptions](../../../extensibility/debugger/reference/idebugengine3-setallexceptions.md) método y no se utiliza en el [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md) estructura.  
  
 EXCEPTION_STOP_FIRST_CHANCE_USE_PARENT  
 OBSOLETA, NO USE.  
  
 EXCEPTION_STOP_SECOND_CHANCE_USE_PARENT  
 OBSOLETA, NO USE.  
  
 EXCEPTION_STOP_USER_FIRST_CHANCE_USE_PARENT  
 OBSOLETA, NO USE.  
  
 EXCEPTION_STOP_USER_SECOND_CHANCE_USE_PARENT  
 OBSOLETA, NO USE.  
  
## <a name="remarks"></a>Comentarios  
 Usar como el `dwState` miembro de la [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md) estructura para indicar el estado de la excepción y qué se puede hacer sobre él.  
  
 Estos valores también se pasan a la [SetAllExceptions](../../../extensibility/debugger/reference/idebugengine3-setallexceptions.md) método para establecer el estado de todas las excepciones.  
  
 Estas marcas se pueden combinar con una operación OR bit a bit.  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vea también  
 [Enumeraciones](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md)   
 [SetAllExceptions](../../../extensibility/debugger/reference/idebugengine3-setallexceptions.md)