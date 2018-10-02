---
title: IDebugPointerField::GetDereferencedField | Microsoft Docs
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
- IDebugPointerField::GetDereferencedField
helpviewer_keywords:
- IDebugPointerField::GetDereferencedField method
ms.assetid: 8de988ab-cd79-4287-be72-3c900f2fe407
caps.latest.revision: 8
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 730f869613341b3733bff47a3bdcb066e987f9a5
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47567868"
---
# <a name="idebugpointerfieldgetdereferencedfield"></a>IDebugPointerField::GetDereferencedField
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [IDebugPointerField::GetDereferencedField](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugpointerfield-getdereferencedfield).  
  
Este método devuelve el tipo de objeto al que señala este objeto de puntero.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp#  
HRESULT GetDereferencedField(  
   IDebugField** ppField  
);  
```  
  
```csharp  
int GetDereferencedField(  
   out IDebugField ppField  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `ppField`  
 [out] Devuelve un [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) que describe el tipo de objeto de destino.  
  
## <a name="return-value"></a>Valor devuelto  
 Si es correcto, devuelve `S_OK`; en caso contrario, devuelve un código de error.  
  
## <a name="remarks"></a>Comentarios  
 Por ejemplo, si la [IDebugPointerField](../../../extensibility/debugger/reference/idebugpointerfield.md) objeto apunta a un entero, el [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) ese tipo entero describe el tipo devuelto por este método.  
  
## <a name="see-also"></a>Vea también  
 [IDebugPointerField](../../../extensibility/debugger/reference/idebugpointerfield.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)

