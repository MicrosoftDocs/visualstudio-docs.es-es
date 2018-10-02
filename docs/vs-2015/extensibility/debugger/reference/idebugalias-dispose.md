---
title: IDebugAlias::Dispose | Microsoft Docs
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
- IDebugAlias::Dispose
helpviewer_keywords:
- IDebugAlias::Dispose method
ms.assetid: e84909a4-d378-4f48-bf25-2c014c77c8e3
caps.latest.revision: 8
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: c6032612d021e257a9f2c8ef74d35f3bec4a343a
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47574036"
---
# <a name="idebugaliasdispose"></a>IDebugAlias::Dispose
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [IDebugAlias::Dispose](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugalias-dispose).  
  
Marca este alias para su eliminación.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
HRESULT Dispose();  
```  
  
```csharp  
int Dispose();  
```  
  
#### <a name="parameters"></a>Parámetros  
 Ninguno.  
  
## <a name="return-value"></a>Valor devuelto  
 Si se realiza correctamente, devuelve S_OK; en caso contrario, devuelve un código de error.  
  
## <a name="remarks"></a>Comentarios  
 Una vez que se llama a este método, el alias ya no está disponible.  
  
## <a name="see-also"></a>Vea también  
 [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md)

