---
title: IDebugExpressionEvaluator2::GetService | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- IDebugExpressionEvaluator2::GetService
- GetService
ms.assetid: f8988a9e-9d18-42af-84a7-55f41e9adf63
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: cfde812730a5f9d2fbad3144cf4298472ec2f8c5
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
ms.locfileid: "31110385"
---
# <a name="idebugexpressionevaluator2getservice"></a>IDebugExpressionEvaluator2::GetService
Recupera un objeto de servicio según su identificador único.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
HRESULT GetService (  
   GUID        uid,  
   IUnknown ** ppService  
);  
```  
  
```csharp  
int GetService (  
   Guid       uid,  
   out object ppService  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `uid`  
 [in] Identificador único del servicio que se va a recuperar.  
  
 `ppService`  
 [out] Devuelve un objeto que representa el servicio.  
  
## <a name="return-value"></a>Valor devuelto  
 Si se realiza correctamente, devuelve `S_OK`; en caso contrario, devuelve un código de error.  
  
## <a name="remarks"></a>Comentarios  
 Esto puede ser utilizado por un evaluador de expresiones de terceros para obtener servicios del otro evaluador de expresiones. Por ejemplo, este método puede utilizarse para obtener la interfaz para el servicio del visualizador en el evaluador de expresiones de valor predeterminado. Evaluadores de expresión de terceros están probable que necesite implementar esta interfaz.  
  
## <a name="see-also"></a>Vea también  
 [IDebugExpressionEvaluator2](../../../extensibility/debugger/reference/idebugexpressionevaluator2.md)