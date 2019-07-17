---
title: IDebugArrayObject::GetDimensions | Documentos de Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugArrayObject::GetDimensions
helpviewer_keywords:
- IDebugArrayObject::GetDimensions method
ms.assetid: 113e0aff-9028-49d6-b104-9fe7be4772d7
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 09902c60f87cfb92d0f0778fcbd106ade4d8dac4
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "68197789"
---
# <a name="idebugarrayobjectgetdimensions"></a>IDebugArrayObject::GetDimensions
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Obtiene las dimensiones de la matriz.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp#  
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
 [in, out] Una matriz que se rellena con los tamaños de cada dimensión. `dwCount` Especifica el tamaño máximo de la `dwDimensions` matriz.  
  
## <a name="return-value"></a>Valor devuelto  
 Si se realiza correctamente, devuelve S_OK; en caso contrario, devuelve un código de error.  
  
## <a name="remarks"></a>Comentarios  
 Una matriz multidimensional puede tener distintos tamaños de cada dimensión. Por ejemplo, dada la matriz tridimensional `myarray[3][2][6]`, este método devuelve 3, 2 y 6 en el `dwDimensions` parámetro en ese orden.  
  
## <a name="see-also"></a>Vea también  
 [IDebugArrayObject](../../../extensibility/debugger/reference/idebugarrayobject.md)
