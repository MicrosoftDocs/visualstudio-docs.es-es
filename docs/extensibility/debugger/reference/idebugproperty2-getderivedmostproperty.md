---
title: IDebugProperty2::GetDerivedMostProperty | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugProperty2::GetDerivedMostProperty
helpviewer_keywords: IDebugProperty2::GetDerivedMostProperty
ms.assetid: cc86b461-62d1-4340-8209-c65037fd8b02
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 3ac691b8e1c2d28477eb8c07f760eae8909a9633
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="idebugproperty2getderivedmostproperty"></a>IDebugProperty2::GetDerivedMostProperty
Obtiene la propiedad más derivado de una propiedad.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
HRESULT GetDerivedMostProperty (   
   IDebugProperty2** ppDerivedMost  
);  
```  
  
```csharp  
int GetDerivedMostProperty (   
   out IDebugProperty2 ppDerivedMost  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `ppDerivedMost`  
 [out] Devuelve un [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) objeto que representa la propiedad más derivado.  
  
## <a name="return-value"></a>Valor devuelto  
 Si se realiza correctamente, devuelve `S_OK`; en caso contrario, devuelve el código de error. Devuelve `S_GETDERIVEDMOST_NO_DERIVED_MOST` si no hay ninguna propiedad más derivado para recuperar.  
  
## <a name="remarks"></a>Comentarios  
 Por ejemplo, si esta propiedad describe un objeto que implementa `ClassRoot` pero que es realmente una instancia de `ClassDerived` que se deriva de `ClassRoot`, a continuación, este método devuelve un [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) objeto que describe la `ClassDerived` objeto.  
  
## <a name="see-also"></a>Vea también  
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)