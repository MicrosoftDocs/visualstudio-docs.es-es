---
title: IDebugExceptionEvent2::GetException | Documentos de Microsoft
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
- IDebugExceptionEvent2::GetException
helpviewer_keywords:
- IDebugExceptionEvent2::GetException
ms.assetid: 7c98f41d-322b-4e72-a514-cbd4823eb70d
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: b603f7e5b9b42b387df7922068d690762726b0d0
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47567343"
---
# <a name="idebugexceptionevent2getexception"></a>IDebugExceptionEvent2::GetException
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [IDebugExceptionEvent2::GetException](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugexceptionevent2-getexception).  
  
Obtiene una descripción detallada de la excepción que se desencadena este evento.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp#  
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
 [in, out] Un [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md) estructura que se rellena con la descripción de la excepción.  
  
## <a name="return-value"></a>Valor devuelto  
 Si es correcto, devuelve `S_OK`; en caso contrario, devuelve un código de error.  
  
## <a name="remarks"></a>Comentarios  
 [Solo en C++] El llamador es responsable de liberar cualquier cadena de la [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md) estructura, así como de liberar el [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) objeto de la estructura.  
  
## <a name="see-also"></a>Vea también  
 [IDebugExceptionEvent2](../../../extensibility/debugger/reference/idebugexceptionevent2.md)   
 [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md)   
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)

