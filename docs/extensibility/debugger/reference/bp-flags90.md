---
title: BP_FLAGS90 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- BP_FLAGS90 enumeration
ms.assetid: 3e5a06c5-fb30-4b8a-b2d5-4a0570fc80bd
caps.latest.revision: 7
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: MT
ms.sourcegitcommit: 4a36302d80f4bc397128e3838c9abf858a0b5fe8
ms.openlocfilehash: 5e958be77ca266af30556fa8c03c580eea94b903
ms.contentlocale: es-es
ms.lasthandoff: 09/26/2017

---
# <a name="bpflags90"></a>BP_FLAGS90
Enumera los valores válidos para marcas opcionales. Las marcas opcionales pueden utilizarse para especificar información adicional cuando se establece un punto de interrupción. Esta enumeración se extiende el [BP_FLAGS](../../../extensibility/debugger/reference/bp-flags.md) enumeración.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
enum enum_BP_FLAGS90  
{  
   // VS 8.0 values  
   BP90_FLAG_NONE               = 0x0000,  
   BP90_FLAG_MAP_DOCPOSITION    = 0x0001,  
   BP90_FLAG_DONT_STOP          = 0x0002,  
  
   // Values added in VS 9.0  
   BP90_FLAG_TRACEPOINT_CONTINUE = 0x0004,  
};  
typedef DWORD BP_FLAGS90;  
```  
  
```csharp  
public enum enum_BP_FLAGS90  
{  
   // VS 8.0 values  
   BP90_FLAG_NONE                = 0x0000,  
   BP90_FLAG_MAP_DOCPOSITION     = 0x0001,  
   BP90_FLAG_DONT_STOP           = 0x0002,  
  
   // Values added in VS 9.0  
   BP90_FLAG_TRACEPOINT_CONTINUE = 0x0004,  
};  
```  
  
#### <a name="parameters"></a>Parámetros  
 BP90_FLAG_NONE  
 No especifica ninguna marca de punto de interrupción.  
  
 BP90_FLAG_MAP_DOCPOSITION  
 Especifica que el motor de depuración (Alemania) debe asignar el punto de interrupción mediante el uso de la posición del documento. Esto es aplicable únicamente a los puntos de interrupción establecidos en los archivos de origen y orientada a la secuencia de comandos, como las páginas Active Server (ASP).  
  
 BP90_FLAG_DONT_STOP  
 Especifica que el punto de interrupción debe ser procesado por el motor de depuración, pero que el motor de depuración en última instancia no debería detener es decir, un [IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md) no se debe enviar el objeto de evento. Esta marca está diseñada para utilizarse principalmente con los puntos de seguimiento.  
  
 BP90_FLAG_TRACEPOINT_CONTINUE  
 Utiliza el motor de depuración nativo para determinar si se debe borrar el estado de ejecución paso a paso. Difiere de BP90_FLAG_DONT_STOP porque no se ha establecido BP90_FLAG_DONT_STOP si el punto de seguimiento ejecuta una macro.  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: Msdbg90.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vea también  
 [Enumeraciones](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
