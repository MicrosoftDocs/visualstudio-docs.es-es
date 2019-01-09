---
title: IDebugApplication::FIsAutoJitDebugEnabled | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: b06d223d76ed741eef6b379ace6b522248ded2e1
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/08/2019
ms.locfileid: "54090550"
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