---
title: IDebugArrayObject::GetRank | Documentos de Microsoft
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
- IDebugArrayObject::GetRank
helpviewer_keywords:
- IDebugArrayObject::GetRank method
ms.assetid: 9948551a-e334-4ff6-979c-08dab633b9b6
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: e0100ac37eeebba6d199a87cdbc1da75ea356574
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47578254"
---
# <a name="idebugarrayobjectgetrank"></a>IDebugArrayObject::GetRank
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [IDebugArrayObject::GetRank](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugarrayobject-getrank).  
  
Obtiene el rango de la matriz, es decir, el número de dimensiones.  
  
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
 Use la [GetDimensions](../../../extensibility/debugger/reference/idebugarrayobject-getdimensions.md) método para recuperar el tamaño de cada dimensión del objeto de matriz.  
  
## <a name="see-also"></a>Vea también  
 [IDebugArrayObject](../../../extensibility/debugger/reference/idebugarrayobject.md)

