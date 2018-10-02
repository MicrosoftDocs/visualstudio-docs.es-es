---
title: IDebugObject::IsNullReference | Microsoft Docs
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
- IDebugObject::IsNullReference
helpviewer_keywords:
- IDebugObject::IsNullReference method
ms.assetid: 6dbfcdb0-954f-4486-8fac-7ea8d003e3a9
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 0709033929414554c8d1592922ee0ac8086d376d
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47577980"
---
# <a name="idebugobjectisnullreference"></a>IDebugObject::IsNullReference
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [IDebugObject::IsNullReference](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugobject-isnullreference).  
  
Comprueba si este objeto es una referencia nula.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp#  
HRESULT IsNullReference(   
   BOOL* pfIsNull  
);  
```  
  
```csharp  
int IsNullReference(  
   out int pfIsNull  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pfIsNull`  
 [out] Devuelve cero (`TRUE`) si este objeto es una referencia null; en caso contrario, devuelve cero (`FALSE`).  
  
## <a name="return-value"></a>Valor devuelto  
 Si se realiza correctamente, devuelve S_OK; en caso contrario, devuelve un código de error.  
  
## <a name="remarks"></a>Comentarios  
 Una referencia null significa que un objeto vacío o un objeto que no se ha asignado a.  
  
## <a name="see-also"></a>Vea también  
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)

