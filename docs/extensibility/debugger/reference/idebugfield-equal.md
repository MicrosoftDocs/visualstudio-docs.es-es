---
title: IDebugField::Equal | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugField::Equal
helpviewer_keywords:
- IDebugField::Equal method
ms.assetid: 75369fe6-ddd3-497d-80d1-2488e6100e9f
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: b2d195c28123cc786c9a5a97add98b7f67d499b7
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
ms.locfileid: "31121881"
---
# <a name="idebugfieldequal"></a>IDebugField::Equal
Este método compara este campo con el campo especificado para la igualdad.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
HRESULT Equal(   
   IDebugField* pField  
);  
```  
  
```csharp  
int Equal(  
   IDebugField pField  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pField`  
 [in] El campo para comparar a este.  
  
## <a name="return-value"></a>Valor devuelto  
 Si los campos son iguales, devuelve `S_OK`. Si los campos son diferentes, devuelve `S_FALSE.` en caso contrario, devuelve un código de error.  
  
## <a name="see-also"></a>Vea también  
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)