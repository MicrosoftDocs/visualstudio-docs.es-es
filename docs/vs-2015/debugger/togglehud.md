---
title: ToggleHUD | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 7261e01d-3c72-46ce-9fb3-5f33b2ddb901
caps.latest.revision: 8
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 87c2571926b92e59ae03e5e988bbf535474dc6d0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "68144578"
---
# <a name="togglehud"></a>ToggleHUD
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Alterna la activación o desactivación de la superposición del *HUD* (pantalla de visualización frontal) de diagnóstico de gráficos.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
void ToggleHUD();  
```  
  
## <a name="remarks"></a>Comentarios  
 El HUD de diagnósticos de gráficos se muestra en la esquina superior izquierda de la aplicación que se ejecuta bajo diagnóstico de gráficos. Muestra información en tiempo de ejecución sobre la aplicación, la captura de información de gráficos y los mensajes que se agregan al llamar a la función miembro [AddMessage](../debugger/addmessage.md).  
  
 Para alternar el HUD, no tiene que estar capturando activamente información de gráficos; es decir, se puede alternar mediante una instancia de la clase `VsgDbg`, pero no se debe llamar primero a la función miembro [Init](../debugger/init.md).
