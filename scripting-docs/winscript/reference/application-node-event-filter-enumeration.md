---
title: Enumeración APPLICATION_NODE_EVENT_FILTER | Microsoft Docs
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
ms.openlocfilehash: 481e015ec84d833f52220276bffa4ce0163f98ff
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572646"
---
# <a name="application_node_event_filter-enumeration"></a>APPLICATION_NODE_EVENT_FILTER (Enumeración)
Especifica los tipos de nodos que se deben excluir al filtrar documentos de código. Se usa en [idebugapplicationnode100 (:: GetExcludedDocuments](../../winscript/reference/idebugapplicationnode100-getexcludeddocuments.md) y [Idebugapplicationnode100 (:: SetFilterForEventSink](../../winscript/reference/idebugapplicationnode100-setfilterforeventsink.md)  
  
> [!IMPORTANT]
> Estas constantes las implementan PDM v 10.0 y versiones posteriores. Se encuentra en activdbg100.h.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
typedef enum tagAPPLICATION_NODE_EVENT_FILTER {    FILTER_EXCLUDE_NOTHING = 0,    FILTER_EXCLUDE_ANONYMOUS_CODE = 0x1,    FILTER_EXCLUDE_EVAL_CODE = 0x2} APPLICATION_NODE_EVENT_FILTER;  
```  
  
## <a name="members"></a>Miembros  
  
|Miembro|Valor|Descripción|  
|------------|-----------|-----------------|  
|FILTER_EXCLUDE_NOTHING|0x00000000|Enviar todos los eventos.|  
|FILTER_EXCLUDE_ANONYMOUS_CODE|0x00000001|Excluya los nodos de código anónimo. El tiempo de ejecución de JScript usa estos nodos para `new Function([args,] <code>)'`.|  
|FILTER_EXCLUDE_EVAL_CODE|0x00000002|Excluya los nodos de código de evaluación. Estos nodos son usados por el tiempo de ejecución de JScript para la compatibilidad con eval.|  
  
## <a name="see-also"></a>Vea también  
 [Active Script Debugger (Constantes, Enumeraciones y Estructuras)](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)