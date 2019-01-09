---
title: IActiveScriptGarbageCollector::CollectGarbage | Documentos de Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 75f77c49-2190-4d49-a3e0-9dcf847c502b
caps.latest.revision: 3
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 478a7a39c69e0c2106e3c6cc308f44f8f7aa3201
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/08/2019
ms.locfileid: "54097128"
---
# <a name="iactivescriptgarbagecollectorcollectgarbage"></a>IActiveScriptGarbageCollector::CollectGarbage
El host de Active Script llama a este método para iniciar la recolección de elementos no utilizados.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
HRESULT CollectGarbage(        SCRIPTGCTYPE scriptgctype    );  
```  
  
#### <a name="parameters"></a>Parámetros  
 `scriptgctype`  
 [in] El [SCRIPTGCTYPE (enumeración)](../../winscript/reference/scriptgctype-enumeration.md) que especifica si se debe realizar la recolección normal o exhaustiva.  
  
## <a name="return-value"></a>Valor devuelto  
 Devuelve un valor HRESULT.  
  
## <a name="see-also"></a>Vea también  
 [IActiveScriptGarbageCollector Interface](../../winscript/reference/iactivescriptgarbagecollector-interface.md)