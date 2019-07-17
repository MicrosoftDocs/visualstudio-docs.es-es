---
title: IDebugAlias::GetObject | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugAlias::GetObject
helpviewer_keywords:
- IDebugAlias::GetObject method
ms.assetid: 97bc3af6-6e55-4940-8a6d-692c61257806
caps.latest.revision: 8
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: bced4d6ea45cc33c3811e42428aa43c334b7b83b
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "68187234"
---
# <a name="idebugaliasgetobject"></a>IDebugAlias::GetObject
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Obtiene el objeto que de este alias.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
HRESULT GetObject(  
   IDebugObject2** ppObject  
);  
```  
  
```csharp  
int GetObject(  
   Out IDebugObject2 ppObject  
)  
```  
  
#### <a name="parameters"></a>Parámetros  
 `ppObject`  
 [out] El [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md) representa este alias.  
  
## <a name="return-value"></a>Valor devuelto  
 Si se realiza correctamente, devuelve S_OK; en caso contrario, devuelve un código de error.  
  
## <a name="see-also"></a>Vea también  
 [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md)   
 [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md)
