---
title: BP_RES_DATA_FLAGS | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- BP_RES_DATA_FLAGS
helpviewer_keywords:
- BP_RES_DATA_FLAGS enumeration
ms.assetid: d97611e2-def6-45a9-ad7d-eedf2ad4c82b
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 68d1c0705ae7d27bf281f5d65e9385228cd36bc4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "68153345"
---
# <a name="bp_res_data_flags"></a>BP_RES_DATA_FLAGS
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Especifica si el punto de interrupción de datos se está emulando o implementando en el hardware.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp#  
enum enum_BP_RES_DATA_FLAGS {   
   BP_RES_DATA_EMULATED = 0x0001  
};  
typedef DWORD BP_RES_DATA_FLAGS;  
```  
  
```csharp  
public enum enum_BP_RES_DATA_FLAGS {   
   BP_RES_DATA_EMULATED = 0x0001  
};  
```  
  
## <a name="members"></a>Miembros  
 BP_RES_DATA_EMULATED  
 Especifica que se está emulando el punto de interrupción de datos.  
  
## <a name="remarks"></a>Comentarios  
 Se utiliza para el `dwFlags` miembro de la estructura [BP_RESOLUTION_DATA](../../../extensibility/debugger/reference/bp-resolution-data.md) .  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: msdbg. h  
  
 Espacio de nombres: Microsoft. VisualStudio. Debugger. Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Consulte también  
 [Enumeraciones](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [BP_RESOLUTION_DATA](../../../extensibility/debugger/reference/bp-resolution-data.md)
