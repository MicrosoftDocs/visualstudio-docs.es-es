---
title: IDebugProcessEx2::Attach | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugProcessEx2::Attach
helpviewer_keywords: IDebugProcessEx2::Attach method
ms.assetid: f3334ed7-39bf-4d02-a338-36f567b9b287
caps.latest.revision: "15"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 111895b73ee9685b9608be9812452d04d84cd48c
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="idebugprocessex2attach"></a>IDebugProcessEx2::Attach
Este método le informa que el proceso que una sesión es ahora el proceso de depuración.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
HRESULT Attach(   
   IDebugSession2* pSession  
);  
```  
  
```csharp  
int Attach(  
   IDebugSession2 pSession  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pSession`  
 [in] Un valor que identifica de forma única la sesión adjuntar a este proceso.  
  
## <a name="return-value"></a>Valor devuelto  
 Si se realiza correctamente, devuelve `S_OK`; en caso contrario, devuelve un código de error.  
  
## <a name="remarks"></a>Comentarios  
 La interfaz se pasa en `pSession` debe tratarse como una cookie, un valor que identifica de forma única el Administrador de sesión de depuración adjuntar a este proceso; ninguno de los métodos de la interfaz proporcionada es funcional.  
  
## <a name="see-also"></a>Vea también  
 [IDebugProcessEx2](../../../extensibility/debugger/reference/idebugprocessex2.md)