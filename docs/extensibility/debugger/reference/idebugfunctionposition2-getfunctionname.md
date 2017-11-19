---
title: IDebugFunctionPosition2::GetFunctionName | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugFunctionPosition2::GetFunctionName
helpviewer_keywords: IDebugFunctionPosition2::GetFunctionName
ms.assetid: eb7a348e-a7f5-4f25-be68-80482d5482a8
caps.latest.revision: "13"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 15329895493359a6054209fa1688a9870b4deb67
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="idebugfunctionposition2getfunctionname"></a>IDebugFunctionPosition2::GetFunctionName
Obtiene el nombre de la función a la que apunta esta posición.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
HRESULT GetFunctionName(   
   BSTR* pbstrFunctionName  
);  
```  
  
```csharp  
int GetFunctionName(  
   out string pbstrFunctionName  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pbstrFunctionName`  
 [out] Devuelve el nombre de la función.  
  
## <a name="return-value"></a>Valor devuelto  
 Si se realiza correctamente, devuelve `S_OK`; en caso contrario, devuelve un código de error.  
  
## <a name="see-also"></a>Vea también  
 [IDebugFunctionPosition2](../../../extensibility/debugger/reference/idebugfunctionposition2.md)