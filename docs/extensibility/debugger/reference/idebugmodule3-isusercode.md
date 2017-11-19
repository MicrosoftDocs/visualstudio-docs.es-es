---
title: IDebugModule3::IsUserCode | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugModule3::IsUserCode
helpviewer_keywords: IDebugModule3::IsUserCode
ms.assetid: 77022946-bb8b-4114-aa81-614df6e54b13
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 9dcade316ef9bd58cc7be2906df3ca3cfa9fa33b
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="idebugmodule3isusercode"></a>IDebugModule3::IsUserCode
Recupera información sobre si el módulo representa el código de usuario o no.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
HRESULT IsUserCode(  
   BOOL* pfUser  
);  
```  
  
```csharp  
int IsUserCode(  
   out int pfUser  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pfUser`  
 [out] Es distinto de cero (`TRUE`) si el módulo representa el código de usuario, es cero (`FALSE`) si no es así.  
  
## <a name="return-value"></a>Valor devuelto  
 Si se realiza correctamente, devuelve `S_OK`; en caso contrario, devuelve el código de error.  
  
## <a name="see-also"></a>Vea también  
 [IDebugModule3](../../../extensibility/debugger/reference/idebugmodule3.md)