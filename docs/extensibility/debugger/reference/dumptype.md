---
title: DUMPTYPE | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- DUMPTYPE
helpviewer_keywords:
- DUMPTYPE enumeration
ms.assetid: ea8160db-8732-4056-a1d7-892ef72da71e
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 5e886649a7eaa5f9f99eb2e2bfcc48985f12a5e4
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49949557"
---
# <a name="dumptype"></a>DUMPTYPE
Especifica qué parte del estado de un programa (por ejemplo, los subprocesos en ejecución, marcos de pila y dirección de la instrucción actual) para volcar.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
enum enum_DUMPTYPE {   
   DUMP_MINIDUMP = 0,  
   DUMP_FULLDUMP = 1  
};  
typedef DWORD DUMPTYPE;  
```  
  
```csharp  
public enum enum_DUMPTYPE {   
   DUMP_MINIDUMP = 0,  
   DUMP_FULLDUMP = 1  
};  
```  
  
## <a name="members"></a>Miembros  
 DUMP_MINIDUMP  
 Especifica un volcado de memoria pequeño y compacto.  
  
 DUMP_FULLDUMP  
 Especifica un volcado de memoria grande, completa.  
  
## <a name="remarks"></a>Comentarios  
 Se pasa como argumento a la [WriteDump](../../../extensibility/debugger/reference/idebugprogram2-writedump.md) método.  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vea también  
 [Enumeraciones](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [WriteDump](../../../extensibility/debugger/reference/idebugprogram2-writedump.md)