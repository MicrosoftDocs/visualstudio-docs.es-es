---
title: IDebugEnumField::GetStringFromValue | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugEnumField::GetStringFromValue
helpviewer_keywords:
- IDebugEnumField::GetStringFromValue method
ms.assetid: 5f95fd0c-fdce-497f-9f54-2ad8749494e9
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: e9c1bd0887c8d154501a87ea9a2227e079bbb083
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49872764"
---
# <a name="idebugenumfieldgetstringfromvalue"></a>IDebugEnumField::GetStringFromValue
Este método obtiene el nombre de la constante de enumeración dada su valor.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
HRESULT GetStringFromValue(  
   ULONGLONG value,  
   BSTR*     pbstrValue  
);  
```  
  
```csharp  
int GetStringFromValue(  
   ulong      value,  
   out string pbstrValue  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `value`  
 [in] El valor para el que se va a obtener el nombre de la enumeración constante.  
  
 `pbstrValue`  
 [out] Devuelve el nombre de la constante de enumeración.  
  
## <a name="return-value"></a>Valor devuelto  
 Si es correcto, devuelve `S_OK`; en caso contrario, devuelve `S_FALSE` si el valor no tiene asociado un nombre, o devuelve un código de error.  
  
## <a name="remarks"></a>Comentarios  
 Si hay más de un nombre asociado con el mismo valor, se devolverá el nombre definido en la enumeración.  
  
## <a name="see-also"></a>Vea también  
 [IDebugEnumField](../../../extensibility/debugger/reference/idebugenumfield.md)