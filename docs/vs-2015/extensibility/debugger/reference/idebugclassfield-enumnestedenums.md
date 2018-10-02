---
title: IDebugClassField::EnumNestedEnums | Documentos de Microsoft
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
- IDebugClassField::EnumNestedEnums
helpviewer_keywords:
- IDebugClassField::EnumNestedEnums method
ms.assetid: 90fd0cef-9145-4de6-91d4-6c881df39d6e
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 36816b233646460aa5e3a77260dc8f37b2486d9d
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47578832"
---
# <a name="idebugclassfieldenumnestedenums"></a>IDebugClassField::EnumNestedEnums
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [IDebugClassField::EnumNestedEnums](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugclassfield-enumnestedenums).  
  
Crea un enumerador para los enumeradores anidados de esta clase.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp#  
HRESULT EnumNestedEnums(   
   IEnumDebugFields** ppEnum  
);  
```  
  
```csharp  
int EnumNestedEnums(  
   out IEnumDebugFields ppEnum  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `ppEnum`  
 [out] Devuelve un [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) objeto que representa la lista de enumeraciones anidadas. Devuelve un valor null si no hay ningún enumeraciones anidadas.  
  
## <a name="return-value"></a>Valor devuelto  
 Si se realiza correctamente, devuelve S_OK o devuelve S_FALSE si no hay ningún enumeradores anidados. De lo contrario, devuelve un código de error.  
  
## <a name="remarks"></a>Comentarios  
 Cada elemento de la enumeración es un [IDebugEnumField](../../../extensibility/debugger/reference/idebugenumfield.md) objeto que describe una enumeración anidada.  
  
 Una enumeración declarada dentro de una clase se considera una enumeración anidada. Por ejemplo, dado:  
  
```  
class RootClass {  
   enum NestedEnum { EnumValue = 0 }  
};  
```  
  
 El `EnumNestedEnums` método devolvería un [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) objeto que contiene un [IDebugEnumField](../../../extensibility/debugger/reference/idebugenumfield.md) objeto que representa el `NestedEnum` enumeración.  
  
## <a name="see-also"></a>Vea también  
 [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)   
 [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)   
 [IDebugEnumField](../../../extensibility/debugger/reference/idebugenumfield.md)

