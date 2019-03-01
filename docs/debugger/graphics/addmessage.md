---
title: AddMessage | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 102a0404-a00c-4566-93f3-01bc8df63280
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 41a71a69c916bf2fff30b2dee8784d5d9997436b
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 02/22/2019
ms.locfileid: "56705575"
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