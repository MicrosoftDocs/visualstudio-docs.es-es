---
title: ToggleHUD | Documentos de Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7261e01d-3c72-46ce-9fb3-5f33b2ddb901
caps.latest.revision: 8
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 02b461ac8d80146bc86bf3636a367900fcdb8f39
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/16/2018
ms.locfileid: "51786943"
---
# <a name="togglehud"></a>ToggleHUD
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Alterna el diagnóstico de gráficos *HUD* (visualización) de superposición activado o desactivado.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
void ToggleHUD();  
```  
  
## <a name="remarks"></a>Comentarios  
 El HUD de diagnóstico de gráficos se muestra en la esquina superior izquierda de la aplicación que se ejecuta bajo diagnóstico de gráficos. Muestra información de tiempo de ejecución acerca de la aplicación y captura de información de gráficos y los mensajes que se agregan mediante una llamada a la [AddMessage](../debugger/addmessage.md) función miembro.  
  
 Para alternar el HUD, no tiene que estar capturando activamente información de gráficos, es decir, se puede alternar mediante una instancia de la `VsgDbg` (clase), pero la [Init](../debugger/init.md) función miembro no debe llamarse en primer lugar.



