---
title: Características de Visual Studio compatibles (Preview)
description: Infórmese de las características del IDE de Visual Studio disponibles cuando trabaje con GitHub Codespaces.
ms.topic: how-to
ms.date: 09/21/2020
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
ms.workload:
- multiple
monikerRange: vs-2019
ms.openlocfilehash: c86fc99fe6bd2ae17b6ce222b04549db07d7687e
ms.sourcegitcommit: 062615c058d2ff44751e8d0c704ccfa3c5543469
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/22/2020
ms.locfileid: "90862488"
---
# <a name="supported-visual-studio-features-preview"></a>Características de Visual Studio compatibles (Preview)

Visual Studio proporciona una experiencia de desarrollo enriquecida al conectarse a un codespace. Conseguirá las herramientas de bucle interno de Visual Studio con las que está familiarizado para editar, depurar, probar y crear versiones del código fuente, además de características de productividad, como plantillas de proyecto, navegación por el código enriquecida e IntelliSense.

En la actual versión [beta pública](https://github.com/features/codespaces) de GitHub Codespaces, es posible que algunas características de Visual Studio no sean completamente compatibles o falten inicialmente. En las secciones siguientes se describe lo que puede esperar con Visual Studio y la versión beta de GitHub Codespaces y lo que puede desear en el futuro. 

Esto no **pretende ser una lista exhaustiva**, sino explicar la funcionalidad general de Visual Studio cuando se conecta a un codespace.

> [!NOTE]
> Si echa en falta alguna característica al usar codespaces con Visual Studio, háganoslo saber creando una incidencia en https://developercommunity.visualstudio.com/. Esto nos ayuda a priorizar las características más deseadas.

> [!NOTE]
> Las características que se describen a continuación corresponden a Visual Studio y no a los otros dos clientes de GitHub Codespaces: Visual Studio Code y el editor del explorador.

## <a name="edit-and-navigation"></a>Edición y navegación

Observará poca diferencia en la edición de código fuente en un codespace a medida que obtenga características de lenguaje inteligente como IntelliSense, navegación por el código, diagnósticos y sugerencias.

* IntelliSense*
* Navegación por el código*
* Formato de código con Dar formato al documento
* Resalte de sintaxis
* Información rápida*
* Editores de HTML, CSS, Razor*: compatibilidad parcial.
* Editor de JavaScript*: compatibilidad parcial.

No disponible aún:

* IntelliSense*: algunos de los filtros de finalización automática/lista de miembros no están disponibles. La finalización de tipos no importados e IntelliSense en la ventana de inspección todavía no está disponible.
* Navegación por el código*: se admite la mayoría de los comandos, en concreto, Ir a base y Buscar en archivos con una especificación de ruta de acceso que todavía no se admite.
* Información rápida*: no se admite la coloración de información rápida.
* Editores de HTML, CSS, Razor*: diagnósticos, finalización de IntelliSense, información rápida, sangría inteligente. Actualmente no se admite coloración semántica, comandos de navegación, etc.
* Editor de JavaScript*: aún no se admiten bloques de scripts (por ejemplo, contenido de JavaScript en archivos HTML y CSHTML) ni resaltado semántico. Problemas conocidos de características de bombilla y linting.
* Vista de destinos de CMake
* Editor de configuración del proyecto de CMake
* Ctrl+F7 (compilar archivo)
* CodeLens
* Fragmentos de código
* IntelliCode

## <a name="application-types-and-configuration"></a>Tipos y configuración de aplicaciones

Se admite la mayoría de los tipos de aplicación y las configuraciones de proyecto, pero tendrá que editar el código del proyecto directamente sin la ayuda de los diseñadores visuales. Para más instrucciones sobre la configuración, consulte [Personalización de un codespace](customize-codespaces.md).

* Plantillas de proyecto y elemento
* Proyectos de .NET Core y ASP.NET Core
* Aplicaciones de consola C++: se admiten CMake y vcxproj
* Aplicaciones C++ destinadas a Linux: se admiten en su mayor parte en caso de ausencia de interfaz gráfica de usuario. Capacidad de instalar y aprovisionar WSL, IntelliSense específico de la plataforma, y compilar.
* Edición de archivos de proyecto: se admite en su mayor parte. Faltan algunas características de finalización, resaltado de sintaxis y edición avanzada.
* Cuentas de GitHub: se pueden usar para crear y conectarse a Codespaces y acceder a los recursos disponibles para la cuenta en GitHub.
* CLI de Azure: no comparte las cuentas de identidad o cadena de claves de Visual Studio con sesión iniciada. No se admite el inicio de sesión basado en el explorador, pero puede autenticarse en el terminal integrado mediante: `az login --use-device-code`.

No disponible aún:

* Diseñadores de UI: diseñadores de WinForms y WPF
* Proyectos de Visual Basic y F#
* Proyectos destinados a .NET Framework
* Proyectos de Docker Compose
* Páginas de propiedades del proyecto
* Opciones de autenticación en plantillas de ASP.NET Core
* Aplicaciones que requieren una interfaz gráfica de usuario para su instalación: se admite todo lo que se puede instalar con el terminal (incluido el instalador de Chocolatey), pero la interfaz gráfica de usuario real no estará disponible de inmediato. La habilitación de Live Share de pantalla completa para acceder a las interfaces gráficas de usuario es una solución alternativa en este momento. No se puede acceder a las consolas de administración. No se admiten las aplicaciones que requieren un reinicio para su instalación.
* Integración de identidades administradas para recursos de Azure en Visual Studio
* Recursos de la intranet (red privada): Actualmente, codespaces no podrá conectarse a ningún recurso que requiera una VPN.
* Extensiones: no se admiten extensiones cuando se usa Codespaces con Visual Studio.

## <a name="debugging"></a>Depuración

Se admite la depuración de bucles internos esenciales, como el establecimiento de puntos de interrupción, el recorrido paso a paso básico de código, la inspección de variables y las ventanas Variables locales, Automático e Inspección. No se admiten algunas ventanas, personalizaciones y visualizadores adicionales.

* Puntos de interrupción*
* Recorrido paso a paso básico
* Ventanas Variables locales, Automático, Inspección*: compatibilidad parcial.
* Se admiten parcialmente el servidor de símbolos, el servidor de origen y las sugerencias sobre importación y exportación de datos.

No disponible aún:

* Puntos de interrupción*: etiquetas de punto de interrupción, puntos de interrupción de datos y Establecer punto de interrupción en la ventana Desensamblado están en curso. Se admite parcialmente la importación y exportación de puntos de interrupción.
* Ventanas Variables locales, Automático, Inspección*: algunas funciones como la finalización de instrucciones en el cuadro de búsqueda y la navegación del cuadro de búsqueda.
* Personalizaciones de la interfaz de usuario: no se admite anclar propiedades y ocultar parámetros de plantilla.
* Visualizadores: se admiten parcialmente los archivos Natvis en C++. No se admiten la ventana Desensamblado, el diagnóstico visual XAML, los visualizadores de .NET personalizados y los visualizadores de conjuntos de datos.
* Ventanas de depurador adicionales: se admiten parcialmente las ventanas Procesos. Ventana Pilas paralelas: no se admiten la vista tareas, el concentrador de diagnósticos y el cuadro de diálogo Buscar código fuente/símbolo.
* Algunos flujos de trabajo del depurador: asociar al proceso, el depurador Just-in-Time (JIT), la depuración de volcado, la generación de perfiles e IntelliTrace no se admiten. Se admite parcialmente el recorrido paso a paso de Solo mi código de C++.
* Editar y continuar: no se admite para código administrado y nativo.
* Características de subprocesos: no se admiten inmovilizar o reanudar subprocesos, cambiar nombre de subprocesos y mostrar subprocesos en código fuente no se admiten.
* Características adicionales de recorrido paso a paso: Saltar propiedades y operadores automáticamente (.NET Core) e Ir a específico. 

## <a name="features"></a>Características

Al trabajar con Visual Studio conectado a un codespace, se obtienen las mismas características de accesibilidad que al trabajar de forma local.

* Control de código fuente: compatibilidad con Git completa a través de la nueva [ventana de Git](https://devblogs.microsoft.com/visualstudio/improved-git-experience-in-visual-studio-2019/).
* Accesibilidad: hay un problema conocido con la tecnología de asistencia que no es capaz de acceder a la appcasting de una aplicación depurada. Además de esta limitación, no creemos que haya otros problemas de compatibilidad que no existan ya en la experiencia de Visual Studio local. Si detecta errores comuníquenoslo presentando una incidencia en [Developer Community](https://developercommunity.visualstudio.com/).
* Publicación: se admite la publicación en Azure a través de Acciones de GitHub.
* Servicios conectados: se admiten parcialmente App Insights, KeyVault, Storage, SQL, Redis, Cosmos, openAPI y gRPC.
* Explorador de pruebas*: en su mayor parte.

No disponible aún:

* Explorador de pruebas *: algunas características, como la selección de arquitectura predeterminada, la ejecución de pruebas en paralelo, listas de reproducción, etc. Problemas conocidos con la depuración de una prueba unitaria, la configuración de ejecución y algunas características empresariales adicionales. No se admiten las pruebas unitarias de generación de perfiles.
* Interfaz de usuario del administrador de paquetes NuGet: se admite la línea de comandos de NuGet.
* Características de pruebas empresariales: no se admiten Live Unit Testing, Microsoft Fakes, Cobertura de código e IntelliTest.
* Escenarios de publicación avanzada: publicación selectiva, publicación FTP, cambios en la versión preliminar, barra de herramientas de publicación rápida, etc.

## <a name="see-also"></a>Consulte también

* [¿Qué es GitHub Codespaces?](codespaces-overview.md)
* [Uso de Visual Studio con un codespace](use-visual-studio-with-codespaces.md)
* [Personalización de un codespace](customize-codespaces.md)
