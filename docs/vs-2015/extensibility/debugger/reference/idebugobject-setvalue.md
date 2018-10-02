---
title: IDebugObject::SetValue | Documentos de Microsoft
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugObject::SetValue
helpviewer_keywords:
- IDebugObject::SetValue method
ms.assetid: d652e09c-cdc1-4519-8116-d7c743f5679b
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: c47439c69ece059b12ff0d92efd438d73a366915
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47578188"
---
# <a name="idebugobjectsetvalue"></a>IDebugObject::SetValue
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [IDebugObject::SetValue](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugobject-setvalue).  
  
Establece el valor del objeto de una serie de bytes consecutiva.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp#  
HRESULT SetValue(   
   BYTE* pValue,  
   UINT  nSize  
);  
```  
  
```csharp  
int SetValue(  
   byte[] pValue,   
   uint   nSize  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pValue`  
 [in] Una matriz de bytes que representa el nuevo valor.  
  
 `nSize`  
 [in] El tamaño del valor en bytes.  
  
## <a name="return-value"></a>Valor devuelto  
 Si se realiza correctamente, devuelve S_OK; en caso contrario, devuelve un código de error.  
  
## <a name="remarks"></a>Comentarios  
 Los valores de la matriz se copian en esta [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) objeto, reemplazando cualquier valor existente. El tamaño del nuevo valor puede ser mayor o menor que el valor existente. Esto `IDebugObject` no puede ser una referencia nula.  
  
## <a name="see-also"></a>Vea también  
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)   
 [GetValue](../../../extensibility/debugger/reference/idebugobject-getvalue.md)

