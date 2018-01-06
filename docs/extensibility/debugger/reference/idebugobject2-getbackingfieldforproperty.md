---
title: IDebugObject2::GetBackingFieldForProperty | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugObject2::GetBackingFieldForProperty
helpviewer_keywords: IDebugObject2::GetBackingFieldForProperty method
ms.assetid: e72c6338-5573-4fad-8075-f3ade3435424
caps.latest.revision: "7"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: f8833e3d2b686e1c350e1094aaa9bdfe925586a7
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="idebugobject2getbackingfieldforproperty"></a>IDebugObject2::GetBackingFieldForProperty
Obtiene el campo o la variable (si existe) que puede realizar una copia la propiedad representada por este objeto.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
HRESULT GetBackingFieldForProperty(  
   IDebugObject2** ppObject  
);  
```  
  
```csharp  
int GetBackingFieldForProperty(  
   out IDebugObject2 ppObject  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `ppObject`  
 [out] Un [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md) objeto que describe el campo de respaldo.  
  
## <a name="return-value"></a>Valor devuelto  
 Si se realiza correctamente, devuelve S_OK; en caso contrario, devuelve un código de error.  
  
## <a name="remarks"></a>Comentarios  
 El [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md) objeto representa una propiedad de clase de código administrado, es decir, un método con una operación get o descriptor de acceso set. Estas propiedades requieren generalmente una variable que contenga el valor manipulado por la propiedad. Esta variable se conoce como el campo de respaldo. Si no hay ningún campo de respaldo para el objeto, asegúrese de que se devuelve un valor null: algunos los llamadores no pueden prestar atención al valor devuelto, pero tendrá un aspecto en su lugar para ver si se devolvió un valor null en `ppObject`.  
  
## <a name="see-also"></a>Vea también  
 [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md)