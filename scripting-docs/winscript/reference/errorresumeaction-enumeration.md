---
title: Enumeración ERRORRESUMEACTION (| Microsoft Docs
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
ms.openlocfilehash: ad9b8598cb027c96f6fb6fad6f3d343e6058cfdb
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575863"
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
|ERRORRESUMEACTION_ReexecuteErrorStatement|Vuelve a ejecutar la instrucción que generó el error.|  
|ERRORRESUMEACTION_AbortCallAndReturnErrorToCaller|Permite que el motor del lenguaje controle el error.|  
|ERRORRESUMEACTION_SkipErrorStatement|Reanuda la ejecución en el código que sigue a la instrucción que generó el error.|  
  
## <a name="see-also"></a>Vea también  
 [Active Script Debugger (Constantes, Enumeraciones y Estructuras)](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)