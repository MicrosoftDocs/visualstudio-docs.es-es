---
title: 'IActiveScriptGarbageCollector:: recolector | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 75f77c49-2190-4d49-a3e0-9dcf847c502b
caps.latest.revision: 3
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0539ed2cb3540cf33ceaaa15827c3ca08c156698
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/18/2019
ms.locfileid: "72573585"
---
# <a name="iactivescriptgarbagecollectorcollectgarbage"></a>IActiveScriptGarbageCollector::CollectGarbage
El host de script activo llama a este método para iniciar la recolección de elementos no utilizados.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
HRESULT CollectGarbage(        SCRIPTGCTYPE scriptgctype    );  
```  
  
#### <a name="parameters"></a>Parámetros  
 `scriptgctype`  
 de La [enumeración scriptgctype (](../../winscript/reference/scriptgctype-enumeration.md) que especifica si se va a realizar la recolección de elementos no utilizados normal o exhaustiva.  
  
## <a name="return-value"></a>Valor devuelto  
 Devuelve un valor HRESULT.  
  
## <a name="see-also"></a>Vea también  
 [IActiveScriptGarbageCollector Interface](../../winscript/reference/iactivescriptgarbagecollector-interface.md)