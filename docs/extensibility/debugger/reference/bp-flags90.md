---
title: BP_FLAGS90 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- BP_FLAGS90 enumeration
ms.assetid: 3e5a06c5-fb30-4b8a-b2d5-4a0570fc80bd
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 9f8153f3fb2419e26f7e7d3a741ae4c79c9272a4
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
ms.locfileid: "31100353"
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