---
title: "Iactivescriptprofilercallback3:: Setwebworkerid (método) | Documentos de Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 47744746-1276-441e-ab60-2a78f550e8e2
caps.latest.revision: "3"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 426767b8d4d23964d6bfaa7102ee53b550e7ab9b
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptprofilercallback3setwebworkerid-method"></a>IActiveScriptProfilerCallback3::SetWebWorkerId (Método)
Notifica al generador de perfiles sobre el identificador de trabajo que se va a usar para esta sesión de generación de perfiles. Si la función no se está ejecutando en el contexto de la página, no se invoca este método. El valor de `webWorkerId` se incrementa en 1 para cada trabajo, comenzando por 1. Los valores de identificador no pretenden ser estable más allá de una sesión y corresponder solo en el orden en que se crearon los trabajadores.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
HRESULT SetWebWorkerId([in] DWORD webWorkerId);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `webWorkerId`  
 El identificador de trabajo de web.  
  
## <a name="return-value"></a>Valor devuelto  
 Se omite el valor devuelto de este método por el motor de scripting.