---
title: IDebugArrayField::GetRank | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugArrayField::GetRank
helpviewer_keywords: IDebugArrayField::GetRank method
ms.assetid: 2364b876-5be1-4bab-9b8f-3b6121da35c6
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 786f765e684f720c8c29b91331259e772bd5a007
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
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
 El rango de una matriz se corresponde con el número de dimensiones. En C++ y C#, las matrices multidimensionales son en realidad las matrices de matrices y, por tanto, se puede considerar simplemente una matriz unidimensional (y el `GetRank` método siempre devuelve 1). En [!INCLUDE[vbprvb](../../../code-quality/includes/vbprvb_md.md)], por otro lado, las matrices multidimensionales se tratan de forma diferente y el rango de dicha matriz refleja el número de dimensiones (y el `GetRank` método siempre devuelve el número de dimensiones).  
  
## <a name="see-also"></a>Vea también  
 [IDebugArrayField](../../../extensibility/debugger/reference/idebugarrayfield.md)