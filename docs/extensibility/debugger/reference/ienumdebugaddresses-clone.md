---
title: IEnumDebugAddresses::Clone | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IEnumDebugAddresses::Clone
helpviewer_keywords: IEnumDebugAddresses::Clone method
ms.assetid: 71189a00-34eb-4c71-b96e-8bd6e70c6966
caps.latest.revision: "5"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 89ad14a37966b81235a100d3102e80bddb978782
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="ienumdebugaddressesclone"></a>IEnumDebugAddresses::Clone
Este método devuelve una copia de la enumeración actual como un objeto independiente.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
HRESULT Clone(  
   IEnumDebugAddresses** ppEnum  
);  
```  
  
```csharp  
int Clone(  
   out IEnumDebugAddresses ppEnum  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `ppEnum`  
 [out] Devuelve una copia de esta enumeración como un objeto independiente.  
  
## <a name="property-valuereturn-value"></a>Valor de propiedad y valor devuelto  
 Si se realiza correctamente, devuelve `S_OK`; en caso contrario, devuelve un código de error.  
  
## <a name="remarks"></a>Comentarios  
 La copia de la enumeración tiene el mismo estado que el original en el momento en que se llama a este método. Sin embargo, los Estados de la copia y el original son independientes y se pueden cambiar de forma individual.  
  
## <a name="see-also"></a>Vea también  
 [IEnumDebugAddresses](../../../extensibility/debugger/reference/ienumdebugaddresses.md)