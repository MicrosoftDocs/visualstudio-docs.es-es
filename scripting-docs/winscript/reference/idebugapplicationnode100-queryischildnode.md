---
title: IDebugApplicationNode100::QueryIsChildNode | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugApplicationNode100::QueryIsChildNode
ms.assetid: 4f36f435-0f34-4f9e-bba3-e75285fd7bbb
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f620a5545c65683eaafd0ac457621f01e6782dff
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/19/2019
ms.locfileid: "58151107"
---
# <a name="idebugapplicationnode100queryischildnode"></a>IDebugApplicationNode100::QueryIsChildNode
Determina si el documento especificado pertenece a uno de los nodos secundarios de este nodo.  
  
> [!IMPORTANT]
>  [IDebugApplicationNode100 (interfaz)](../../winscript/reference/idebugapplicationnode100-interface.md) es implementada por PDM v10.0 y versiones posteriores. Se encuentra en activdbg100.h.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
HRESULT QueryIsChildNode(        [in] IDebugDocument* pSearchKey        );  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pSearchKey`  
 La clave de búsqueda.  
  
## <a name="see-also"></a>Vea también  
 [IDebugApplicationNode100 (Interfaz)](../../winscript/reference/idebugapplicationnode100-interface.md)