---
title: IDebugBinder::Bind | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugBinder::Bind
helpviewer_keywords: IDebugBinder::Bind method
ms.assetid: 15a11ad7-0fcc-4e80-ae34-8a7dd7bae3c3
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 83b1697d2f10cc656e4c7daa2599f7754cef9466
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="idebugbinderbind"></a>IDebugBinder::Bind
Este método obtiene el contexto de la memoria o un objeto que contiene el valor actual del símbolo.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
HRESULT Bind(   
   IDebugObject*  pContainer,  
   IDebugField*   pField,  
   IDebugObject** ppObject  
);  
```  
  
```csharp  
int Bind(  
   IDebugObject     pContainer,  
   IDebugField      pField,  
   out IDebugObject ppObject  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pContainer`  
 [in] El [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) que contiene el elemento secundario al que hace referencia `pField`.  
  
 `pField`  
 [in] El [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) que representa el símbolo.  
  
 `ppObject`  
 [out] Devuelve el `IDebugObject` que representa la instancia del símbolo.  
  
## <a name="return-value"></a>Valor devuelto  
 Si se realiza correctamente, devuelve `S_OK`; en caso contrario, devuelve un código de error.  
  
## <a name="see-also"></a>Vea también  
 [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)   
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)