---
title: IDebugProcess2::GetAttachedSessionName | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugProcess2::GetAttachedSessionName
helpviewer_keywords: IDebugProcess2::GetAttachedSessionName
ms.assetid: 7e5e116f-2c0c-4bc8-ad3f-e9fd2318a7e4
caps.latest.revision: "13"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 8ca045a1fee17891fbe053d1d072a4affa41c787
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="idebugprocess2getattachedsessionname"></a>IDebugProcess2::GetAttachedSessionName
Obtiene el nombre de la sesión que este proceso de depuración. Un IDE puede mostrar esta información a un usuario que se depura un proceso determinado en un equipo determinado.  
  
> [!NOTE]
>  Este método está en desuso y siempre debe devolver su implementación `E_NOTIMPL`.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
HRESULT GetAttachedSessionName(  
   BSTR* pbstrSessionName  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pbstrSessionName`  
  
## <a name="return-value"></a>Valor devuelto  
 Este método siempre debe devolver `E_NOTIMPL`.  
  
## <a name="see-also"></a>Vea también  
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)