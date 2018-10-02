---
title: IDebugClassField::EnumBaseClasses | Microsoft Docs
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
- IDebugClassField::EnumBaseClasses
helpviewer_keywords:
- IDebugClassField::EnumBaseClasses method
ms.assetid: 78749674-ef75-46d3-a1f4-ff33afd90e32
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 69c300abde0cd540e34ce351573948d3546e2b3d
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47581651"
---
# <a name="idebugclassfieldenumbaseclasses"></a>IDebugClassField::EnumBaseClasses
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [IDebugClassField::EnumBaseClasses](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugclassfield-enumbaseclasses).  
  
Crea un enumerador para las clases base de esta clase.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp#  
HRESULT EnumBaseClasses(   
   IEnumDebugFields** ppEnum  
);  
```  
  
```csharp  
int EnumBaseClasses(  
   out IEnumDebugFields ppEnum  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `ppEnum`  
 [out] Devuelve un [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) objeto que representa la lista de clases bases. Devuelve un valor null si no hay ninguna clase base.  
  
## <a name="return-value"></a>Valor devuelto  
 Si se realiza correctamente, devuelve S_OK, se devuelve S_SH_NO_BASE_CLASSES si no hay ninguna clase base (y el `ppEnum` parámetro se establece en un valor null); en caso contrario, devuelve un código de error.  
  
## <a name="remarks"></a>Comentarios  
 Las clases base en el objeto de enumerador se especifican en orden de la clase base más inmediata (o más derivada) a la clase base más remota. Por ejemplo, con las clases de C++:  
  
```  
class Root { }  
class Level1 : Root { }  
class Level2 : Level1 { }  
class MyClass : Level2 { }  
```  
  
 La enumeración devolvería las clases base en el orden `Level2`, `Level1`, `Root`.  
  
## <a name="see-also"></a>Vea también  
 [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)   
 [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)

