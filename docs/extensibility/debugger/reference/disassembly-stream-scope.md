---
title: DISASSEMBLY_STREAM_SCOPE | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- DISASSEMBLY_STREAM_SCOPE
helpviewer_keywords:
- DISASSEMBLY_STREAM_SCOPE enumeration
ms.assetid: 43e2b364-cbbe-4755-a7e6-a03f3054c965
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 860d563abd5922ecf0461ed5f03ffa231ba9450f
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49831164"
---
# <a name="disassemblystreamscope"></a>DISASSEMBLY_STREAM_SCOPE
Especifica el ámbito de la secuencia de desensamblado.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
enum enum_DISASSEMBLY_STREAM_SCOPE {   
   DSS_HUGE     = 0x10000000,  
   DSS_FUNCTION = 0x0001,  
   DSS_MODULE   = (DSS_HUGE) | 0x0002,  
   DSS_ALL      = (DSS_HUGE) | 0x0003  
};  
typedef DWORD DISASSEMBLY_STREAM_SCOPE;  
```  
  
```csharp  
public enum enum_DISASSEMBLY_STREAM_SCOPE {   
   DSS_HUGE     = 0x10000000,  
   DSS_FUNCTION = 0x0001,  
   DSS_MODULE   = (DSS_HUGE) | 0x0002,  
   DSS_ALL      = (DSS_HUGE) | 0x0003  
};  
```  
  
## <a name="members"></a>Miembros  
 DSS_HUGE  
 Especifica que el desensamblado en el contexto del código generaría más resultados de un cliente normalmente desea recuperar en una sola llamada.  
  
 DSS_FUNCTION  
 Especifica que se debe desensamblar la función contenida en el contexto del código. Especifica que la secuencia de desensamblado representa una función, cuando devuelve el [GetScope](../../../extensibility/debugger/reference/idebugdisassemblystream2-getscope.md) método.  
  
 DSS_MODULE  
 Cuando devuelve el `IDebugDisassemblyStream2::GetScope` método, especifica que la secuencia de desensamblado representa un módulo.  
  
 DSS_ALL  
 Especifica el desensamblado disponibles para el espacio de direcciones completa.  
  
## <a name="remarks"></a>Comentarios  
 Pasa como argumento a la [GetDisassemblyStream](../../../extensibility/debugger/reference/idebugprogram2-getdisassemblystream.md) método y devuelve el [GetScope](../../../extensibility/debugger/reference/idebugdisassemblystream2-getscope.md) método.  
  
 Estos valores se pueden combinar con un bit a bit `OR`.  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vea también  
 [Enumeraciones](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [GetDisassemblyStream](../../../extensibility/debugger/reference/idebugprogram2-getdisassemblystream.md)   
 [GetScope](../../../extensibility/debugger/reference/idebugdisassemblystream2-getscope.md)