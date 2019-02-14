---
title: ToggleHUD | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 7261e01d-3c72-46ce-9fb3-5f33b2ddb901
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e49066d4625990119159ea72f59a3a3fe59d581c
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 01/25/2019
ms.locfileid: "54953307"
---
# <a name="togglehud"></a>ToggleHUD
Alterna la activación o desactivación de la superposición del *HUD* (pantalla de visualización frontal) de diagnóstico de gráficos.  
  
## <a name="syntax"></a>Sintaxis  
  
```C++  
void ToggleHUD();  
```  
  
## <a name="remarks"></a>Comentarios  
 El HUD de diagnóstico de gráficos se muestra en la esquina superior izquierda de la aplicación que se ejecuta bajo diagnóstico de gráficos. Muestra información de tiempo de ejecución acerca de la aplicación y captura de información de gráficos y los mensajes que se agregan mediante una llamada a la [AddMessage](addmessage.md) función miembro.  
  
 Para alternar el HUD, no tiene que estar capturando activamente información de gráficos; es decir, se puede alternar mediante una instancia de la clase `VsgDbg`, pero no se debe llamar primero a la función miembro [Init](init.md).