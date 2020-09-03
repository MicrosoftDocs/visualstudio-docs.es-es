---
title: 'IDebugArrayField:: Getrank (| Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugArrayField::GetRank
helpviewer_keywords:
- IDebugArrayField::GetRank method
ms.assetid: 2364b876-5be1-4bab-9b8f-3b6121da35c6
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 5d0396718482c9ce90527155a3612160612f66d3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "68198731"
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
 enuncia Devuelve el rango.  
  
## <a name="return-value"></a>Valor devuelto  
 Si se realiza correctamente, Devuelve S_OK; de lo contrario, devuelve un código de error.  
  
## <a name="remarks"></a>Comentarios  
 El rango de una matriz se corresponde con el número de dimensiones. En C++ y C#, las matrices multidimensionales son realmente matrices de matrices y, por tanto, se pueden considerar solo una matriz unidimensional (y el `GetRank` método siempre devuelve 1). Por [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] otro lado, las matrices multidimensionales se tratan de forma diferente y el rango de una matriz de este tipo refleja el número de dimensiones (y el `GetRank` método siempre devuelve el número de dimensiones).  
  
## <a name="see-also"></a>Consulte también  
 [IDebugArrayField](../../../extensibility/debugger/reference/idebugarrayfield.md)
