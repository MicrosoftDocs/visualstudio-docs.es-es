---
title: IDebugArrayObject2::HasBaseIndices | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- HasBaseIndices
- IDebugArrayObject2::HasBaseIndices
ms.assetid: 51a5d145-ea53-422c-b5cf-c800cf64b8e6
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: d672ba67a81a4d0454b7b37b038cb46a7a55861b
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49907006"
---
# <a name="idebugarrayobject2hasbaseindices"></a>IDebugArrayObject2::HasBaseIndices
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Determina si la matriz tiene índices de base (límites inferiores) definidos.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp#  
HRESULT HasBaseIndices (  
   BOOL* pfHasBaseIndices  
);  
```  
  
```csharp  
int HasBaseIndices (  
   out bool pfHasBaseIndices  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pfHasBaseIndices`  
 [out] TRUE para especificar que la matriz tiene índices de base (límites inferiores); en caso contrario, FALSE.  
  
## <a name="return-value"></a>Valor devuelto  
 Si es correcto, devuelve `S_OK`; en caso contrario, devuelve un código de error.

