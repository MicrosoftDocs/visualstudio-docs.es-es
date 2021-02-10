---
title: ToggleHUD | Microsoft Docs
description: Use el método ToggleHUD() de VsgDbg para alternar si se muestra la pantalla de visualización frontal (HUD) de diagnóstico de gráficos cuando se ejecuta la aplicación.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 7261e01d-3c72-46ce-9fb3-5f33b2ddb901
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 6cde6549551156f3655f313c23dc66659d2830cf
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99905048"
---
# <a name="togglehud"></a>ToggleHUD
Alterna la activación o desactivación de la superposición del *HUD* (pantalla de visualización frontal) de diagnóstico de gráficos.

## <a name="syntax"></a>Sintaxis

```C++
void ToggleHUD();
```

## <a name="remarks"></a>Comentarios
 El HUD de diagnósticos de gráficos se muestra en la esquina superior izquierda de la aplicación que se ejecuta bajo diagnóstico de gráficos. Muestra información en tiempo de ejecución sobre la aplicación, la captura de información de gráficos y los mensajes que se agregan al llamar a la función miembro [AddMessage](addmessage.md).

 Para alternar el HUD, no tiene que estar capturando activamente información de gráficos; es decir, se puede alternar mediante una instancia de la clase `VsgDbg`, pero no se debe llamar primero a la función miembro [Init](init.md).