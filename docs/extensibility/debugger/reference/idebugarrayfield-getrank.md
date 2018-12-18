---
title: IDebugArrayField::GetRank | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugArrayField::GetRank
helpviewer_keywords:
- IDebugArrayField::GetRank method
ms.assetid: 2364b876-5be1-4bab-9b8f-3b6121da35c6
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 6921da02b2df62509dd820795581e3ce6dae92d6
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49846244"
---
# <a name="idebugarrayfieldgetrank"></a>IDebugArrayField::GetRank
Obtiene el rango o el número de dimensiones de la matriz.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
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
 El rango de matriz se corresponde con el número de dimensiones. En C++ y C#, las matrices multidimensionales son en realidad las matrices de matrices y, por tanto, se pueden considerar simplemente una matriz unidimensional (y el `GetRank` método siempre devuelve 1). En [!INCLUDE[vbprvb](../../../code-quality/includes/vbprvb_md.md)], por otro lado, las matrices multidimensionales se tratan de forma diferente y el rango de dicha matriz refleja el número de dimensiones (y el `GetRank` método siempre devuelve el número de dimensiones).  
  
## <a name="see-also"></a>Vea también  
 [IDebugArrayField](../../../extensibility/debugger/reference/idebugarrayfield.md)