---
title: SEEK_START | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- SEEK_START
helpviewer_keywords:
- SEEK_START enumeration
ms.assetid: 55bd8901-626e-428b-a263-23b14417f4c6
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: a10d749022757860c6f7cc620091c2ac10623976
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49905228"
---
# <a name="seekstart"></a>SEEK_START
Especifica la posición desde la que se va a iniciar la búsqueda en una secuencia de desensamblado.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
enum enum_SEEK_START {   
   SEEK_START_BEGIN       = 0x0001,  
   SEEK_START_END         = 0x0002,  
   SEEK_START_CURRENT     = 0x0003,  
   SEEK_START_CODECONTEXT = 0x0004,  
   SEEK_START_CODELOCID   = 0x0005  
};  
typedef DWORD SEEK_START;  
```  
  
```csharp  
public enum enum_SEEK_START {   
   SEEK_START_BEGIN       = 0x0001,  
   SEEK_START_END         = 0x0002,  
   SEEK_START_CURRENT     = 0x0003,  
   SEEK_START_CODECONTEXT = 0x0004,  
   SEEK_START_CODELOCID   = 0x0005  
};  
```  
  
## <a name="members"></a>Miembros  
 SEEK_START_BEGIN  
 Inicia la búsqueda al principio del documento actual.  
  
 SEEK_START_END  
 Inicia la búsqueda al final del documento actual.  
  
 SEEK_START_CURRENT  
 Inicia la búsqueda en la posición actual del documento actual.  
  
 SEEK_START_CODECONTEXT  
 Inicia la búsqueda en el contexto de código especificada del documento actual.  
  
 SEEK_START_CODELOCID  
 Inicia la búsqueda en el identificador de ubicación de código dado. Los identificadores de ubicación de código se obtienen mediante una llamada a [GetCurrentLocation](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcurrentlocation.md).  
  
## <a name="remarks"></a>Comentarios  
 Se pasa como argumento a la [Seek](../../../extensibility/debugger/reference/idebugdisassemblystream2-seek.md) método.  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vea también  
 [Enumeraciones](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [Buscar](../../../extensibility/debugger/reference/idebugdisassemblystream2-seek.md)   
 [GetCurrentLocation](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcurrentlocation.md)