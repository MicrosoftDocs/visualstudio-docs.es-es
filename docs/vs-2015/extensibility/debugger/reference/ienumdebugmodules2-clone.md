---
title: IEnumDebugModules2::Clone | Microsoft Docs
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
- IEnumDebugModules2::Clone
helpviewer_keywords:
- IEnumDebugModules2::Clone
ms.assetid: fd6d3abc-20d9-4f6f-9c8e-5bd29f68d47d
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 9945be48de83673b23cb5f8e22f8911946a14c69
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49863495"
---
# <a name="ienumdebugmodules2clone"></a>IEnumDebugModules2::Clone
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Devuelve una copia de la enumeración actual como un objeto independiente.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp#  
HRESULT Clone(  
   IEnumDebugModules2** ppEnum  
);  
```  
  
```csharp  
int Clone(  
   out IEnumDebugModules2 ppEnum  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `ppEnum`  
 [out] Devuelve una copia de esta enumeración como un objeto independiente.  
  
## <a name="return-value"></a>Valor devuelto  
 Si es correcto, devuelve `S_OK`; en caso contrario, devuelve un código de error.  
  
## <a name="remarks"></a>Comentarios  
 La copia de la enumeración tiene el mismo estado que el original en el momento en que se llama a este método. Sin embargo, los Estados de la copia y el original son independientes y se pueden cambiar de forma individual.  
  
## <a name="see-also"></a>Vea también  
 [IEnumDebugModules2](../../../extensibility/debugger/reference/ienumdebugmodules2.md)

