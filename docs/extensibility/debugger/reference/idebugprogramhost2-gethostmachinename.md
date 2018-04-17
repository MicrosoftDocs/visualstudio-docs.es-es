---
title: IDebugProgramHost2::GetHostMachineName | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugProgramHost2::GetHostMachineName
helpviewer_keywords:
- IDebugProgramHost2::GetHostMachineName
ms.assetid: 4677ffe4-aa9b-4450-a63b-74cd3984d956
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 48ad02e3f62900ee0e6b150ed1868b3d04dc9e35
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="idebugprogramhost2gethostmachinename"></a>IDebugProgramHost2::GetHostMachineName
Obtiene el nombre del equipo que está ejecutando el proceso que hospeda este programa.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
HRESULT GetHostMachineName(   
   BSTR* pbstrHostMachineName  
);  
```  
  
```csharp  
int GetHostMachineName(   
   out string pbstrHostMachineName  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pbstrHostMachineName`  
 [out] Devuelve el nombre de la máquina.  
  
## <a name="return-value"></a>Valor devuelto  
 Si se realiza correctamente, devuelve `S_OK`; en caso contrario, devuelve un código de error.  
  
## <a name="see-also"></a>Vea también  
 [IDebugProgramHost2](../../../extensibility/debugger/reference/idebugprogramhost2.md)