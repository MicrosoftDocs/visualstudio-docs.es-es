---
title: IDebugProperty2::SetValueAsReference | Documentos de Microsoft
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
- IDebugProperty2::SetValueAsReference
helpviewer_keywords:
- IDebugProperty2::SetValueAsReference method
ms.assetid: 341b1b89-4ab8-4e1c-abe2-fb955df5c6b0
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: b63e3fae4b3b83501a3fbba1057b7b5d06b9d14b
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49270587"
---
# <a name="idebugproperty2setvalueasreference"></a>IDebugProperty2::SetValueAsReference
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Establece el valor de esta propiedad en el valor de la referencia proporcionada.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp#  
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

