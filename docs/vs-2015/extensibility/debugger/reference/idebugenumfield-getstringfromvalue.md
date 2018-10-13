---
title: IDebugEnumField::GetStringFromValue | Documentos de Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugEnumField::GetStringFromValue
helpviewer_keywords:
- IDebugEnumField::GetStringFromValue method
ms.assetid: 5f95fd0c-fdce-497f-9f54-2ad8749494e9
caps.latest.revision: 6
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 54348af99dbade2df126106ab4720434e252a210
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49297718"
---
# <a name="idebugenumfieldgetstringfromvalue"></a>IDebugEnumField::GetStringFromValue
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Este método obtiene el nombre de la constante de enumeración dada su valor.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp#  
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

