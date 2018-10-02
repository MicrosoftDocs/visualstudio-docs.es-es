---
title: ToggleHUD | Documentos de Microsoft
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7261e01d-3c72-46ce-9fb3-5f33b2ddb901
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b224fdbd4dfadc6af29a0491bba5a18089c260b4
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47574199"
---
# <a name="togglehud"></a>ToggleHUD
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [ToggleHUD](https://docs.microsoft.com/visualstudio/debugger/graphics/togglehud).  
  
Alterna el diagnóstico de gráficos *HUD* (visualización) de superposición activado o desactivado.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
void ToggleHUD();  
```  
  
## <a name="remarks"></a>Comentarios  
 El HUD de diagnóstico de gráficos se muestra en la esquina superior izquierda de la aplicación que se ejecuta bajo diagnóstico de gráficos. Muestra información de tiempo de ejecución acerca de la aplicación y captura de información de gráficos y los mensajes que se agregan mediante una llamada a la [AddMessage](../debugger/addmessage.md) función miembro.  
  
 Para alternar el HUD, no tiene que estar capturando activamente información de gráficos, es decir, se puede alternar mediante una instancia de la `VsgDbg` (clase), pero la [Init](../debugger/init.md) función miembro no debe llamarse en primer lugar.



