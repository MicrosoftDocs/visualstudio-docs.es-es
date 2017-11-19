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
ms.openlocfilehash: b533423da8152dd23df6d32da3361c99ad032b7e
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
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