---
title: CONTEXT_INFO_FIELDS | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: CONTEXT_INFO_FIELDS
helpviewer_keywords: CONTEXT_INFO_FIELDS enumeration
ms.assetid: ef436bd3-738e-47e8-828c-8febce752439
caps.latest.revision: "13"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: e604dc09215ac98b2c23fe85312e281b306e9961
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="contextinfofields"></a>CONTEXT_INFO_FIELDS
Especifica qué información debe recuperar sobre un contexto de la memoria.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
enum enum_CONTEXT_INFO_FIELDS {   
   CIF_MODULEURL =       0x00000001,  
   CIF_FUNCTION =        0x00000002,  
   CIF_FUNCTIONOFFSET =  0x00000004,  
   CIF_ADDRESS =         0x00000008,  
   CIF_ADDRESSOFFSET =   0x00000010,  
   CIF_ADDRESSABSOLUTE = 0x00000020,  
   CIF_ALLFIELDS =       0x0000003f  
};  
typedef DWORD CONTEXT_INFO_FIELDS;  
```  
  
```csharp  
public enum enum_CONTEXT_INFO_FIELDS {  
   CIF_MODULEURL =       0x00000001,  
   CIF_FUNCTION =        0x00000002,  
   CIF_FUNCTIONOFFSET =  0x00000004,  
   CIF_ADDRESS =         0x00000008,  
   CIF_ADDRESSOFFSET =   0x00000010,  
   CIF_ADDRESSABSOLUTE = 0x00000020,  
   CIF_ALLFIELDS =       0x0000003f  
};  
```  
  
## <a name="members"></a>Miembros  
 CIF_MODULEURL  
 Inicializar o utilizar el `bstrModuleUrl` campo de la [CONTEXT_INFO](../../../extensibility/debugger/reference/context-info.md) estructura.  
  
 CIF_FUNCTION  
 Inicializar o utilizar el `bstrFunction` campo de la `CONTEXT_INFO` estructura.  
  
 CIF_FUNCTIONOFFSET  
 Inicializar o utilizar el `posFunctionOffset` campo de la `CONTEXT_INFO` estructura.  
  
 CIF_ADDRESS  
 Inicializar o utilizar el `bstrAddress` campo de la `CONTEXT_INFO` estructura.  
  
 CIF_ADDRESSOFFSET  
 Inicializar o utilizar el `bstrAddressOffset` campo de la `CONTEXT_INFO` estructura.  
  
 CIF_ALLFIELDS  
 Inicializar o utilizar todos los campos de la `CONTEXT_INFO` estructura.  
  
## <a name="remarks"></a>Comentarios  
 Estos valores se le pasa un parámetro a la [GetInfo](../../../extensibility/debugger/reference/idebugmemorycontext2-getinfo.md) método para indicar qué campos de la [CONTEXT_INFO](../../../extensibility/debugger/reference/context-info.md) estructura deben inicializarse.  
  
 Estas marcas también se utilizan para indicar qué campos de la `CONTEXT_INFO` estructura se usan y válido cuando se devuelve la estructura.  
  
 Estos valores pueden combinarse con una operación OR bit a bit.  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vea también  
 [Enumeraciones](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [CONTEXT_INFO](../../../extensibility/debugger/reference/context-info.md)   
 [GetInfo](../../../extensibility/debugger/reference/idebugmemorycontext2-getinfo.md)