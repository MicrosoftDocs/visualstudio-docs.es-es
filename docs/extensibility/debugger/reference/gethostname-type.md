---
title: GETHOSTNAME_TYPE | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- GETHOSTNAME_TYPE
helpviewer_keywords:
- GETHOSTNAME_TYPE enumeration
ms.assetid: 2be92bea-8133-412b-9015-1833baf16e1b
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 1c6bc4f0736950042a62786caac6179f1edffab8
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="gethostnametype"></a>GETHOSTNAME_TYPE
Especifica el tipo de nombre de host.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
enum enum_GETHOSTNAME_TYPE {   
   GHN_FRIENDLY_NAME = 0,  
   GHN_FILE_NAME     = 1  
};  
typedef DWORD GETHOSTNAME_TYPE;  
```  
  
```csharp  
public enum enum_GETHOSTNAME_TYPE {   
   GHN_FRIENDLY_NAME = 0,  
   GHN_FILE_NAME     = 1  
};  
```  
  
## <a name="members"></a>Miembros  
 GHN_FRIENDLY_NAME  
 Especifica un nombre descriptivo del host.  
  
 GHN_FILE_NAME  
 Especifica un nombre de archivo del host.  
  
## <a name="remarks"></a>Comentarios  
 Estos valores se pasan como argumento a la [GetHostName](../../../extensibility/debugger/reference/idebugprogramnode2-gethostname.md) método para recuperar un nombre de host en formatos diferentes.  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vea también  
 [Enumeraciones](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [GetHostName](../../../extensibility/debugger/reference/idebugprogramnode2-gethostname.md)