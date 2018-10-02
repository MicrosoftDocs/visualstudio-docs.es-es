---
title: 'Cómo: Generar perfiles de código de JavaScript en páginas web | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- JavaScript performance profiling
- Profiling Tools,JavaScript
- web site performance profiling
ms.assetid: 37d02aad-ca4d-4eb0-bf66-ca3ecef31fbe
caps.latest.revision: 32
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a54321b835cad9f37983a386c93f46e26bbdd5ff
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47577454"
---
# <a name="how-to-profile-javascript-code-in-web-pages"></a>Cómo: Generar perfiles de código de JavaScript en páginas web
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [Cómo: Perfilar el código JavaScript en páginas Web](https://docs.microsoft.com/visualstudio/profiling/how-to-profile-javascript-code-in-web-pages).  
  
Las herramientas de generación de perfiles de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] pueden recopilar datos de rendimiento del código JavaScript que se ejecuta en un aplicación web [!INCLUDE[vstecasp](../includes/vstecasp-md.md)], una página web arbitraria o una aplicación JavaScript usando el método de generación de perfiles de instrumentación.  
  
 **Requisitos**  
  
-   [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)], [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)], [!INCLUDE[vsPro](../includes/vspro-md.md)]  
  
-   Internet Explorer 8 o posterior.  
  
> [!WARNING]
>  Para generar perfiles de JavaScript en aplicaciones de la Tienda Windows, consulte uno de los siguientes temas:  
>   
>  -   [Tiempo de función de JavaScript](http://msdn.microsoft.com/library/b2bf49fc-aea7-4d9c-8fcf-cff8b8dd0c03) [tiempo de función de JavaScript en un dispositivo remoto](http://msdn.microsoft.com/library/d78812b6-a97e-46dc-8d99-e724d1d725d8)  
> -   [Analizar datos de tiempo de función de JavaScript](http://msdn.microsoft.com/library/b5aea8d8-36df-47ba-a7ca-95406700ca9b)  
> -  
  
 Puede usar el Asistente para generación de perfiles para crear una sesión de rendimiento. Especifique el método de instrumentación y, después, especifique la opción de generación de perfiles de JavaScript de la página Instrumentación del cuadro de diálogo de propiedades de la sesión de rendimiento.  
  
 Cuando se especifica la generación de perfiles de JavaScript, se generan los perfiles del código JavaScript que se ejecuta en el explorador y del código [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] que se ejecuta en el servidor.  
  
-   Para una aplicación web de [!INCLUDE[vstecasp](../includes/vstecasp-md.md)], se generan los perfiles del código JavaScript que se ejecuta en el explorador y del código [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] que se ejecuta en el servidor.  
  
-   Para una página web arbitraria, se genera el perfil del código JavaScript que se ejecuta en el explorador.  
  
### <a name="to-profile-javascript-in-an-aspnet-web-application-project"></a>Para generar perfiles de JavaScript en un proyecto de aplicación web ASP.NET  
  
1.  En [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)], abra el proyecto web [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] .  
  
2.  En el menú **Analizar** , haga clic en **Iniciar Asistente de rendimiento**.  
  
3.  En la primera página del Asistente de rendimiento, especifique el método de generación de perfiles **Instrumentación** y, luego, haga clic en **Siguiente**.  
  
4.  En la segunda página del asistente, asegúrese de que el proyecto actual está seleccionado en la lista de destinos y, después, haga clic en **Siguiente**.  
  
5.  En la tercera página del asistente, active la casilla **Generar perfiles de JavaScript** y, después, haga clic en **Siguiente**.  
  
6.  En la cuarta página del asistente, haga clic en **Finalizar** para iniciar la aplicación web en el explorador.  
  
7.  Ejecute la funcionalidad de la que desea generar perfiles.  
  
8.  Para finalizar la sesión de generación de perfiles, cierre el explorador.  
  
### <a name="to-profile-javascript-in-individual-web-pages-or-a-javascript-applications"></a>Para generar perfiles de JavaScript en páginas web individuales o aplicaciones JavaScript  
  
1.  Abra [!INCLUDE[vsPreShort](../includes/vspreshort-md.md)].  
  
2.  En el menú **Analizar** , haga clic en **Iniciar Asistente de rendimiento**.  
  
3.  En la primera página del Asistente de rendimiento, especifique el método de generación de perfiles **Instrumentación** y, luego, haga clic en **Siguiente**.  
  
4.  En la segunda página del asistente, haga clic en la aplicación ASP.NET o JavaScript y, después , en **Siguiente**.  
  
5.  En la tercera página del asistente:  
  
    1.  Escriba la dirección URL de la página en el cuadro **¿Qué dirección URL o ruta de acceso ejecutará la aplicación web?**  
  
    2.  Active la casilla **Generar perfiles de JavaScript** y, después, haga clic en **Siguiente**.  
  
6.  En la cuarta página del asistente, haga clic en **Finalizar** para iniciar la aplicación web en el explorador.  
  
7.  Ejecute la funcionalidad de la que desea generar perfiles.  
  
8.  Para finalizar la sesión de generación de perfiles, cierre el explorador.



