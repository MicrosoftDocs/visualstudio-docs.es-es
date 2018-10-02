---
title: IDebugCoreServer2::EnumPorts | Microsoft Docs
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
- IDebugCoreServer2::EnumPorts
helpviewer_keywords:
- IDebugCoreServer2::EnumPorts
ms.assetid: 3d98dfd0-614f-4d68-90c6-8a9b9cab66f1
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 2c2e8825ec6e2c6d6e750b9a941edd95c9b45241
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47580427"
---
# <a name="idebugcoreserver2enumports"></a>IDebugCoreServer2::EnumPorts
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [IDebugCoreServer2::EnumPorts](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugcoreserver2-enumports).  
  
Recupera una lista de todos los puertos disponibles.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp#  
HRESULT EnumPorts(   
   IEnumDebugPorts2** ppEnum  
);  
```  
  
```csharp  
int EnumPorts(   
   out IEnumDebugPorts2 ppEnum  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `ppEnum`  
 [out] Devuelve un [IEnumDebugPorts2](../../../extensibility/debugger/reference/ienumdebugports2.md) objeto que contiene una lista de todos los puertos de todos los proveedores de puertos.  
  
## <a name="return-value"></a>Valor devuelto  
 Si es correcto, devuelve `S_OK`; en caso contrario, devuelve un código de error.  
  
## <a name="see-also"></a>Vea también  
 [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)   
 [IEnumDebugPorts2](../../../extensibility/debugger/reference/ienumdebugports2.md)

