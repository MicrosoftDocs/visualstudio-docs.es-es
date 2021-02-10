---
title: AddMessage | Microsoft Docs
description: Use el método AddMessage de la clase VsgDbg para agregar un mensaje personalizado a la pantalla de visualización frontal (HUD) de diagnóstico de gráficos.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 102a0404-a00c-4566-93f3-01bc8df63280
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: d9d51e4415d9707b2df4bb0912290d4f5aa7825f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99874644"
---
# <a name="addmessage"></a>AddMessage
Agrega un mensaje personalizado al *HUD* (pantalla de visualización frontal) de diagnóstico de gráficos.

## <a name="syntax"></a>Sintaxis

```C++
void AddMessage(
  wchar_t const * szMessage
);
```

#### <a name="parameters"></a>Parámetros
 `szMessage` Mensaje que se va a agregar al HUD.

## <a name="remarks"></a>Comentarios
 El HUD de diagnósticos de gráficos se muestra en la esquina superior izquierda de la aplicación que se ejecuta bajo diagnóstico de gráficos. Muestra información en tiempo de ejecución sobre la aplicación y sobre la captura de información de gráficos, y los mensajes que se agregan al llamar a esta función.

 Para agregar un mensaje al HUD, no tiene que estar capturando activamente información de gráficos; es decir, se puede agregar un mensaje mediante una instancia de la clase `VsgDbg`, pero no se debe llamar primero a la función miembro [Init](init.md). Los mensajes solo se muestran en el HUD, no se registran en el archivo de registro de gráficos.