---
title: IDebugProperty3::CreateObjectID | Microsoft Docs
ms.date: 11/04/2016
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
ms.openlocfilehash: b6fab6a75885dba8ddfd952ec3680e2c44b87312
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53855827"
---
# <a name="idebugproperty3createobjectid"></a>IDebugProperty3::CreateObjectID
Crea un identificador único para esta propiedad para asegurarse de que es único entre todas las demás propiedades.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
HRESULT CreateObjectID(  
   void  
);  
```  
  
```csharp  
int CreateObjectID();  
```  
  
## <a name="return-value"></a>Valor devuelto  
 Si es correcto, devuelve `S_OK`; en caso contrario, devuelve un código de error.  
  
## <a name="remarks"></a>Comentarios  
 Este método se llama cuando el Administrador de sesión de depuración desea asegurarse de que esta propiedad se identifica entre todas las demás propiedades. El motor de depuración (DE) es compatible con este método, a menos que ya de forma exclusiva se identifican las propiedades que se ocupa. Si la DE no admite este método, devuelve `E_NOTIMPL`.  
  
 Cualquier identificador creado con `CreateObjectID` se destruye cuando la [DestroyObjectID](../../../extensibility/debugger/reference/idebugproperty3-destroyobjectid.md) se llama al método; Esto también señala el final de la necesidad de forma única que identifica esta propiedad.  
  
> [!NOTE]
>  No hay ningún método para recuperar este identificador único, por lo que puede hacer la DE cualquier valor para los identificadores únicos cuando la `CreateObjectID` se llama al método.  
  
## <a name="see-also"></a>Vea también  
 [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)   
 [DestroyObjectID](../../../extensibility/debugger/reference/idebugproperty3-destroyobjectid.md)