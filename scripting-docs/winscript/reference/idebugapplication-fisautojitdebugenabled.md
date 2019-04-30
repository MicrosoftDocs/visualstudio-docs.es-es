---
title: IDebugApplication::FIsAutoJitDebugEnabled | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugApplication.FIsAutoJitDebugEnabled
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugApplication::FIsAutoJitDebugEnabled
ms.assetid: 0551dd3b-e6eb-442a-8201-418f96fe62df
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f594c5ce48ebd31a265ed438db176c5707d9b079
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62990861"
---
# <a name="idebugapplicationfisautojitdebugenabled"></a>IDebugApplication::FIsAutoJitDebugEnabled
Determina si un depurador de just-in-time (JIT) está registrado en hosts tontos auto-debug.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
BOOL FIsAutoJitDebugEnabled();  
```  
  
#### <a name="parameters"></a>Parámetros  
 Este método no toma ningún parámetro.  
  
## <a name="return-value"></a>Valor devuelto  
 Si el método se ejecuta correctamente y se registra un depurador JIT a hosts tontos auto-debug, el método devuelve `TRUE`. De lo contrario, devuelve `FALSE`.  
  
## <a name="remarks"></a>Comentarios  
 Este método determina si un depurador JIT está registrado con hosts tontos auto-debug.  
  
## <a name="see-also"></a>Vea también  
 [IDebugApplication (Interfaz)](../../winscript/reference/idebugapplication-interface.md)