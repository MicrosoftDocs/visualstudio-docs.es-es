---
title: Procedimiento para especificar el runtime de .NET Framework | Microsoft Docs
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- Profiling Tools, .NET Framework versions
- .NET Framework versions,profililng
ms.assetid: d39f3579-719a-4f47-a97d-5b4232fe4c64
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- dotnet
ms.openlocfilehash: 2eddbe3602386e6a8f5c7e07e796b8c3b047603c
ms.sourcegitcommit: 57d96de120e0574e506dfd80bb7adfbac73f96be
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/24/2020
ms.locfileid: "85331370"
---
# <a name="how-to-specify-the-net-framework-runtime"></a>Procedimiento Especificar el runtime de .NET Framework

Con el lanzamiento de .NET Framework 4, las aplicaciones pueden estar formadas por módulos compilados con versiones diferentes del runtime de .NET Framework. De forma predeterminada, las Herramientas de generación de perfiles de Visual Studio generan perfiles del primer runtime cargado por la aplicación. Puede especificar el runtime del que se deben generar perfiles cuando se inicia una aplicación con el generador de perfiles y al adjuntar el generador de perfiles a una aplicación que ya se está ejecutando.

## <a name="to-specify-the-net-framework-run-time-to-profile-when-starting-an-application-with-the-profiler"></a>Para especificar el runtime de .NET Framework del que generar perfiles al iniciar una aplicación con el generador de perfiles

1. En el **Explorador de rendimiento**, haga clic con el botón derecho en la sesión de rendimiento, haga clic en **Propiedades** y después haga clic en **Avanzadas**.

     El cuadro de lista **Versión de CLR de destino** muestra **Automática** y las versiones del runtime de .NET Framework que están instaladas en el equipo.

2. Realice uno de estos pasos:

    - Haga clic en la versión de CLR de la que desea generar perfiles.

    - Haga clic en **Automático** para generar perfiles de la primera versión que carga la aplicación.

## <a name="to-specify-the-net-framework-run-time-to-profile-when-attaching-the-profiler-to-an-application"></a>Para especificar el runtime de .NET Framework del que generar perfiles al adjuntar el generador de perfiles a una aplicación

1. En el menú **Analizar**, seleccione **Generador de perfiles** y después haga clic en **Asociar/desasociar**.

2. En el cuadro de diálogo **Asociar generador de perfiles al proceso**, haga clic en el proceso del que quiere generar perfiles.

     El cuadro de lista **Versión de CLR de destino** muestra **Automática** y las versiones del runtime de .NET Framework que están instaladas en el equipo.

3. Realice uno de estos pasos:

    - Haga clic en la versión de CLR de la que desea generar perfiles.

    - Haga clic en **Automático** para generar perfiles de la versión que se carga cuando el generador de perfiles se adjunta a la aplicación.
