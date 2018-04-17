---
title: IDebugProperty3::CreateObjectID | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugProperty3::CreateObjectID
helpviewer_keywords:
- IDebugProperty3::CreateObjectID
ms.assetid: f2fa81e7-822f-456e-8729-a96a18eea771
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: df4e45c442745652b3305fd91146bd31ffe79e4b
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="idebugproperty3createobjectid"></a>IDebugProperty3::CreateObjectID
Crea un identificador único para esta propiedad para asegurarse de que es único entre todas las demás propiedades.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
HRESULT CreateObjectID(  
   void  
);  
```  
  
```csharp  
int CreateObjectID();  
```  
  
## <a name="return-value"></a>Valor devuelto  
 Si se realiza correctamente, devuelve `S_OK`; en caso contrario, devuelve un código de error.  
  
## <a name="remarks"></a>Comentarios  
 Este método se llama cuando el Administrador de sesión de depuración quiere asegurarse de que esta propiedad se identifica de forma única entre todas las demás propiedades. El motor de depuración (Alemania) es compatible con este método, a menos que ya forma única se identifican las propiedades de que se ocupa. Si la DE no admite este método, devuelve `E_NOTIMPL`.  
  
 Cualquier identificador único creado con `CreateObjectID` se destruye cuando la [DestroyObjectID](../../../extensibility/debugger/reference/idebugproperty3-destroyobjectid.md) se llama al método; Esto también marca el final de la necesidad de que identifica de forma única esta propiedad.  
  
> [!NOTE]
>  No hay ningún método para recuperar este identificador único, por lo que la DE puede hacer lo que desee para identificadores únicos cuando el `CreateObjectID` se llama al método.  
  
## <a name="see-also"></a>Vea también  
 [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)   
 [DestroyObjectID](../../../extensibility/debugger/reference/idebugproperty3-destroyobjectid.md)