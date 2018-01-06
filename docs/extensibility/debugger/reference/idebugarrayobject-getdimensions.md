---
title: IDebugArrayObject::GetDimensions | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugArrayObject::GetDimensions
helpviewer_keywords: IDebugArrayObject::GetDimensions method
ms.assetid: 113e0aff-9028-49d6-b104-9fe7be4772d7
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 0e5297019470fe8f3fe314d542013850eab7f1e9
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="idebugarrayobjectgetdimensions"></a>IDebugArrayObject::GetDimensions
Obtiene las dimensiones de la matriz.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
HRESULT GetDimensions(   
   DWORD dwCount,  
   DWORD dwDimensions[]  
);  
```  
  
```csharp  
int GetDimensions(  
   [In] uint    dwCount,   
   [Out] uint[] dwDimensions  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `dwCount`  
 [in] El número de dimensiones que se va a recuperar.  
  
 `dwDimensions`  
 [entrada, salida] Una matriz que se rellena con los tamaños de cada dimensión. `dwCount`Especifica el tamaño máximo de la `dwDimensions` matriz.  
  
## <a name="return-value"></a>Valor devuelto  
 Si se realiza correctamente, devuelve S_OK; en caso contrario, devuelve un código de error.  
  
## <a name="remarks"></a>Comentarios  
 Una matriz multidimensional puede tener distintos tamaños de cada dimensión. Por ejemplo, dada la matriz tridimensional `myarray[3][2][6]`, este método devuelve 3, 2 y 6 en el `dwDimensions` parámetro en ese orden.  
  
## <a name="see-also"></a>Vea también  
 [IDebugArrayObject](../../../extensibility/debugger/reference/idebugarrayobject.md)