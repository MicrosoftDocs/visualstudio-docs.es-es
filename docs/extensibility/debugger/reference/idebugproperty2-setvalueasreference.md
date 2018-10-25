---
title: IDebugProperty2::SetValueAsReference | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugProperty2::SetValueAsReference
helpviewer_keywords:
- IDebugProperty2::SetValueAsReference method
ms.assetid: 341b1b89-4ab8-4e1c-abe2-fb955df5c6b0
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: af0f31ba2bff7effce91232fd7e5cfc6f96afd9f
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49833868"
---
# <a name="idebugproperty2setvalueasreference"></a>IDebugProperty2::SetValueAsReference
Establece el valor de esta propiedad en el valor de la referencia proporcionada.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
HRESULT SetValueAsReference(  
   IDebugReference2** rgpArgs,  
   DWORD              dwArgCount,  
   IDebugReference2*  pValue,  
   DWORD              dwTimeout  
);  
```  
  
```csharp  
int SetValueAsReference(  
   IDebugReference2[] rgpArgs,  
   uint               dwArgCount,  
   IDebugReference2   pValue,  
   uint               dwTimeout  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `rgpArgs`  
 [in] Una matriz de argumentos para pasar al establecedor de propiedad de código administrado. Si el establecedor de propiedad no puede tomar argumentos o si este [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) objeto no hace referencia a este tipo de establecedor de propiedades, `rgpArgs` debe ser un valor null. Normalmente, este parámetro es un valor null.  
  
 `dwArgCount`  
 [in] El número de argumentos de la `rgpArgs` matriz.  
  
 `pValue`  
 [in] Una referencia en forma de un [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) objeto para el valor que se usa para establecer esta propiedad.  
  
 `dwTimeout`  
 [in] Cuánto tiempo debe tomar para establecer el valor, en milisegundos. Un valor típico es `INFINITE`. Esto afecta a la cantidad de tiempo que puede tomar cualquier evaluación posibles.  
  
## <a name="return-value"></a>Valor devuelto  
 Si es correcto, devuelve `S_OK`; en caso contrario, devuelve un error de código, normalmente uno de los siguientes:  
  
|Error|Descripción|  
|-----------|-----------------|  
|`E_SETVALUEASREFERENCE_NOTSUPPORTED`|No se admite establecer el valor de una referencia.|  
|`E_SETVALUE_VALUE_CANNOT_BE_SET`|No se puede establecer el valor como esta propiedad hace referencia a un método.|  
|`E_SETVALUE_VALUE_IS_READONLY`|El valor es de solo lectura y no se puede establecer.|  
|`E_NOTIMPL`|No se implementa el método.|  
  
## <a name="see-also"></a>Vea también  
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)   
 [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)