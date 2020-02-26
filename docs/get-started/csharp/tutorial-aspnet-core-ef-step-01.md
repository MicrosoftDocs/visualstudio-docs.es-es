---
title: Aplicación web de ASP.NET Core con Entity Framework y Visual Studio 2019
titleSuffix: ''
description: Como primer paso antes de crear una aplicación web de ASP.NET Core, obtenga información sobre cómo instalar Visual Studio 2019 con este tutorial en vídeo e instrucciones detalladas.
ms.custom: get-started
ms.date: 03/31/2019
ms.technology: vs-ide-general
ms.prod: visual-studio-windows
monikerRange: vs-2019
ms.topic: tutorial
ms.devlang: CSharp
author: ardalis
ms.author: ornella
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- aspnet
- dotnetcore
ms.openlocfilehash: d900c0f51b14450f38caf06738739daef2549235
ms.sourcegitcommit: 2ae2436dc3484b9dfa10e0483afba1e5a02a52eb
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/25/2020
ms.locfileid: "77580090"
---
# <a name="tutorial-create-your-first-aspnet-core-app-using-entity-framework-with-visual-studio-2019"></a>Tutorial: Creación de la primera aplicación de ASP.NET Core mediante Entity Framework con Visual Studio 2019

En este tutorial, creará una aplicación web de ASP.NET Core que usa datos y, después, la implementará en Azure. Este tutorial se compone de los siguientes pasos:

- [Paso 1: Instale Visual Studio 2019](#step-1-install-visual-studio-2019)
- [Paso 2: Creación de la primera aplicación web de ASP.NET Core](tutorial-aspnet-core-ef-step-02.md)
- [Paso 3: Trabajo con datos mediante Entity Framework](tutorial-aspnet-core-ef-step-03.md)
- [Paso 4: Exposición de una API web desde la aplicación de ASP.NET Core](tutorial-aspnet-core-ef-step-04.md)
- [Paso 5: Implementación de la aplicación de ASP.NET Core en Azure](tutorial-aspnet-core-ef-step-05.md)

## <a name="step-1-install-visual-studio-2019"></a>Paso 1: Instalación de Visual Studio 2019

Obtenga información sobre cómo instalar Visual Studio 2019 con este tutorial en vídeo e instrucciones detalladas. Si ya ha instalado Visual Studio, vaya al [Paso 2: Creación de la primera aplicación web de ASP.NET Core](tutorial-aspnet-core-ef-step-02.md).

_Vea este vídeo y siga el tutorial para instalar Visual Studio y crear la primera aplicación de ASP.NET Core._

> [!VIDEO https://www.youtube.com/embed/Fz_HAqQGLtY]

## <a name="download-the-installer"></a>Descarga del instalador

Vaya a [visualstudio.com](https://visualstudio.com) para encontrar el instalador. Busque el vínculo de Visual Studio 2019 y haga clic en él para iniciar la descarga. Para obtener una versión gratuita de Visual Studio, elija Visual Studio Community.

## <a name="start-the-installer"></a>Inicio del instalador

Una vez completada la descarga, haga clic en **Ejecutar** para iniciar el instalador.

![Instalador de Visual Studio 2019](media/vs-2019/vs2019-installer.png)

## <a name="choose-workloads"></a>Elección de las cargas de trabajo

Visual Studio se puede usar para muchos tipos diferentes de tareas de desarrollo, y las cargas de trabajo facilitan la descarga de todo lo necesario para el tipo de aplicaciones que desea compilar. Por ahora, elija las cargas de trabajo **Desarrollo de ASP.NET y web** y **Desarrollo multiplataforma de .NET Core**. Siempre puede volver a ejecutar el instalador más adelante para instalar componentes y cargas de trabajo adicionales.

![Elección de cargas de trabajo en Visual Studio 2019](media/vs-2019/vs2019-choose-workloads.png)

## <a name="install"></a>Instalar

Haga clic en **Instalar** y deje que el instalador se descargue e instale Visual Studio.

## <a name="run-visual-studio-for-the-first-time"></a>Primera ejecución de Visual Studio

Visual Studio debe iniciarse automáticamente cuando el instalador finaliza. Puede que se le pida que inicie sesión, una acción que tiene algunas características interesantes asociadas, pero, por ahora, puede elegir hacerlo más tarde. A continuación, puede elegir la configuración de desarrollo y el tema. Una vez haya seleccionado estas opciones, podrá empezar con su primer proyecto. Haga clic en **Crear un proyecto nuevo** y, después, elija **Aplicación web ASP.NET Core**.

![Creación de un proyecto de aplicación web ASP.NET Core en Visual Studio 2019](media/vs-2019/vs2019-create-new-project.png)

## <a name="explore-aspnet-core-project-types"></a>Exploración de los tipos de proyectos de ASP.NET Core

Puede elegir el nombre del proyecto y la ubicación y, luego, seleccionar **Crear**. Ahora, elija qué plantilla desea usar para la aplicación de ASP.NET Core. Puede elegir entre las siguientes opciones:

- Vacía. Una plantilla de proyecto vacía que le permite empezar desde cero.
- API. Recomendada para las API web.
- Aplicación web. Una aplicación web estándar de ASP.NET Core compilada con Razor Pages.
- Aplicación web (Modelo-Vista-Controlador). Una aplicación web estándar de ASP.NET Core que usa el patrón Modelo-Vista-Controlador.
- Angular.
- React.js.
- React.js/Redux.
- Biblioteca de clases de Razor. Se utiliza para compartir los recursos de Razor entre proyectos.

Tenga en cuenta que para la mayoría de las plantillas de proyecto también puede elegir habilitar la compatibilidad con Docker mediante la activación de una casilla. También puede agregar compatibilidad con la autenticación, para lo que debe hacer clic en el botón Cambiar autenticación. Ahí, puede elegir entre las siguientes opciones:

- Sin autenticación.
- Cuentas de usuario individuales. Se almacenan en una base de datos local o basada en Azure.
- Cuentas profesionales o educativas. Esta opción usa Active Directory, Azure AD u Office 365 para la autenticación.
- Autenticación de Windows. Conveniente para las aplicaciones de intranet.

Seleccione la plantilla de aplicación web estándar sin autenticación y haga clic en **Crear**.

![Elección de opciones de proyecto de ASP.NET Core en Visual Studio 2019](media/vs-2019/vs2019-choose-aspnetcore-project.png)

## <a name="next-steps"></a>Pasos siguientes

En el siguiente vídeo, aprenderá más acerca de su primer proyecto de ASP.NET Core.

[Tutorial: Creación de la primera aplicación web de ASP.NET Core](tutorial-aspnet-core-ef-step-02.md)

## <a name="see-also"></a>Vea también

- [Tutorial: Introducción a C# y ASP.NET Core](tutorial-aspnet-core.md) Un tutorial más detallado sin una guía en vídeo
