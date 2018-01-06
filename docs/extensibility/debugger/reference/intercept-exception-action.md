---
title: INTERCEPT_EXCEPTION_ACTION | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: INTERCEPT_EXCEPTION_ACTION
helpviewer_keywords: INTERCEPT_EXCEPTION_ACTION enumeration
ms.assetid: e647f1eb-2932-4447-8c78-3b0d706fb972
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: aaa64bf201c0f36be52240926937c063f95bf094
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="interceptexceptionaction"></a>INTERCEPT_EXCEPTION_ACTION
Especifica qué acciones emprender al interceptar excepciones.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
enum enum_INTERCEPT_EXCEPTION_ACTION  
{  
   IEA_INTERCEPT = 0x0001  
}  
typedef DWORD INTERCEPT_EXCEPTION_ACTION;  
```  
  
```csharp  
public enum enum_INTERCEPT_EXCEPTION_ACTION  
{  
   IEA_INTERCEPT = 0x0001  
}  
```  
  
#### <a name="parameters"></a>Parámetros  
 IEA_INTERCEPT  
 Permite interceptar la excepción actual. Este es el único valor admitido en la actualidad y debe especificarse.  
  
## <a name="remarks"></a>Comentarios  
 Estos valores se pasan a la [InterceptCurrentException](../../../extensibility/debugger/reference/idebugstackframe3-interceptcurrentexception.md) método.  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vea también  
 [Enumeraciones](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [InterceptCurrentException](../../../extensibility/debugger/reference/idebugstackframe3-interceptcurrentexception.md)