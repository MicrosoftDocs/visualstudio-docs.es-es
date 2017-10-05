---
title: IDebugExceptionEvent2::GetException | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugExceptionEvent2::GetException
helpviewer_keywords:
- IDebugExceptionEvent2::GetException
ms.assetid: 7c98f41d-322b-4e72-a514-cbd4823eb70d
caps.latest.revision: 10
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
ms.openlocfilehash: 5ae6c92b103ce5d37a24425ec080e651a70dece4
ms.contentlocale: es-es
ms.lasthandoff: 09/26/2017

---
# <a name="idebugexceptionevent2getexception"></a>IDebugExceptionEvent2::GetException
Obtiene una descripción detallada de la excepción que se desencadenó este evento.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
HRESULT GetException(   
   EXCEPTION_INFO* pExceptionInfo  
);  
```  
  
```csharp  
int GetException(   
   EXCEPTION_INFO[] pExceptionInfo  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pExceptionInfo`  
 [entrada, salida] Un [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md) estructura que se rellena con la descripción de la excepción.  
  
## <a name="return-value"></a>Valor devuelto  
 Si se realiza correctamente, devuelve `S_OK`; en caso contrario, devuelve un código de error.  
  
## <a name="remarks"></a>Comentarios  
 [Solo en C++] El llamador es responsable de liberación de las cadenas en el [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md) estructura, así como liberar el [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) objeto en la estructura.  
  
## <a name="see-also"></a>Vea también  
 [IDebugExceptionEvent2](../../../extensibility/debugger/reference/idebugexceptionevent2.md)   
 [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md)   
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
