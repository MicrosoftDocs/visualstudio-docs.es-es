---
title: ERRORRESUMEACTION (enumeración) | Documentos de Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- ERRORRESUMEACTION
apilocation:
- scrobj.dll
helpviewer_keywords:
- ERRORRESUMEACTION enumeration
ms.assetid: a68293c8-056b-439f-83e7-69e4a38f4976
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d92b4b2e00b25a509d29511008876d781c8a577a
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/19/2019
ms.locfileid: "58146206"
---
# <a name="errorresumeaction-enumeration"></a>Enumeración ERRORRESUMEACTION
Describe cómo continuar desde un error de tiempo de ejecución.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
typedef enum tagERRORRESUMEACTION {  
   ERRORRESUMEACTION_ReexecuteErrorStatement,  
   ERRORRESUMEACTION_AbortCallAndReturnErrorToCaller,  
   ERRORRESUMEACTION_SkipErrorStatement,  
} ERRORRESUMEACTION;  
```  
  
## <a name="members"></a>Miembros  
  
|Miembro|Descripción|  
|------------|-----------------|  
|ERRORRESUMEACTION_ReexecuteErrorStatement|Vuelve a ejecutar la instrucción que produjo el error.|  
|ERRORRESUMEACTION_AbortCallAndReturnErrorToCaller|Permite que el motor de lenguaje controlar el error.|  
|ERRORRESUMEACTION_SkipErrorStatement|Reanuda la ejecución en el código que sigue a la instrucción que produjo el error.|  
  
## <a name="see-also"></a>Vea también  
 [Active Script Debugger (Constantes, Enumeraciones y Estructuras)](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)