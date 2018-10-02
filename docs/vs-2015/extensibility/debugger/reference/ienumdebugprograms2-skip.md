---
title: IEnumDebugPrograms2::Skip | Microsoft Docs
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
- IEnumDebugPrograms2::Skip
helpviewer_keywords:
- IEnumDebugPrograms2::Skip
ms.assetid: b283858b-b375-4760-bfec-ab37de89958d
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: fa500bf653fc9cf0356d5eebbd6ea66299766ddc
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47574773"
---
# <a name="ienumdebugprograms2skip"></a>IEnumDebugPrograms2::Skip
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [IEnumDebugPrograms2::Skip](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/ienumdebugprograms2-skip).  
  
Omite el número especificado de elementos.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp#  
HRESULT Skip(  
   ULONG celt  
);  
```  
  
```csharp  
int Skip(  
   uint celt  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `celt`  
 [in] Número de elementos que se van a omitir.  
  
## <a name="return-value"></a>Valor devuelto  
 Si es correcto, devuelve `S_OK`. Devuelve `S_FALSE` si `celt` es mayor que el número de elementos restantes; en caso contrario, devuelve un código de error.  
  
## <a name="remarks"></a>Comentarios  
 Si `celt` especifica un valor mayor que el número de elementos restantes, la enumeración se establece en el extremo y `S_FALSE` se devuelve.  
  
## <a name="see-also"></a>Vea también  
 [IEnumDebugPrograms2](../../../extensibility/debugger/reference/ienumdebugprograms2.md)

