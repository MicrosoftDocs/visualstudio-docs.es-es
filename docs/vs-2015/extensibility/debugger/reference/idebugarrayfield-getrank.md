---
title: IDebugArrayField::GetRank | Documentos de Microsoft
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
- IDebugArrayField::GetRank
helpviewer_keywords:
- IDebugArrayField::GetRank method
ms.assetid: 2364b876-5be1-4bab-9b8f-3b6121da35c6
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 2ff33ddc6ba41eb43f63ecfb92ad440f205f253a
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/16/2018
ms.locfileid: "51797740"
---
# <a name="idebugarrayfieldgetrank"></a>IDebugArrayField::GetRank
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Obtiene el rango o el número de dimensiones de la matriz.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp#  
HRESULT GetRank(   
   DWORD* pdwRank  
);  
```  
  
```csharp  
int GetRank(  
   out uint pdwRank  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pdwRank`  
 [out] Devuelve el rango.  
  
## <a name="return-value"></a>Valor devuelto  
 Si se realiza correctamente, devuelve S_OK; en caso contrario, devuelve un código de error.  
  
## <a name="remarks"></a>Comentarios  
 El rango de matriz se corresponde con el número de dimensiones. En C++ y C#, las matrices multidimensionales son en realidad las matrices de matrices y, por tanto, se pueden considerar simplemente una matriz unidimensional (y el `GetRank` método siempre devuelve 1). En [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)], por otro lado, las matrices multidimensionales se tratan de forma diferente y el rango de dicha matriz refleja el número de dimensiones (y el `GetRank` método siempre devuelve el número de dimensiones).  
  
## <a name="see-also"></a>Vea también  
 [IDebugArrayField](../../../extensibility/debugger/reference/idebugarrayfield.md)

