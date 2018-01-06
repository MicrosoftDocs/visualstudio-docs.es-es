---
title: IDebugObject::IsNullReference | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugObject::IsNullReference
helpviewer_keywords: IDebugObject::IsNullReference method
ms.assetid: 6dbfcdb0-954f-4486-8fac-7ea8d003e3a9
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 57952a29750b15cecf61abcea8a4aa02059464df
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="idebugobjectisnullreference"></a>IDebugObject::IsNullReference
Comprueba si este objeto es una referencia nula.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
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
 [out] Devuelve distinto de cero (`TRUE`) si este objeto es una referencia null; en caso contrario, devuelve cero (`FALSE`).  
  
## <a name="return-value"></a>Valor devuelto  
 Si se realiza correctamente, devuelve S_OK; en caso contrario, devuelve un código de error.  
  
## <a name="remarks"></a>Comentarios  
 Una referencia nula significa un objeto vacío o un objeto que no se ha asignado a.  
  
## <a name="see-also"></a>Vea también  
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)