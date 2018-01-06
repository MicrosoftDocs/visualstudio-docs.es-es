---
title: BPRESI_FIELDS | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: BPRESI_FIELDS
helpviewer_keywords: BPRESI_FIELDS enumeration
ms.assetid: 99f17b1e-3e67-4f85-89d6-5c6cf45c8008
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 560080231de78d60e3d7c1e56c5b1c46bbfe6155
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="bpresifields"></a>BPRESI_FIELDS
Especifica la información que se va a recuperar sobre la resolución correcta de un punto de interrupción.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
enum enum_BPRESI_FIELDS {   
   BPRESI_BPRESLOCATION = 0x0001,  
   BPRESI_PROGRAM       = 0x0002,  
   BPRESI_THREAD        = 0x0004,  
   BPRESI_ALLFIELDS     = 0xffffffff  
};  
typedef DWORD BPRESI_FIELDS;  
```  
  
```csharp  
public enum enum_BPRESI_FIELDS {   
   BPRESI_BPRESLOCATION = 0x0001,  
   BPRESI_PROGRAM       = 0x0002,  
   BPRESI_THREAD        = 0x0004,  
   BPRESI_ALLFIELDS     = 0xffffffff  
};  
```  
  
## <a name="members"></a>Miembros  
 BPRESI_BPRESLOCATION  
 Inicializar o utilizar el `bpResLocation` campo (ubicación de resolución de punto de interrupción) de la [BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md) estructura.  
  
 BPRESI_PROGRAM  
 Inicializar o utilizar el `pProgram` campo de la `BP_RESOLUTION_INFO` estructura.  
  
 BPRESI_THREAD  
 Inicializar o utilizar el `pThread` campo de la `BP_RESOLUTION_INFO` estructura.  
  
 BPRESI_ALLFIELDS  
 Especifica todos los campos.  
  
## <a name="remarks"></a>Comentarios  
 Pasa a la [GetResolutionInfo](../../../extensibility/debugger/reference/idebugbreakpointresolution2-getresolutioninfo.md) método para indicar qué campos de la [BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md) estructura deben inicializarse.  
  
 Estas marcas también se utilizan para indicar qué campos de la `BP_RESOLUTION_INFO` estructura se usan y válido cuando se devuelve esa estructura.  
  
 Estos valores se pueden combinar con un bit a bit `OR`.  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vea también  
 [Enumeraciones](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md)   
 [GetResolutionInfo](../../../extensibility/debugger/reference/idebugbreakpointresolution2-getresolutioninfo.md)