---
title: IDebugAlias2::GetAppDomainId | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- GetAppDomainId
- IDebugAlias2::GetAppDomainId
ms.assetid: 23581aaa-5a53-4859-b264-eca49fc44bcd
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 03d0ebeeddfd212b4ad99b8f1686c4f9d64141d3
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53900267"
---
# <a name="idebugalias2getappdomainid"></a>IDebugAlias2::GetAppDomainId
Recupera el identificador del dominio de aplicación.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
HRESULT GetAppDomainId (  
   ULONG32* pappDomainId  
);  
```  
  
```csharp  
int GetAppDomainId (  
   out uint pappDomainId  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pappDomainId`  
 [out] Devuelve el identificador de dominio de aplicación.  
  
## <a name="return-value"></a>Valor devuelto  
 Si es correcto, devuelve `S_OK`; en caso contrario, devuelve un código de error.  
  
## <a name="remarks"></a>Comentarios  
 Se crea un nuevo dominio de aplicación y de los cambios de identificador de dominio de aplicación cada vez que se reinicie la aplicación.  
  
## <a name="see-also"></a>Vea también  
 [IDebugAlias2](../../../extensibility/debugger/reference/idebugalias2.md)