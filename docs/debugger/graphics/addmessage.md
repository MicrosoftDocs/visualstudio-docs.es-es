---
title: AddMessage | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 102a0404-a00c-4566-93f3-01bc8df63280
caps.latest.revision: "5"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5b0050f5022b31020879b45e45da48546e5a7caa
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="addmessage"></a>AddMessage
Agrega un mensaje personalizado al diagnóstico de gráficos *HUD* (visualización frontal).  
  
## <a name="syntax"></a>Sintaxis  
  
```C++  
void AddMessage(  
  wchar_t const * szMessage  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `szMessage`  
 Mensaje que se va a agregar al HUD.  
  
## <a name="remarks"></a>Comentarios  
 El HUD de diagnósticos de gráficos se muestra en la esquina superior izquierda de la aplicación que se ejecuta bajo diagnóstico de gráficos. Muestra información en tiempo de ejecución sobre la aplicación y sobre la captura de información de gráficos, y los mensajes que se agregan al llamar a esta función.  
  
 Para agregar un mensaje al HUD, no tiene que ser capturaba activamente información de gráficos, es decir, se puede agregar un mensaje a través de una instancia de la `VsgDbg` (clase), pero la [Init](init.md) hace de la función de miembro para que no se llamará en primer lugar. Los mensajes solo se muestran en el HUD, no se registran en el archivo de registro de gráficos.