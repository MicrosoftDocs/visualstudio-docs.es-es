---
title: 'IDebugMethodField:: EnumStaticLocals | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugMethodField::EnumStaticLocals
helpviewer_keywords:
- IDebugMethodField::EnumStaticLocals method
ms.assetid: e0c522c4-f759-4c32-ae87-7abcb573e77d
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 69230ce3f748cca460c08d2d40648523161707d5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "68162580"
---
# <a name="idebugmethodfieldenumstaticlocals"></a>IDebugMethodField::EnumStaticLocals
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Crea un enumerador para las variables locales estáticas del método.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp#  
HRESULT EnumStaticLocals(   
   IEnumDebugFields** ppLocals  
);  
```  
  
```csharp  
int EnumStaticLocals(  
   out IEnumDebugFields ppLocals  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `ppLocals`  
 enuncia Devuelve un objeto [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) que representa la lista de variables locales estáticas. Devuelve un valor NULL si no hay variables locales estáticas.  
  
## <a name="return-value"></a>Valor devuelto  
 Si es correcto, Devuelve S_OK o devuelve S_FALSE si no hay variables locales estáticas. De lo contrario, devuelve un código de error.  
  
## <a name="remarks"></a>Comentarios  
 Cada elemento es un objeto [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) que representa distintos tipos de variables locales estáticas. Llame al método [GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md) en cada objeto para determinar exactamente qué tipo de local estático representa el objeto.  
  
## <a name="see-also"></a>Consulte también  
 [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)   
 [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
