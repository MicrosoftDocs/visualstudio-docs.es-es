---
title: IDebugMethodField::GetThis | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugMethodField::GetThis
helpviewer_keywords: IDebugMethodField::GetThis method
ms.assetid: cc235bea-e909-4d8c-ab54-936736c803fc
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: af534ee57a68158e3f909ba69a1771a5073320e1
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="idebugmethodfieldgetthis"></a>IDebugMethodField::GetThis
Obtiene el `this` (`Me` en [!INCLUDE[vbprvb](../../../code-quality/includes/vbprvb_md.md)]) puntero del objeto que contiene el método.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
HRESULT GetThis(   
   IDebugClassField** ppClass  
);  
```  
  
```csharp  
int GetThis(  
   out IDebugClassField ppClass  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `ppClass`  
 [out] Devuelve un [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md) objeto que representa el puntero "this".  
  
## <a name="return-value"></a>Valor devuelto  
 Si se realiza correctamente, devuelve S_OK; en caso contrario, devuelve un código de error.  
  
## <a name="remarks"></a>Comentarios  
 En los lenguajes orientados a objetos, normalmente hay un puntero a la instancia actual de una clase implícito. Esto se conoce como `this` en C# / C++ y como `Me` en [!INCLUDE[vbprvb](../../../code-quality/includes/vbprvb_md.md)].  
  
## <a name="see-also"></a>Vea también  
 [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)   
 [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)