---
title: "Dise&#241;ar y crear soluciones de Office | Microsoft Docs"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "desarrollo de Office en Visual Studio, crear soluciones"
  - "tipos de proyectos de Office en Visual Studio"
  - "soluciones de Office [desarrollo de Office en Visual Studio], crear"
  - "soluciones [desarrollo de Office en Visual Studio], crear"
ms.assetid: 53c32c61-3d3a-4427-a5a7-f9c2c8f1de02
caps.latest.revision: 103
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 99
---
# Dise&#241;ar y crear soluciones de Office
  Visual Studio proporciona plantillas de proyecto que puede usar para crear varios tipos distintos de soluciones de Office.  En esta sección de la documentación se describen las plantillas de proyecto y se ofrecen instrucciones sobre cómo crear proyectos de Office.  Para obtener información sobre cómo implementar personalizaciones de la interfaz de usuario y código después de haber creado el proyecto, vea [Desarrollar soluciones de Office](../vsto/developing-office-solutions.md).  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
## Crear proyectos de Office  
 Antes de empezar, debe determinar los requisitos y el tipo de solución que mejor se adapta a sus necesidades.  Por ejemplo, si su solución de Office debe ejecutarse cada vez que se utiliza la aplicación, un complemento de VSTO será lo que mejor se adapte a sus necesidades.  Si el código está estrechamente integrado con un único documento, cree una personalización de nivel de documento.  Estos tipos de proyecto están disponibles como plantillas de proyecto de Visual Studio.  Para obtener más información acerca de las plantillas de proyecto de Office que se incluyen con Visual Studio, vea [Información general sobre las plantillas de Office Project](../vsto/office-project-templates-overview.md).  Para obtener más información sobre cómo crear proyectos de Office, consulte [Cómo: Crear proyectos de Office en Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
 Los proyectos de Office tienen características y elementos de proyecto que difieren de otros tipos de proyectos de Visual Studio.  Por ejemplo, cuando se crea un proyecto de nivel de documento, el documento o el libro del proyecto se puede abrir y editar en Visual Studio.  Para obtener más información, vea [Proyectos de Office en el entorno de Visual Studio](../vsto/office-projects-in-the-visual-studio-environment.md).  
  
## Elegir una versión de .NET Framework  
 Después de seleccionar el tipo de proyecto que mejor se adapte a sus requisitos, puede elegir qué versión de .NET Framework se utilizará en el proceso de desarrollo.  Puede elegir como destino las siguientes versiones de .NET Framework en los proyectos de Office:  
  
-   [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]  
  
-   [!INCLUDE[net_client_v40_long](../vsto/includes/net-client-v40-long-md.md)]  
  
-   [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)]  
  
 La versión de .NET Framework que elija para el proyecto deberá estar instalada en los equipos de los usuarios finales para que la solución se pueda ejecutar.  Por ejemplo, si su proyecto tiene como destino la versión [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)], [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] deberá estar instalado en los equipos de los usuarios finales.  En este ejemplo, la solución no se ejecutará si solo está instalado .NET Framework 3.5 en los equipos de los usuarios finales.  
  
 Si migra un proyecto de complemento de VSTO que tiene como destino .NET Framework 3.5, Visual Studio cambia el marco de trabajo de destino del proyecto a [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] o a una versión posterior, según la versión de Office que haya instalado.  
  
 Sin embargo, una vez que Visual Studio cambie el marco de trabajo de destino, deberá modificar parte del código del proyecto si utiliza determinadas características.  Para obtener más información sobre cómo cambiar el marco de trabajo de destino, vea este artículo sobre [Cómo: Usar como destino una versión de .NET Framework](~/ide/how-to-target-a-version-of-the-dotnet-framework.md).  Para obtener más información acerca de los cambios que puede que deba realizar en el proyecto, vea este artículo sobre cómo [Migrar soluciones de Office a .NET Framework 4 o posterior](../vsto/migrating-office-solutions-to-the-dotnet-framework-4-or-later.md).  
  
 Si Visual Studio cambia la versión de .NET Framework de destino del proyecto y usa ClickOnce para implementar la solución, asegúrese de seleccionar también la versión correspondiente de .NET Framework en el cuadro de diálogo **Requisitos previos**.  Esta selección no cambia automáticamente al cambiar el marco de trabajo de destino del proyecto.  Para obtener más información, consulte este artículo sobre [Cómo: Instalar los requisitos previos en equipos de usuarios finales para ejecutar las soluciones de Office](http://msdn.microsoft.com/es-es/74dd2c52-838f-4abf-b2b4-4d7b0c2a0a98).  
  
> [!NOTE]  
>  No podrá elegir como destino la versión .NET Framework 3.5 o alguna versión anterior en proyectos de Office que cree mediante [!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)].  Los proyectos de Office que cree mediante [!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)] requieren características que se introdujeron por primera vez en [!INCLUDE[net_client_v40_long](../vsto/includes/net-client-v40-long-md.md)].  
  
### Cuándo se requieren los PIA de Office en los equipos de usuarios finales  
 De forma predeterminada, no es necesario instalar ensamblados de interoperabilidad primarios \(PIA\) de Office en los equipos de usuarios finales, si la propiedad **Incrustar tipos de interoperabilidad** de cada referencia de los PIA de Office en el proyecto está establecida en **True**, que es el valor predeterminado.  En este escenario, la información de tipo de los tipos de PIA que utiliza la solución se incrusta en el ensamblado de la solución al compilar el proyecto.  La información de tipo incrustada se usa en tiempo de ejecución en lugar de los PIA para llamar al modelo de objetos basado en COM de la aplicación de Office.  Para obtener más información sobre cómo se incrustan los tipos de PIA en la solución, vea este artículo sobre [Type Equivalence and Embedded Interop Types](http://msdn.microsoft.com/library/78892eba-2a58-4165-b4b1-0250ee2f41dc).  
  
 Si la propiedad **Incrustar tipos de interoperabilidad** de cada referencia de los PIA de Office en el proyecto está establecida en **False**, los PIA de Office deben instalarse y registrarse en la caché global de ensamblados en cada equipo de usuario final que ejecute la solución.  En la mayoría de los casos, los PIA se instalan de forma predeterminada con Office, pero también puede incluir el redistribuible de PIA como un requisito previo para una solución.  Para obtener más información, consulte este artículo sobre los [Requisitos previos de las soluciones de Office para su implementación](http://msdn.microsoft.com/es-es/9f672809-43a3-40a1-9057-397ce3b5126e).  
  
### Comprender Client Profile  
 .NET Framework Client Profile constituye un subconjunto de funcionalidades de la versión completa de .NET Framework.  Puede elegir como destino .NET Framework Client Profile si solo necesita utilizar las características de cliente de .NET Framework y desea proporcionar la experiencia de implementación más rápida posible para una solución de Office.  Para obtener más información, vea el artículo de [.NET Framework Client Profile](http://msdn.microsoft.com/library/f0219919-1f02-4588-8704-327a62fd91f1).  
  
 Cuando crea un proyecto de Office que tiene como destino [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)], [!INCLUDE[net_client_v40_long](../vsto/includes/net-client-v40-long-md.md)] se establece como destino de forma predeterminada. Si desea desarrollar la solución para la versión completa de [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)], debe establecer esta opción después de crear el proyecto.  Para obtener más información, vea este artículo sobre [Cómo: Usar como destino una versión de .NET Framework](~/ide/how-to-target-a-version-of-the-dotnet-framework.md).  
  
## Crear soluciones para la edición de 64 bits de Microsoft Office  
 Microsoft Office está disponible en ediciones de 64 bits y 32 bits.  Para crear soluciones de Office que se puedan ejecutar en ambas ediciones, la configuración de destino de la plataforma del proyecto debe establecerse en **Cualquier CPU**.  Este es el valor predeterminado para los proyectos de Office. Para obtener más información, vea [Compilar soluciones de Office](../vsto/building-office-solutions.md).  
  
 Hay versiones independientes de 64 bits y 32 bits de [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] que utilizan las ediciones de 64 bits y 32 bits de Microsoft Office.  Para obtener más información, consulte [Información general sobre el Motor en tiempo de ejecución de Microsoft Visual Studio Tools para Office](../vsto/visual-studio-tools-for-office-runtime-overview.md).  
  
## Ensamblados en las soluciones de Office  
 Al crear un proyecto de Office mediante las herramientas de desarrollo de Office en Visual Studio, el código que se escribe se compila finalmente en un ensamblado.  Normalmente, el ensamblado se implementa en un servidor compartido o en un directorio del equipo cliente.  
  
 Los ensamblados de las soluciones de Office se cargan a través de una aplicación de Office.  Una vez cargado el ensamblado, el código del ensamblado puede responder a eventos que se produzcan en la aplicación, como, por ejemplo, cuando un usuario hace clic en un elemento de menú.  El código del ensamblado también puede realizar llamadas en el modelo de objetos para automatizar y extender la aplicación, y utilizar cualquiera de las clases en [!INCLUDE[dnprdnshort](../sharepoint/includes/dnprdnshort-md.md)]. Para obtener más información, vea [Arquitectura de las personalizaciones de nivel de documento](../vsto/architecture-of-document-level-customizations.md) y [Arquitectura de complementos de VSTO](../vsto/architecture-of-vsto-add-ins.md).  
  
 Las soluciones de Office usan manifiestos de implementación y de aplicación para identificar el ensamblado.  Los manifiestos contienen información sobre el nombre, la versión y la ubicación del ensamblado, para que la aplicación pueda buscar y ejecutar el ensamblado adecuado, y establecer vínculos con este.  Para obtener más información, consulte [Manifiestos de implementación y aplicación en soluciones de Office](../vsto/application-and-deployment-manifests-in-office-solutions.md).  
  
 Los proyectos de nivel de documento incluyen un documento además de un ensamblado.  El documento actúa como el front\-end de la aplicación y es donde se realiza toda la interacción del usuario.  Cada documento solo puede tener un ensamblado de proyecto principal asociado a él. Sin embargo, varios documentos pueden apuntar al mismo ensamblado.  
  
 Los ensamblados en los proyectos de nivel de documento no se incrustan en el documento, sino que se almacenan en otra ubicación y se identifican mediante el manifiesto de aplicación del documento.  
  
## Consideraciones de seguridad para los ensamblados  
 Para que una solución de Office se ejecute en un equipo y lo hagan también los ensamblados que esta usa, estos ensamblados deben ser de confianza.  Para obtener más información acerca de la seguridad, consulte [Asegurar las soluciones de Office](../vsto/securing-office-solutions.md).  
  
 De forma predeterminada, el ensamblado de la solución y los ensamblados a los que se hace referencia y que se encuentran en la carpeta de salida del proyecto son de confianza para ejecutarse en el equipo de desarrollo al compilar el proyecto.  Para obtener más información, vea [Compilar soluciones de Office](../vsto/building-office-solutions.md).  
  
 Por motivos de seguridad, es mejor crear proyectos en el equipo local, en lugar de desarrollarlos en una ubicación compartida.  Para obtener más información, consulte [Desarrollo en colaboración de las soluciones de Office](../vsto/collaborative-development-of-office-solutions.md).  
  
## Ensamblados a los que se hace referencia  
 El ensamblado puede hacer referencia a otros ensamblados, que se enumeran en las referencias del proyecto.  Sin embargo, un ensamblado de proyecto de nivel de documento no puede hacer referencia a otro ensamblado de proyecto de nivel de documento.  
  
## Vea también  
 [Información general sobre las plantillas de Office Project](../vsto/office-project-templates-overview.md)   
 [Cómo: Crear proyectos de Office en Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)   
 [Proyectos de Office en el entorno de Visual Studio](../vsto/office-projects-in-the-visual-studio-environment.md)   
 [Propiedades de los proyectos de Office](../vsto/properties-in-office-projects.md)   
 [Ejecutar soluciones en diferentes versiones de Microsoft Office](../vsto/running-solutions-in-different-versions-of-microsoft-office.md)   
 [Cómo: Apuntar a las aplicaciones de Office mediante los ensamblados de interoperabilidad primarios](../vsto/how-to-target-office-applications-through-primary-interop-assemblies.md)   
 [Manifiestos de implementación y aplicación en soluciones de Office](../vsto/application-and-deployment-manifests-in-office-solutions.md)   
 [Cómo: Establecer la información de configuración para una solución de Office](../vsto/how-to-set-up-configuration-information-for-an-office-solution.md)   
 [Usar la funcionalidad de Office dentro de Visual Studio](../vsto/using-office-functionality-inside-of-visual-studio.md)   
 [Implementar una solución de Office](../vsto/deploying-an-office-solution.md)   
 [Tareas comunes en la programación de Office](../vsto/common-tasks-in-office-programming.md)   
 [Desarrollar soluciones de Office](../vsto/developing-office-solutions.md)   
 [Arquitectura de las soluciones de Office en Visual Studio](../vsto/architecture-of-office-solutions-in-visual-studio.md)  
  
  