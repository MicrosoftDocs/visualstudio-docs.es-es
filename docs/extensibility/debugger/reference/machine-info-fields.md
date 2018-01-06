---
title: MACHINE_INFO_FIELDS | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: MACHINE_INFO_FIELDS
helpviewer_keywords: MACHINE_INFO_FIELDS enumeration
ms.assetid: 2d61d206-7d40-4df1-8c88-1b3c9c78821e
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 65d6be8d22955bfd07dfbe40fed723221c60f689
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="machineinfofields"></a>MACHINE_INFO_FIELDS
Especifica qué tipo de información que se va a recuperar de un equipo determinado.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
enum enum_MACHINE_INFO_FIELDS {   
   MCIF_NAME  = 0x00000001,  
   MCIF_FLAGS = 0x00000002,  
   MCIF_ALL   = 0x00000003  
};  
typedef DWORD MACHINE_INFO_FIELDS;  
```  
  
```csharp  
public enum enum_MACHINE_INFO_FIELDS {   
   MCIF_NAME  = 0x00000001,  
   MCIF_FLAGS = 0x00000002,  
   MCIF_ALL   = 0x00000003  
};  
```  
  
## <a name="members"></a>Miembros  
 MCIF_NAME  
 Inicializar o utilizar el `bstrName` campo en la estructura.  
  
 MCIF_FLAGS  
 Inicializar o utilizar el `Flags` campo en la estructura.  
  
 MIF_ALL  
 Inicializar o utilizar todos los campos de la estructura.  
  
## <a name="remarks"></a>Comentarios  
 Estos valores se pasan a la [GetMachineInfo](../../../extensibility/debugger/reference/idebugcoreserver2-getmachineinfo.md) método para indicar qué miembros de la [MACHINE_INFO](../../../extensibility/debugger/reference/machine-info.md) estructura deben inicializarse.  
  
 También se utiliza en el `Fields` miembro de la `MACHINE_INFO` estructura para indicar qué campos se utilizan y válido.  
  
 Estas marcas se pueden combinar con un bit a bit `OR`.  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vea también  
 [Enumeraciones](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [MACHINE_INFO](../../../extensibility/debugger/reference/machine-info.md)   
 [GetMachineInfo](../../../extensibility/debugger/reference/idebugcoreserver2-getmachineinfo.md)