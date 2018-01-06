---
title: IDebugBinder3::GetExceptionObjectAndType | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugBinder3::GetExceptionObjectAndType
helpviewer_keywords: IDebugBinder3::GetExceptionObjectAndType method
ms.assetid: 2a313fe1-4ee1-4f01-af86-382d6c661a8f
caps.latest.revision: "7"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: b698295f3bfff9fb2c16e286b85bf5268bf6e852
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="idebugbinder3getexceptionobjectandtype"></a>IDebugBinder3::GetExceptionObjectAndType
Este método recupera la excepción asociada a un objeto, si lo hay.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
HRESULT GetExceptionObjectAndType(  
   IDebugObject** ppException,  
   IDebugField**  ppField  
);  
```  
  
```csharp  
int GetExceptionObjectAndType(  
   out IDebugObject ppException,  
   out IDebugField  ppField  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `ppException`  
 [out] Devuelve el objeto que representa la excepción.  
  
 `ppField`  
 [out] Devuelve el objeto que representa un campo concreto que puede haber causado la excepción (Esto puede ser un valor null).  
  
## <a name="return-value"></a>Valor devuelto  
 Si se realiza correctamente, devuelve `S_OK`; en caso contrario, devuelve un código de error.  
  
> [!NOTE]
>  Para comprobar si hay una excepción, compruebe el valor devuelto por `ppException`: si es un valor null, entonces ninguna excepción está asociada a este objeto.  
  
## <a name="see-also"></a>Vea también  
 [IDebugBinder3](../../../extensibility/debugger/reference/idebugbinder3.md)