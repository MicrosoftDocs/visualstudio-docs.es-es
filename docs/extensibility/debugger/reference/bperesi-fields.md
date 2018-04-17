---
title: BPERESI_FIELDS | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- BPERESI_FIELDS
helpviewer_keywords:
- BPERESI_FIELDS enumeration
ms.assetid: dd7dd89c-1043-46a1-a929-099cc039c344
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 2280740766e20a048f57e58590cc529d98b85264
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="bperesifields"></a>BPERESI_FIELDS
Especifica la información que se va a recuperar sobre una resolución de errores de un punto de interrupción.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
enum enum_BPERESI_FIELDS {   
   PERESI_BPRESLOCATION = 0x0001,  
   BPERESI_PROGRAM      = 0x0002,  
   BPERESI_THREAD       = 0x0004,  
   BPERESI_MESSAGE      = 0x0008,  
   BPERESI_TYPE         = 0x0010,  
   BPERESI_ALLFIELDS    = 0xffffffff  
};  
typedef DWORD BPERESI_FIELDS;  
```  
  
```csharp  
public enum enum_BPERESI_FIELDS {   
   PERESI_BPRESLOCATION = 0x0001,  
   BPERESI_PROGRAM      = 0x0002,  
   BPERESI_THREAD       = 0x0004,  
   BPERESI_MESSAGE      = 0x0008,  
   BPERESI_TYPE         = 0x0010,  
   BPERESI_ALLFIELDS    = 0xffffffff  
};  
```  
  
## <a name="members"></a>Miembros  
 PERESI_BPRESLOCATION  
 Inicializar o utilizar el `bpResLocation` campo (ubicación de resolución de punto de interrupción) de la [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md) estructura.  
  
 BPERESI_PROGRAM  
 Inicializar o utilizar el `pProgram` campo de la `BP_ERROR_RESOLUTION_INFO` estructura.  
  
 BPERESI_THREAD  
 Inicializar o utilizar el `pThread` campo de la `BP_ERROR_RESOLUTION_INFO` estructura.  
  
 BPERESI_MESSAGE  
 Inicializar o utilizar el `bstrMessage` campo de la `BP_ERROR_RESOLUTION_INFO` estructura.  
  
 BPERESI_TYPE  
 Inicializar o utilizar el `dwType` campo (tipo de punto de interrupción) de la `BP_ERROR_RESOLUTION_INFO` estructura.  
  
 BPERESI_ALLFIELDS  
 Inicializar o utilizar todos los campos de la `BP_ERROR_RESOLUTION_INFO` estructura.  
  
## <a name="remarks"></a>Comentarios  
 Pasar como un parámetro a la [GetResolutionInfo](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getresolutioninfo.md) método para indicar qué campos de la [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md) estructura deben inicializarse.  
  
 Estos valores también se utilizan para indicar qué campos de la `BP_ERROR_RESOLUTION_INFO` estructura se usan y válido cuando se devuelve esa estructura.  
  
 Estos valores se pueden combinar con un bit a bit `OR`.  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vea también  
 [Enumeraciones](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md)   
 [GetResolutionInfo](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getresolutioninfo.md)