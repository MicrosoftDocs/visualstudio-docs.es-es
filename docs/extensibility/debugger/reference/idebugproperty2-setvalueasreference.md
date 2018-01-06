---
title: IDebugProperty2::SetValueAsReference | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugProperty2::SetValueAsReference
helpviewer_keywords: IDebugProperty2::SetValueAsReference method
ms.assetid: 341b1b89-4ab8-4e1c-abe2-fb955df5c6b0
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 7bd9e42ae6be1cbd5afe1cbe2ae1b06da7f9937f
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
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
 [in] Una matriz de argumentos que se pasarán al establecedor de propiedad de código administrado. Si el establecedor de propiedad no acepta argumentos, o si este [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) objeto no hace referencia a este tipo de establecedor de propiedades, `rgpArgs` debe ser un valor null. Normalmente, este parámetro es un valor null.  
  
 `dwArgCount`  
 [in] El número de argumentos en la `rgpArgs` matriz.  
  
 `pValue`  
 [in] Una referencia, en forma de un [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) objeto, el valor se utiliza para establecer esta propiedad.  
  
 `dwTimeout`  
 [in] ¿Cuánto hay que llevar a cabo para establecer el valor, en milisegundos. Un valor típico es `INFINITE`. Esto afecta a la cantidad de tiempo que puede llevar a cabo cualquier evaluación posibles.  
  
## <a name="return-value"></a>Valor devuelto  
 Si se realiza correctamente, devuelve `S_OK`; en caso contrario devuelve un error de código, normalmente uno de los siguientes:  
  
|Error|Descripción|  
|-----------|-----------------|  
|`E_SETVALUEASREFERENCE_NOTSUPPORTED`|No se permite establecer el valor de una referencia.|  
|`E_SETVALUE_VALUE_CANNOT_BE_SET`|No se puede establecer el valor como esta propiedad hace referencia a un método.|  
|`E_SETVALUE_VALUE_IS_READONLY`|El valor es de solo lectura y no se puede establecer.|  
|`E_NOTIMPL`|No se implementa el método.|  
  
## <a name="see-also"></a>Vea también  
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)   
 [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)