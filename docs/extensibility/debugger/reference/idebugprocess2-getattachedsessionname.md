---
title: IDebugProcess2::GetAttachedSessionName | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugProcess2::GetAttachedSessionName
helpviewer_keywords:
- IDebugProcess2::GetAttachedSessionName
ms.assetid: 7e5e116f-2c0c-4bc8-ad3f-e9fd2318a7e4
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 34e404fe33858c1db7d9dfb103df7b4e0bb9fb91
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
ms.locfileid: "31123112"
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