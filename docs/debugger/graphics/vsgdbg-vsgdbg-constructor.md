---
description: Construye una instancia de la clase VsgDbg con o sin preparar el componente de aplicación de diagnóstico de gráficos para capturar y registrar información de gráficos activamente de forma predeterminada, según el parámetro booleano especificado.
title: VsgDbg::VsgDbg (Constructor) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 670651e6-5e79-4845-b0c2-671beb7055a8
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: ae4259b1af1bcb51b05431131db596d2a26da895
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2021
ms.locfileid: "102160451"
---
# <a name="vsgdbgvsgdbg-constructor"></a>VsgDbg::VsgDbg (Constructor)
Construye una instancia de la clase `VsgDbg` con o sin preparar el componente de aplicación de diagnóstico de gráficos para capturar y registrar información de gráficos activamente de forma predeterminada, según el parámetro booleano especificado.

## <a name="syntax"></a>Sintaxis

```C++
VsgDbg(
  bDefaultInit
);
```

#### <a name="parameters"></a>Parámetros
 `bDefaultInit` es `true` para especificar que el componente en la aplicación de diagnóstico de gráficos debe prepararse para capturar y grabar información de gráficos de forma activa; es `false` para especificar que la aplicación no se debe preparar para capturar y grabar información de gráficos de forma activa en este momento.

## <a name="remarks"></a>Comentarios
 Cuando se llama al constructor con `bDefaultInit` establecido en `true`, el nombre de archivo del archivo de registro de gráficos viene determinado por cómo se hayan definido los símbolos de preprocesador `DONT_SAVE_VSGLOG_TO_TEMP` y `VSG_DEFAULT_RUN_FILENAME` antes de incluir `vsgcapture.h` en la aplicación.

 Cuando se llama al constructor con `bDefaultInit` establecido en `false`, el componente de aplicación de diagnóstico de gráficos se puede preparar para capturar y grabar activamente información de gráficos en otro momento llamando a la función `Init`.

## <a name="see-also"></a>Vea también
- [VsgDbg::~VsgDbg (Destructor)](vsgdbg-tilde-vsgdbg-destructor.md)
- [Init](init.md)
- [DONT_SAVE_VSGLOG_TO_TEMP](dont-save-vsglog-to-temp.md)
- [VSG_DEFAULT_RUN_FILENAME](vsg-default-run-filename.md)
