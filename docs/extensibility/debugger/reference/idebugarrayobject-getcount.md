---
title: IDebugArrayObject::GetCount | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugArrayObject::GetCount
helpviewer_keywords: IDebugArrayObject::GetCount method
ms.assetid: 7931f3f7-033c-4bf8-8abd-95183952ebb0
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 7c7a860dd1039f5b2e5a2049674ba78a91af7741
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="idebugarrayobjectgetcount"></a>IDebugArrayObject::GetCount
Obtiene el número de elementos de la matriz.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
[C++]  
HRESULT GetCount(   
   DWORD* pdwElements  
);  
```  
  
```  
[C#]  
int GetCount(  
   out uint pdwElements  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pdwElements`  
 [out] Devuelve el recuento.  
  
## <a name="return-value"></a>Valor devuelto  
 Si se realiza correctamente, devuelve S_OK; en caso contrario, devuelve un código de error.  
  
## <a name="remarks"></a>Comentarios  
 Este método ve todos los elementos de un objeto de matriz como una matriz unidimensional, incluso si el objeto de matriz es multidimensional. Por ejemplo, dada la matriz `myarray[3][2][6]`, este método devolverá 36 en el `pdwElements` parámetro. Use la [GetElement](../../../extensibility/debugger/reference/idebugarrayobject-getelement.md) método para recuperar los elementos individuales de uno en uno.  
  
## <a name="see-also"></a>Vea también  
 [IDebugArrayObject](../../../extensibility/debugger/reference/idebugarrayobject.md)