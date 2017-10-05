---
title: IDebugCustomAttribute::GetParentField | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugCustomAttribute::GetParentField
helpviewer_keywords:
- IDebugCustomAttribute::GetParentField
ms.assetid: bcdfdf37-bfcf-4988-a7b8-4c731d0af1b0
caps.latest.revision: 9
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: MT
ms.sourcegitcommit: 4a36302d80f4bc397128e3838c9abf858a0b5fe8
ms.openlocfilehash: 1f30a03099c4b8464f64737d706486d07c42a537
ms.contentlocale: es-es
ms.lasthandoff: 09/26/2017

---
# <a name="idebugcustomattributegetparentfield"></a>IDebugCustomAttribute::GetParentField
Obtiene el campo al que está asociado el atributo personalizado.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
HRESULT GetParentField(   
   IDebugField** ppField  
);  
```  
  
```csharp  
int GetParentField(  
   out IDebugField ppField  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `ppField`  
 [out] Devuelve el [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) objeto que representa el campo al que está asociado el atributo personalizado.  
  
## <a name="return-value"></a>Valor devuelto  
 Si se realiza correctamente, devuelve S_OK; en caso contrario, devuelve un código de error.  
  
## <a name="remarks"></a>Comentarios  
 Llame a la [GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md) método en el valor devuelto [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) es el objeto que se va a determinar qué tipo de campo primario.  
  
## <a name="see-also"></a>Vea también  
 [IDebugCustomAttribute](../../../extensibility/debugger/reference/idebugcustomattribute.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
