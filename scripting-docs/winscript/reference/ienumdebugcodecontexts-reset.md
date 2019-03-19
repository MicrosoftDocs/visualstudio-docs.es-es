---
title: IEnumDebugCodeContexts::Reset | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IEnumDebugCodeContexts.Reset
apilocation:
- jscript.dll
helpviewer_keywords:
- IEnumDebugCodeContexts::Reset
ms.assetid: b7042fac-9f45-46ee-a024-81fed73b0762
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 756ed93f774419f33bc721429ea3e3bb605577df
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/19/2019
ms.locfileid: "58157586"
---
# <a name="ienumdebugcodecontextsreset"></a>IEnumDebugCodeContexts::Reset
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
 [IEnumDebugCodeContexts (Interfaz)](../../winscript/reference/ienumdebugcodecontexts-interface.md)