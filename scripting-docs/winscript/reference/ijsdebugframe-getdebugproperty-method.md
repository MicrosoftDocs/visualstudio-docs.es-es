---
title: Getdebugproperty (método) | Documentos de Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IJsDebugFrame.GetDebugProperty
apilocation:
- jscript9diag.dll
ms.assetid: 19bfbe9e-323e-4fe7-ac0e-dc9e87d53219
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b8640eb2bad9633e77797a5ce2348833dbee80d6
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/08/2019
ms.locfileid: "54089913"
---
# <a name="ijsdebugframegetdebugproperty-method"></a>IJsDebugFrame::GetDebugProperty (Método)
Devuelve un explorador de propiedades para este marco de pila.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
HRESULT GetDebugProperty(  
   IJsDebugProperty **ppDebugProperty  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `ppDebugProperty`  
 [out] Objeto que representa el Explorador de propiedades.  
  
## <a name="return-value"></a>Valor devuelto  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** jscript9diag.h  
  
## <a name="see-also"></a>Vea también  
 [IJsDebugFrame (Interfaz)](../../winscript/reference/ijsdebugframe-interface.md)