---
title: IDebugField::GetInfo | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugField::GetInfo
helpviewer_keywords:
- IDebugField::GetInfo method
ms.assetid: 7d508200-89ce-400f-a8ea-f28e7610cb2b
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: ed9a83d11f180467938ba2f9a1e783c73866837e
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49899453"
---
# <a name="idebugfieldgetinfo"></a>IDebugField::GetInfo
Este método obtiene que se puede mostrar información sobre el campo.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
HRESULT GetInfo(   
   FIELD_INFO_FIELDS dwFields,  
   FIELD_INFO* pFieldInfo  
);  
```  
  
```csharp  
int GetInfo(  
   enum_FIELD_INFO_FIELDS dwFields,  
   FIELD_INFO[] pFieldInfo  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `dwFields`  
 [in] Una combinación de [FIELD_INFO_FIELDS](../../../extensibility/debugger/reference/field-info-fields.md) constantes que selecciona la información que se mostrará. Si el campo representa un símbolo, esto suele ser el nombre de símbolo y el tipo.  
  
 `pFieldInfo`  
 [out] Devuelve la información de la proporcionada [FIELD_INFO](../../../extensibility/debugger/reference/field-info.md) estructura.  
  
## <a name="return-value"></a>Valor devuelto  
 Si es correcto, devuelve `S_OK`; en caso contrario, devuelve un código de error.  
  
## <a name="see-also"></a>Vea también  
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)   
 [FIELD_INFO](../../../extensibility/debugger/reference/field-info.md)