---
title: APPLICATION_NODE_EVENT_FILTER (enumeración) | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- APPLICATION_NODE_EVENT_FILTER Constants
ms.assetid: dccb2cf7-0598-46f8-b3eb-16b752815e96
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a5112f52e9d48417cfd63a514d22a034168c1aea
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/19/2019
ms.locfileid: "58152121"
---
# <a name="applicationnodeeventfilter-enumeration"></a>APPLICATION_NODE_EVENT_FILTER (Enumeración)
Especifica los tipos de nodos que se van a excluir al filtrar los documentos de código. Utilizado en [IDebugApplicationNode100::GetExcludedDocuments](../../winscript/reference/idebugapplicationnode100-getexcludeddocuments.md) y [IDebugApplicationNode100::SetFilterForEventSink](../../winscript/reference/idebugapplicationnode100-setfilterforeventsink.md)  
  
> [!IMPORTANT]
>  Estas constantes se implementan mediante PDM v10.0 y versiones posteriores. Se encuentra en activdbg100.h.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
typedef enum tagAPPLICATION_NODE_EVENT_FILTER {    FILTER_EXCLUDE_NOTHING = 0,    FILTER_EXCLUDE_ANONYMOUS_CODE = 0x1,    FILTER_EXCLUDE_EVAL_CODE = 0x2} APPLICATION_NODE_EVENT_FILTER;  
```  
  
## <a name="members"></a>Miembros  
  
|Miembro|Valor|Descripción|  
|------------|-----------|-----------------|  
|FILTER_EXCLUDE_NOTHING|0x00000000|Enviar todos los eventos.|  
|FILTER_EXCLUDE_ANONYMOUS_CODE|0x00000001|Excluya los nodos de código anónimo. Estos nodos se usan por el tiempo de ejecución de JScript para `new Function([args,] <code>)'`.|  
|FILTER_EXCLUDE_EVAL_CODE|0x00000002|Excluya los nodos de evaluación del código. Estos nodos se usan el tiempo de ejecución de JScript para admitir eval.|  
  
## <a name="see-also"></a>Vea también  
 [Active Script Debugger (Constantes, Enumeraciones y Estructuras)](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)