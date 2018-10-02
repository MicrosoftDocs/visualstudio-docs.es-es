---
title: IDebugProperty3::CreateObjectID | Microsoft Docs
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
- IDebugProperty3::CreateObjectID
helpviewer_keywords:
- IDebugProperty3::CreateObjectID
ms.assetid: f2fa81e7-822f-456e-8729-a96a18eea771
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: f5b7ca39a36bafe2ebba838c7f6d03f89e2f8132
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47576521"
---
# <a name="idebugproperty3createobjectid"></a>IDebugProperty3::CreateObjectID
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [IDebugProperty3::CreateObjectID](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugproperty3-createobjectid).  
  
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
 Si es correcto, devuelve `S_OK`; en caso contrario, devuelve un código de error.  
  
## <a name="remarks"></a>Comentarios  
 Este método se llama cuando el Administrador de sesión de depuración desea asegurarse de que esta propiedad se identifica entre todas las demás propiedades. El motor de depuración (DE) es compatible con este método, a menos que ya de forma exclusiva se identifican las propiedades que se ocupa. Si la DE no admite este método, devuelve `E_NOTIMPL`.  
  
 Cualquier identificador creado con `CreateObjectID` se destruye cuando la [DestroyObjectID](../../../extensibility/debugger/reference/idebugproperty3-destroyobjectid.md) se llama al método; Esto también señala el final de la necesidad de forma única que identifica esta propiedad.  
  
> [!NOTE]
>  No hay ningún método para recuperar este identificador único, por lo que puede hacer la DE cualquier valor para los identificadores únicos cuando la `CreateObjectID` se llama al método.  
  
## <a name="see-also"></a>Vea también  
 [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)   
 [DestroyObjectID](../../../extensibility/debugger/reference/idebugproperty3-destroyobjectid.md)

