---
title: IActiveScriptProfilerControl5 (interfaz) | Documentos de Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 7fd0ce34-6ae3-428f-ba90-3e86a8a98ed0
caps.latest.revision: "2"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e0c8b464004337b41280d6d19821f0fb9f1f50a5
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptprofilercontrol5-interface"></a>IActiveScriptProfilerControl5 (Interfaz)
Proporciona un método para enumerar sobre los objetos del montón GC asociados con un motor de scripts.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
interface IActiveScriptProfilerControl5 : IActiveScriptProfilerControl4  
```  
  
## <a name="methods"></a>Métodos  
 [IActiveScriptProfilerControl5::EnumHeap2 (Método)](../../winscript/reference/iactivescriptprofilercontrol5-enumheap2-method.md)  
 Devuelve una interfaz ([IActiveScriptProfilerHeapEnum (interfaz)](../../winscript/reference/iactivescriptprofilerheapenum-interface.md)) que se puede utilizar para recorrer en iteración los objetos de montón del GC en el contexto del motor de script asociado.