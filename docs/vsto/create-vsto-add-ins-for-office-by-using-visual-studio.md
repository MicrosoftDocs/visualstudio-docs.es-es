---
title: Crear complementos de VSTO para Office con Visual Studio
description: Obtenga información sobre cómo puede usar las herramientas Microsoft Office desarrolladores de Visual Studio para crear .NET Framework aplicaciones que extienden Office.
titleSuffix: ''
ms.custom: seodec18, SEO-VS-2020
ms.date: 04/28/2021
ms.topic: conceptual
dev_langs:
- VB
- CSharp
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 990caeec642a745bec5b6e0f2d29ff5d6213d095
ms.sourcegitcommit: 9cb0097c33755a3e5cbadde3b0a6e9e76cee727d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/13/2021
ms.locfileid: "109848323"
---
# <a name="create-vsto-add-ins-for-office-by-using-visual-studio"></a>Crear complementos de VSTO para Office con Visual Studio
> [!IMPORTANT]
> VSTO se basa en el [.NET Framework](https://docs.microsoft.com/dotnet/framework/get-started/overview). Los complementos COM también se pueden escribir con el .NET Framework. Los complementos de Office no se pueden crear con .NET Core y [.NET 5+](https://docs.microsoft.com/dotnet/core/dotnet-five), las versiones más recientes de .NET. Esto se debe a que .NET Core/.NET 5+ no puede funcionar junto con .NET Framework en el mismo proceso y puede provocar errores de carga de complementos. Puede seguir usando .NET Framework para escribir complementos VSTO y COM para Office. Microsoft no actualizará VSTO ni la plataforma de complementos COM para usar .NET Core o .NET 5+. Puede aprovechar las ventajas de .NET Core y .NET 5+, incluido ASP.NET Core, para crear el lado servidor de los complementos [web de Office.](https://docs.microsoft.com/office/dev/add-ins/overview/office-add-ins)

  Puede usar las herramientas para desarrolladores de Microsoft Office en Visual Studio para crear aplicaciones de .NET Framework que amplíen Office. Estas aplicaciones también se denominan *soluciones de Office*.

 Office Developer Tools proporciona características que ayudan a crear soluciones de Office para diversas necesidades empresariales. Las herramientas incluyen plantillas de proyecto para crear soluciones de Office mediante Visual Basic o Visual C# y diseñadores visuales para interfaces de usuario personalizadas para las soluciones de Office.

[!include[Add-ins note](includes/addinsnote.md)]

 Para obtener la información más reciente sobre el desarrollo de Office, consulte el [centro Microsoft Office desarrolladores.](https://developer.microsoft.com/office/docs)

## <a name="in-this-section"></a>En esta sección
- [Introducción al &#40;desarrollo de Office en Visual Studio&#41;](getting-started-office-development-in-visual-studio.md)

 Proporciona vínculos a información acerca de cómo configurar un equipo de desarrollo para crear soluciones de Office, cómo empezar a crear soluciones de Office y novedades del desarrollo de Office en Visual Studio.

- [Actualización y migración de soluciones de Office](upgrading-and-migrating-office-solutions.md)

 Proporciona vínculos a información sobre el proceso de actualización para los proyectos creados con versiones anteriores de Visual Studio.

- [Arquitectura de soluciones de Office en Visual Studio](architecture-of-office-solutions-in-visual-studio.md)

 Proporciona vínculos a información sobre cómo funcionan las soluciones de Office, con información sobre las personalizaciones de nivel de documento y los complementos de VSTO.

- [Diseño y creación de soluciones de Office](designing-and-creating-office-solutions.md)

 Proporciona información sobre cómo crear un proyecto de Office y configurar el proyecto en Visual Studio.

- [Desarrollo de soluciones de Office](developing-office-solutions.md)

 Proporciona información sobre cómo usar código administrado con soluciones de Office, incluido cómo personalizar la interfaz de usuario de Office, trabajar con datos y solucionar problemas.

- [Soluciones de Excel](excel-solutions.md)

 Proporciona información acerca de cómo automatizar Excel, crear soluciones de Excel y comprender los problemas de globalización específicos de Excel.

- [Soluciones de InfoPath](infopath-solutions.md)

 Proporciona información sobre cómo crear plantillas de formulario y complementos de VSTO para InfoPath.

- [Soluciones de Outlook](outlook-solutions.md)

 Proporciona información sobre cómo automatizar Outlook y crear complementos de VSTO de Outlook y áreas del formulario.

- [Soluciones de PowerPoint](powerpoint-solutions.md)

 Proporciona información sobre cómo automatizar PowerPoint y crear complementos de VSTO de PowerPoint.

- [Soluciones de proyecto](project-solutions.md)

 Proporciona información sobre cómo automatizar Microsoft Office proyecto y crear complementos vsTO de proyecto.

- [Soluciones de Visio](visio-solutions.md)

 Proporciona información sobre cómo automatizar Visio y crear complementos de VSTO de Visio.

- [Soluciones de Word](word-solutions.md)

 Proporciona información acerca de cómo automatizar Word y crear soluciones de Word.

- [Compilación de soluciones de Office](building-office-solutions.md)

 Proporciona información acerca de las diferencias entre la compilación de proyectos de Office y otros tipos de proyectos en [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].

- [Depuración de proyectos de Office](debugging-office-projects.md)

 Proporciona información acerca de las diferencias entre la depuración de proyectos de Office y otros tipos de proyectos en [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].

- [Soluciones seguras de Office](securing-office-solutions.md)

 Proporciona información acerca de cómo funcionan las características de seguridad en las soluciones de Office.

- [Implementación de una solución de Office](deploying-an-office-solution.md)

 Proporciona información sobre cómo crear soluciones de Office disponibles para los usuarios y las principales cuestiones a considerar cuando se elige un método de implementación.

- [Ejemplos y tutoriales de desarrollo de Office](office-development-samples-and-walkthroughs.md)

 Proporciona vínculos a aplicaciones de ejemplo y temas que proporcionan instrucciones paso a paso para realizar tareas habituales.

- [Referencia general &#40;desarrollo de Office en Visual Studio&#41;](general-reference-office-development-in-visual-studio.md)

 Proporciona vínculos a información detallada sobre los ensamblados de interoperabilidad primarios de Office, manifiestos, elementos de la interfaz de usuario y mensajes de error.

- [Referencia administrada &#40;desarrollo de Office en Visual Studio&#41;](managed-reference-office-development-in-visual-studio.md)

 Proporciona vínculos a información acerca de los tipos y espacios de nombres de API que se usan en los proyectos de Office para [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]. Para obtener documentación de referencia de API sobre los espacios de nombres y los tipos que se usan en los proyectos de Office que tienen como destino .NET Framework 3.5, vea la siguiente sección de referencia en la documentación de Visual Studio 2008: Referencia administrada por el sistema de [2007](managed-reference-office-development-in-visual-studio.md).

- [Referencia de API no administrada &#40;desarrollo de Office en Visual Studio&#41;](unmanaged-api-reference-office-development-in-visual-studio.md)

 Contiene vínculos a información sobre las interfaces COM que se pueden usar para realizar acciones como cargar y descargar complementos de VSTO administrados en las aplicaciones de Office.

## <a name="related-sections"></a>Secciones relacionadas
- [Desarrollo de Office Visual Studio portal para desarrolladores](https://developer.microsoft.com/office/docs) Proporciona recursos adicionales, como artículos técnicos, vídeos y blogs.

- [Visual Studio centro para desarrolladores](https://visualstudio.microsoft.com/) Proporciona recursos Visual Studio como artículos técnicos, vídeos y blogs.

- [Microsoft Office de desarrollo de MSDN Library](/previous-versions/office/office-12/bb726434(v=office.12)) Área de MSDN Library donde puede encontrar artículos y documentación de referencia sobre el desarrollo de soluciones para varias versiones de Office (no específica para el desarrollo de Office mediante Visual Studio).

- [Desarrollo de aplicaciones en Visual Studio](/previous-versions/h8w79z10(v=vs.140)) Contiene vínculos a temas que explican cómo puede usar Visual Studio para diseñar, desarrollar, depurar e implementar aplicaciones web, servicios web XML y aplicaciones cliente tradicionales.

- [.NET Framework programación en Visual Studio](/previous-versions/visualstudio/visual-studio-2010/k1s94fta(v=vs.100)) Describe el desarrollo de aplicaciones con la .NET Framework en Visual Basic y Visual C#.
