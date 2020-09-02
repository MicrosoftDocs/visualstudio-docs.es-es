---
title: THREADPROPERTY_FIELDS | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- THREADPROPERTY_FIELDS
helpviewer_keywords:
- THREADPROPERTY_FIELDS enumeration
ms.assetid: 5b88acb9-03ea-4c29-a788-f0087dccbe23
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: dc0e0f7cae4aed887809c22bda0cd6a9ed50307f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "68204802"
---
# <a name="threadproperty_fields"></a>THREADPROPERTY_FIELDS
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Especifica la información de un subproceso que se va a recuperar.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp#  
enum enum_THREADPROPERTY_FIELDS {   
   TPF_ID           = 0x0001,  
   TPF_SUSPENDCOUNT = 0x0002,  
   TPF_STATE        = 0x0004,  
   TPF_PRIORITY     = 0x0008,  
   TPF_NAME         = 0x0010,  
   TPF_LOCATION     = 0x0020,  
   TPF_ALLFIELDS    = 0xffffffff  
};  
typedef DWORD THREADPROPERTY_FIELDS;  
```  
  
```csharp  
public enum enum_THREADPROPERTY_FIELDS {   
   TPF_ID           = 0x0001,  
   TPF_SUSPENDCOUNT = 0x0002,  
   TPF_STATE        = 0x0004,  
   TPF_PRIORITY     = 0x0008,  
   TPF_NAME         = 0x0010,  
   TPF_LOCATION     = 0x0020,  
   TPF_ALLFIELDS    = 0xffffffff  
};  
```  
  
## <a name="members"></a>Miembros  
 TPF_ID  
 Inicialice/use el `dwThreadId` campo de la estructura [THREADPROPERTIES](../../../extensibility/debugger/reference/threadproperties.md) .  
  
 TPF_SUSPENDCOUNT  
 Inicialice/use el `dwSuspendCount` campo de la `THREADPROPERTIE` estructura S.  
  
 TPF_STATE  
 Inicialice/use el `dwThreadState` campo de la `THREADPROPERTIE` estructura S.  
  
 TPF_PRIORITY  
 Inicialice/use el `bstrPriority` campo de la `THREADPROPERTIE` estructura S.  
  
 TPF_NAME  
 Inicialice/use el `bstrName` campo de la `THREADPROPERTIE` estructura S.  
  
 TPF_LOCATION  
 Inicialice/use el `bstrLocation` campo de la `THREADPROPERTIE` estructura S.  
  
 TPF_ALLFIELDS  
 Especifica todos los campos.  
  
## <a name="remarks"></a>Observaciones  
 Estos valores se pasan como argumento al método [GetThreadProperties](../../../extensibility/debugger/reference/idebugthread2-getthreadproperties.md) para indicar qué campos de la estructura [THREADPROPERTIES](../../../extensibility/debugger/reference/threadproperties.md) se van a inicializar.  
  
 Estos valores también se usan en `dwFields` el miembro de la `THREADPROPERTIES` estructura para indicar qué campos se usan y son válidos.  
  
 Estas marcas se pueden combinar con una operación bit a bit `OR` .  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: msdbg. h  
  
 Espacio de nombres: Microsoft. VisualStudio. Debugger. Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Consulte también  
 [Enumeraciones](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [THREADPROPERTIES](../../../extensibility/debugger/reference/threadproperties.md)   
 [GetThreadProperties](../../../extensibility/debugger/reference/idebugthread2-getthreadproperties.md)
