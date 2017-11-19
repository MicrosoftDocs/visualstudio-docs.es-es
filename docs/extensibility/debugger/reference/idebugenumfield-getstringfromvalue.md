---
title: IDebugEnumField::GetStringFromValue | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugEnumField::GetStringFromValue
helpviewer_keywords: IDebugEnumField::GetStringFromValue method
ms.assetid: 5f95fd0c-fdce-497f-9f54-2ad8749494e9
caps.latest.revision: "5"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: ed010734ec09af01c4a7abe6f8ceab0a93fdb482
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="idebugenumfieldgetstringfromvalue"></a>IDebugEnumField::GetStringFromValue
Este método obtiene el nombre de la constante de enumeración asigna su valor.  
  
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
 Si se realiza correctamente, devuelve `S_OK`; en caso contrario, devuelve `S_FALSE` si el valor no tiene asociado un nombre, o devuelve un código de error.  
  
## <a name="remarks"></a>Comentarios  
 Si hay más de un nombre asociado con el mismo valor, se devolverá el nombre definido en la enumeración.  
  
## <a name="see-also"></a>Vea también  
 [IDebugEnumField](../../../extensibility/debugger/reference/idebugenumfield.md)