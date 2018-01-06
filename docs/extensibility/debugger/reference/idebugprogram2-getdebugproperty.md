---
title: IDebugProgram2::GetDebugProperty | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugProgram2::GetDebugProperty
helpviewer_keywords: IDebugProgram2::GetDebugProperty
ms.assetid: d194224e-f0e6-46ab-85d4-9e2639e28946
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 2263b96f64a72e9c89061d1ca3b7792526a8231b
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="idebugprogram2getdebugproperty"></a>IDebugProgram2::GetDebugProperty
Obtiene las propiedades del programa.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
HRESULT GetDebugProperty(   
   IDebugProperty2** ppProperty  
);  
```  
  
```csharp  
int GetDebugProperty(   
   out IDebugProperty2 ppProperty  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `ppProperty`  
 [out] Devuelve un [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) objeto que representa las propiedades del programa.  
  
## <a name="return-value"></a>Valor devuelto  
 Si se realiza correctamente, devuelve `S_OK`; en caso contrario, devuelve un código de error.  
  
## <a name="remarks"></a>Comentarios  
 Las propiedades devueltas por este método son específicas del programa. Si el programa necesita devolver más de una propiedad, el [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) objeto devuelto por este método es un contenedor de propiedades adicionales y llamar a la [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md) método devuelve una lista de todas las propiedades.  
  
 Un programa puede exponer cualquier número y tipo de propiedades adicionales que se puede describir mediante el `IDebugProperty2` interfaz. Un IDE puede mostrar las propiedades del programa adicionales a través de una interfaz de usuario del explorador de propiedad genérica.  
  
## <a name="see-also"></a>Vea también  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)   
 [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md)