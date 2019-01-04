---
title: IDebugExtendedField::GetExtendedKind | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- IDebugExtendedField::GetExtendedKind
- GetExtendedKind
ms.assetid: 20dc1c13-3cc0-4bb4-9c99-fa85587c86c3
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: a88e6df112d2f9396601d485ba1e74be2313c9a8
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53867139"
---
# <a name="idebugextendedfieldgetextendedkind"></a>IDebugExtendedField::GetExtendedKind
Recupera el tipo de campo extendidas especificado.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
HRESULT GetExtendedKind(  
   FIELD_KIND_EX* pdwKind  
);  
```  
  
```csharp  
int GetExtendedKind(  
   ref enum_FIELD_KIND_EX pdwKind  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pdwKind`  
 [in, out] Valor de la [FIELD_KIND_EX](../../../extensibility/debugger/reference/field-kind-ex.md) enumeración que define el tipo de campo.  
  
## <a name="return-value"></a>Valor devuelto  
 Si es correcto, devuelve `S_OK`; en caso contrario, devuelve un código de error.  
  
## <a name="see-also"></a>Vea también  
 [IDebugExtendedField](../../../extensibility/debugger/reference/idebugextendedfield.md)