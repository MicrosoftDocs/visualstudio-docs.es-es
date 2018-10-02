---
title: THREADPROPERTY_FIELDS | Documentos de Microsoft
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- THREADPROPERTY_FIELDS
helpviewer_keywords:
- THREADPROPERTY_FIELDS enumeration
ms.assetid: 5b88acb9-03ea-4c29-a788-f0087dccbe23
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 861a7d51b69f72938750a3210c29b8ac560af016
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47568132"
---
# <a name="threadpropertyfields"></a>THREADPROPERTY_FIELDS
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [THREADPROPERTY_FIELDS](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/threadproperty-fields).  
  
Especifica qué información acerca de un subproceso que se va a recuperar.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp#  
enum enum_THREADPROPERTY_FIELDS {   
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
public enum enum_THREADPROPERTY_FIELDS {   
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
 Inicializar o usar el `dwThreadId` campo de la [THREADPROPERTIES](../../../extensibility/debugger/reference/threadproperties.md) estructura.  
  
 TPF_SUSPENDCOUNT  
 Inicializar o usar el `dwSuspendCount` campo de la `THREADPROPERTIE`estructura.  
  
 TPF_STATE  
 Inicializar o usar el `dwThreadState` campo de la `THREADPROPERTIE`estructura.  
  
 TPF_PRIORITY  
 Inicializar o usar el `bstrPriority` campo de la `THREADPROPERTIE`estructura.  
  
 TPF_NAME  
 Inicializar o usar el `bstrName` campo de la `THREADPROPERTIE`estructura.  
  
 TPF_LOCATION  
 Inicializar o usar el `bstrLocation` campo de la `THREADPROPERTIE`estructura.  
  
 TPF_ALLFIELDS  
 Especifica todos los campos.  
  
## <a name="remarks"></a>Comentarios  
 Estos valores se pasan como argumento a la [GetThreadProperties](../../../extensibility/debugger/reference/idebugthread2-getthreadproperties.md) método para indicar qué campos de la [THREADPROPERTIES](../../../extensibility/debugger/reference/threadproperties.md) estructura deben inicializarse.  
  
 Estos valores también se usan en `dwFields` miembro de la `THREADPROPERTIES` estructura para indicar qué campos se usan y válido.  
  
 Estas marcas se pueden combinar con un bit a bit `OR`.  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vea también  
 [Enumeraciones](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [THREADPROPERTIES](../../../extensibility/debugger/reference/threadproperties.md)   
 [GetThreadProperties](../../../extensibility/debugger/reference/idebugthread2-getthreadproperties.md)

