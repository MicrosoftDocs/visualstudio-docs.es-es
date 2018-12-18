---
title: 'Cómo: Generar perfiles de código de JavaScript en páginas web | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- JavaScript performance profiling
- Profiling Tools,JavaScript
- web site performance profiling
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 007603f0695a658b6bfa6c1ab1173b4483004c13
ms.sourcegitcommit: ce154aee5b403d5c1c41da42302b896ad3cf8d82
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/07/2018
ms.locfileid: "34843928"
---
# <a name="how-to-profile-javascript-code-in-web-pages"></a>Cómo: Generar perfiles de código de JavaScript en páginas web

Las Herramientas de generación de perfiles de Visual Studio pueden recopilar datos de rendimiento del código JavaScript que se ejecuta en un aplicación web [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)], una página web arbitraria o una aplicación JavaScript usando el método de generación de perfiles de instrumentación. Requiere Internet Explorer 8 o posterior.

> [!WARNING]
> Para generar perfiles de JavaScript en aplicaciones para UWP, vea [Memoria de JavaScript](../profiling/javascript-memory.md). 

Puede usar el Asistente para generación de perfiles para crear una sesión de rendimiento. Especifique el método de instrumentación y, después, especifique la opción de generación de perfiles de JavaScript de la página Instrumentación del cuadro de diálogo de propiedades de la sesión de rendimiento.

Cuando se especifica la generación de perfiles de JavaScript, se generan los perfiles del código JavaScript que se ejecuta en el explorador y del código [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] que se ejecuta en el servidor.

- Para una aplicación web [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)], se generan los perfiles del código JavaScript que se ejecuta en el explorador y del código [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] que se ejecuta en el servidor.

- Para una página web arbitraria, se genera el perfil del código JavaScript que se ejecuta en el explorador.

## <a name="to-profile-javascript-in-an-aspnet-web-application-project"></a>Para generar perfiles de JavaScript en un proyecto de aplicación web ASP.NET

1. Abra el proyecto web [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] en Visual Studio.

2. En el menú **Analizar** , haga clic en **Iniciar Asistente de rendimiento**.

3. En la primera página del Asistente de rendimiento, especifique el método de generación de perfiles **Instrumentación** y, luego, haga clic en **Siguiente**.

4. En la segunda página del asistente, asegúrese de que el proyecto actual está seleccionado en la lista de destinos y, después, haga clic en **Siguiente**.

5. En la tercera página del asistente, active la casilla **Generar perfiles de JavaScript** y, después, haga clic en **Siguiente**.

6. En la cuarta página del asistente, haga clic en **Finalizar** para iniciar la aplicación web en el explorador.

7. Ejecute la funcionalidad de la que desea generar perfiles.

8. Para finalizar la sesión de generación de perfiles, cierre el explorador.

### <a name="to-profile-javascript-in-individual-web-pages-or-a-javascript-applications"></a>Para generar perfiles de JavaScript en páginas web individuales o aplicaciones JavaScript

1. Abra Visual Studio.

2. En el menú **Analizar** , haga clic en **Iniciar Asistente de rendimiento**.

3. En la primera página del Asistente de rendimiento, especifique el método de generación de perfiles **Instrumentación** y, luego, haga clic en **Siguiente**.

4. En la segunda página del asistente, haga clic en la aplicación ASP.NET o JavaScript y, después , en **Siguiente**.

5. En la tercera página del asistente:

    1. Escriba la dirección URL de la página en el cuadro **¿Qué dirección URL o ruta de acceso ejecutará la aplicación web?**

    2. Active la casilla **Generar perfiles de JavaScript** y, después, haga clic en **Siguiente**.

6. En la cuarta página del asistente, haga clic en **Finalizar** para iniciar la aplicación web en el explorador.

7. Ejecute la funcionalidad de la que desea generar perfiles.

8. Para finalizar la sesión de generación de perfiles, cierre el explorador.