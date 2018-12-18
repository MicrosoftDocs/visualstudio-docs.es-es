---
title: 'Cómo: Especificar runtime de .NET Framework | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- Profiling Tools, .NET Framework versions
- .NET Framework versions,profililng
ms.assetid: d39f3579-719a-4f47-a97d-5b4232fe4c64
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: e85e1c571ecb900d5ce7ffdecf8e85b8c367de5c
ms.sourcegitcommit: ce154aee5b403d5c1c41da42302b896ad3cf8d82
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/07/2018
ms.locfileid: "34844139"
---
# <a name="how-to-specify-the-net-framework-runtime"></a>Cómo: Especificar runtime de .NET Framework

Con el lanzamiento de [!INCLUDE[net_v40_long](../code-quality/includes/net_v40_long_md.md)], las aplicaciones se pueden componer de módulos que se compilaron con versiones diferentes del runtime de [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]. De forma predeterminada, las Herramientas de generación de perfiles de Visual Studio generan perfiles del primer runtime cargado por la aplicación. Puede especificar el runtime del que se deben generar perfiles cuando se inicia una aplicación con el generador de perfiles y al adjuntar el generador de perfiles a una aplicación que ya se está ejecutando.

## <a name="to-specify-the-net-framework-run-time-to-profile-when-starting-an-application-with-the-profiler"></a>Para especificar el runtime de .NET Framework del que generar perfiles al iniciar una aplicación con el generador de perfiles

1. En el **Explorador de rendimiento**, haga clic con el botón derecho en la sesión de rendimiento, haga clic en **Propiedades** y después haga clic en **Avanzadas**.

     El cuadro de lista **Versión de CLR de destino** muestra **Automática** y las versiones del runtime de [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] que están instaladas en el equipo.

2. Realice uno de estos pasos:

    - Haga clic en la versión de CLR de la que desea generar perfiles.

    - Haga clic en **Automático** para generar perfiles de la primera versión que carga la aplicación.

## <a name="to-specify-the-net-framework-run-time-to-profile-when-attaching-the-profiler-to-an-application"></a>Para especificar el runtime de .NET Framework del que generar perfiles al adjuntar el generador de perfiles a una aplicación

1. En el menú **Analizar**, seleccione **Generador de perfiles** y después haga clic en **Asociar/desasociar**.

2. En el cuadro de diálogo **Asociar generador de perfiles al proceso**, haga clic en el proceso del que quiere generar perfiles.

     El cuadro de lista **Versión de CLR de destino** muestra **Automático** y las versiones del runtime de [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] que están instaladas en el equipo.

3. Realice uno de estos pasos:

    - Haga clic en la versión de CLR de la que desea generar perfiles.

    - Haga clic en **Automático** para generar perfiles de la versión que se carga cuando el generador de perfiles se adjunta a la aplicación.