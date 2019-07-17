---
title: IDebugField::GetTypeInfo | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugField::GetTypeInfo
helpviewer_keywords:
- IDebugField::GetTypeInfo method
ms.assetid: bb5acfa3-04c3-4088-be84-9ff8926cd16f
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: d4229bef0460c7475cda3f81d06b6b24e38ed759
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "68148909"
---
# <a name="idebugfieldgettypeinfo"></a>IDebugField::GetTypeInfo
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Este método obtiene independiente del tipo de información sobre el tipo o el símbolo.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp#  
HRESULT GetTypeInfo(   
   TYPE_INFO* pTypeInfo  
);  
```  
  
```csharp  
int GetTypeInfo(  
   TYPE_INFO[] pTypeInfo  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pTypeInfo`  
 [out] Devuelve información de tipo en proporcionado [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md) estructura.  
  
## <a name="return-value"></a>Valor devuelto  
 Si es correcto, devuelve `S_OK`; en caso contrario, devuelve un código de error.  
  
## <a name="remarks"></a>Comentarios  
 Independiente del tipo de información incluyen, por ejemplo, el dominio de aplicación, el módulo y la clase que contiene el símbolo.  
  
## <a name="see-also"></a>Vea también  
 [GetType](../../../extensibility/debugger/reference/idebugfield-gettype.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)   
 [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md)
