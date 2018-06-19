---
title: IDebugApplicationNode100::QueryIsChildNode | Documentos de Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: ea31bbf4efbe6f47a3d2b7e97e001999fc692d7a
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
ms.locfileid: "24725605"
---
# <a name="idebugapplicationnode100queryischildnode"></a>IDebugApplicationNode100::QueryIsChildNode
Determina si el documento especificado pertenece a uno de los nodos secundarios de este nodo.  
  
> [!IMPORTANT]
>  [IDebugApplicationNode100 (interfaz)](../../winscript/reference/idebugapplicationnode100-interface.md) se implementa mediante PDM v10.0 y versiones posteriores. Se encuentra en activdbg100.h.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
HRESULT QueryIsChildNode(        [in] IDebugDocument* pSearchKey        );  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pSearchKey`  
 La clave de búsqueda.  
  
## <a name="see-also"></a>Vea también  
 [IDebugApplicationNode100 (Interfaz)](../../winscript/reference/idebugapplicationnode100-interface.md)