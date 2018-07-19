---
title: Visual Studio y Xamarin | Microsoft Docs
ms.custom: ''
ms.date: 03/30/2018
ms.technology: vs-ide-mobile
ms.topic: conceptual
ms.assetid: 1da4064f-af69-472c-8f31-98484be5f790
author: charlespetzold
ms.author: chape
manager: crdun
ms.workload:
- xamarin
ms.openlocfilehash: 30bc5e4d14e09852904ca93087bdd99f6f2443ef
ms.sourcegitcommit: 4667e6ad223642bc4ac525f57281482c9894daf4
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/20/2018
ms.locfileid: "36280694"
---
# <a name="visual-studio-and-xamarin"></a>Visual Studio y Xamarin

Xamarin es una plataforma de desarrollo de aplicaciones móviles para compilar aplicaciones para iOS, Android y Windows nativas a partir de una base de código C#/.NET común. Las aplicaciones escritas con Xamarin pueden lograr un grado de reutilización de código entre plataformas de entre un 75% y casi un 100%. Estas aplicaciones tienen acceso total a las API de la plataforma subyacente y pueden incorporar interfaces de usuario nativas. Se compilan en paquetes específicos de la plataforma con poco impacto en el rendimiento del runtime. (Nota: Xamarin también es compatible con F#, pero en esta documentación se centrará solo en C#. Visual Basic no se admite en este momento).

Los programadores familiarizados con C#, .NET y Visual Studio disfrutarán de la misma potencia y productividad al trabajar con Xamarin para aplicaciones móviles. Estas ventajas incluyen la depuración remota en dispositivos Android, iOS y Windows, sin tener que aprender lenguajes de codificación nativos como Objective-C o Java. No sorprende, por tanto, que muchas aplicaciones de alto rendimiento con interfaces de usuario atractivas, como NASCAR, Aviva y MixRadio, estén compiladas con Xamarin.

Esta documentación lo ayudará a evaluar la potencia completa de **Visual Studio con Xamarin** para crear estas experiencias.

-   Comience con [Setup and install](../cross-platform/setup-and-install.md), un proceso que tardará algo de tiempo (por lo general, de 2 a 4 horas dependiendo de la velocidad de la conexión a Internet, de lo que tenga instalado y de las opciones que seleccione).

-   Mientras se ejecutan los instaladores, puede ver [Más información sobre el desarrollo móvil con Xamarin](learn-about-mobile-development-with-xamarin.md) que le informará sobre la naturaleza de Xamarin, comparará Xamarin.Forms con la interfaz de usuario nativa y mucho más.

-   Cuando se complete la instalación, vea [Comprobar el entorno de Xamarin](../cross-platform/verify-your-xamarin-environment.md).

-   Para terminar, revise el tutorial [Información sobre los conceptos básicos de la compilación de aplicaciones con Xamarin.Forms en Visual Studio](learn-app-building-basics-with-xamarin-forms-in-visual-studio.md).

Puede trabajar con todas las características de Xamarin con [cualquier edición de Visual Studio 2017](https://visualstudio.microsoft.com/vs) (Community, Professional y Enterprise). No es necesaria ninguna licencia aparte.

> [!NOTE]
>  En estas instrucciones se describe la configuración del equipo más fácil y directa para los desarrolladores que tienen experiencia con Windows y Visual Studio. Con esta configuración, la experiencia de desarrollo global se simplifica porque solo se debe interactuar con el Mac para usar el simulador de iOS y los dispositivos anclados a red. Si en su lugar tiene experiencia con Mac, se recomienda ejecutar Visual Studio en Parallels o VMWare, o usar Visual Studio para Mac. Para obtener instrucciones, vea [Configuración, instalación y comprobaciones para usuarios de Mac](../cross-platform/setup-install-and-verifications-for-mac-users.md).

> [!NOTE]
>  Si está buscando una solución de desarrollo multiplataforma basada en HTML y CSS, pruebe Visual Studio Tools para Apache Cordova como se describe en [Desarrollo multiplataforma en Visual Studio](../cross-platform/cross-platform-mobile-development-in-visual-studio.md#HTML).