---
title: IEnumDebugExpressionContexts::Reset | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IEnumDebugExpressionContexts.Reset
apilocation:
- jscript.dll
helpviewer_keywords:
- IEnumDebugExpressionContexts::Reset
ms.assetid: b471954f-d3b5-4c99-88e1-1de3e3f72c7f
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 88e6a66f560e778297658a63244eb510967101f2
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/19/2019
ms.locfileid: "58148092"
---
# <a name="ienumdebugexpressioncontextsreset"></a>IEnumDebugExpressionContexts::Reset
Restablece una secuencia de enumeración al principio.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
HRESULT Reset();  
```  
  
#### <a name="parameters"></a>Parámetros  
 Este método no toma ningún parámetro.  
  
## <a name="return-value"></a>Valor devuelto  
 El método devuelve un objeto `HRESULT`. Entre los valores posibles se incluyen los que se indican en la tabla siguiente, entre otros.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
  
## <a name="remarks"></a>Comentarios  
 Este método restablece una secuencia de enumeración al principio.  
  
## <a name="see-also"></a>Vea también  
 [IEnumDebugExpressionContexts (Interfaz)](../../winscript/reference/ienumdebugexpressioncontexts-interface.md)