---
title: Diseñar y crear soluciones de Office
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office solutions [Office development in Visual Studio], creating
- Office development in Visual Studio, creating solutions
- solutions [Office development in Visual Studio], creating
- Office project types in Visual Studio
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 05cf317823d4f5853d960109bd97da77ea8a927d
ms.sourcegitcommit: be938c7ecd756a11c9de3e6019a490d0e52b4190
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50671253"
---
# <a name="design-and-create-office-solutions"></a>Diseñar y crear soluciones de Office
  Visual Studio proporciona plantillas de proyecto que puede usar para crear varios tipos distintos de soluciones de Office. En esta sección de la documentación se describen las plantillas de proyecto y se ofrecen instrucciones sobre cómo crear proyectos de Office. Para obtener información sobre cómo implementar personalizaciones de la interfaz de usuario y código después de haber creado el proyecto, vea [soluciones de desarrollo de Office](../vsto/developing-office-solutions.md).  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
> [!NOTE]  
>  ¿Está interesado en desarrollar soluciones que amplían la experiencia de Office a través de [varias plataformas](https://dev.office.com/add-in-availability)? Visite el nuevo [modelo de complementos de Office](https://dev.office.com/docs/add-ins/overview/office-add-ins). Complementos de Office tienen una superficie pequeña en comparación con las soluciones y los complementos de VSTO, y puede crearlas con prácticamente cualquier tecnología, como HTML5, CSS3, JavaScript y XML de programación web.  
  
## <a name="create-office-projects"></a>Crear proyectos de Office  
 Antes de empezar, debe determinar los requisitos y el tipo de solución que mejor se adapta a sus necesidades. Por ejemplo, si su solución de Office debe ejecutarse cada vez que se utiliza la aplicación, un complemento de VSTO será lo que mejor se adapte a sus necesidades. Si el código está estrechamente integrado con un único documento, cree una personalización de nivel de documento. Estos tipos de proyecto están disponibles como plantillas de proyecto de Visual Studio. Para obtener más información acerca de las plantillas de proyecto de Office que se incluyen con Visual Studio, consulte [Introducción a las plantillas de proyecto de Office](../vsto/office-project-templates-overview.md). Para obtener más información sobre cómo crear proyectos de Office, consulte [Cómo: proyectos de creación de Office en Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
 Los proyectos de Office tienen características y elementos de proyecto que difieren de otros tipos de proyectos de Visual Studio. Por ejemplo, cuando se crea un proyecto de nivel de documento, el documento o el libro del proyecto se puede abrir y editar en Visual Studio. Para obtener más información, consulte [proyectos de Office en el entorno de Visual Studio](../vsto/office-projects-in-the-visual-studio-environment.md).  
  
## <a name="choose-a-net-framework-version"></a>Elegir una versión de .NET Framework  
 Después de seleccionar el tipo de proyecto que mejor se adapte a sus requisitos, puede elegir qué versión de .NET Framework se utilizará en el proceso de desarrollo. Puede elegir como destino las siguientes versiones de .NET Framework en los proyectos de Office:  
  
- [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]  
  
- [!INCLUDE[net_client_v40_long](../vsto/includes/net-client-v40-long-md.md)]  
  
- [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)]  
  
  Se requiere la versión de .NET Framework que elija para el proyecto en equipos de usuarios finales para ejecutar la solución. Por ejemplo, si el proyecto está destinado el [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)], el [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] es necesario en equipos de usuario final. En este ejemplo, la solución no se ejecutará si solo .NET Framework 3.5 está instalado en equipos de usuario final.  
  
  Si migra un proyecto de complemento de VSTO que tiene como destino .NET Framework 3.5, Visual Studio cambia la plataforma de destino del proyecto a [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] o a una versión posterior, según la versión de Office que haya instalado.  
  
  Sin embargo, una vez que Visual Studio cambie el marco de trabajo de destino, deberá modificar parte del código del proyecto si utiliza determinadas características. Para obtener más información sobre cómo cambiar la plataforma de destino, vea [Cómo: usar como destino una versión de .NET Framework](../ide/how-to-target-a-version-of-the-dotnet-framework.md). Para obtener más información acerca de los cambios que es posible que deba realizar en el proyecto, vea [soluciones de Office de migrar a .NET Framework 4 o posterior](../vsto/migrating-office-solutions-to-the-dotnet-framework-4-or-later.md).  
  
  Si Visual Studio cambia el destino es .NET Framework para el proyecto y usa ClickOnce para implementar la solución, asegúrese de que seleccione también la versión correspondiente de .NET Framework en el **requisitos previos** cuadro de diálogo. Esta selección no cambia automáticamente al cambiar la plataforma de destino del proyecto. Para obtener más información, consulte [Cómo: instalar requisitos previos en equipos de usuarios finales para ejecutar soluciones de Office](https://msdn.microsoft.com/74dd2c52-838f-4abf-b2b4-4d7b0c2a0a98).  
  
> [!NOTE]  
>  No podrá elegir como destino la versión .NET Framework 3.5 o alguna versión anterior en proyectos de Office que cree mediante [!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)]. Los proyectos de Office que cree mediante [!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)] requieren características que se introdujeron por primera vez en [!INCLUDE[net_client_v40_long](../vsto/includes/net-client-v40-long-md.md)].  
  
### <a name="understand-when-the-office-pias-are-required-on-end-user-computers"></a>Comprender cuándo se requieren los PIA de Office en equipos de usuario final  
 De forma predeterminada, los ensamblados de interoperabilidad primarios (PIA) de Office no es necesario para instalarse en equipos de usuario final si la **Embed Interop Types** propiedad de cada referencia de PIA de Office en el proyecto está establecida en **True**, que es el valor predeterminado. En este escenario, la información de tipo de los tipos de PIA que utiliza la solución se incrusta en el ensamblado de la solución al compilar el proyecto. En tiempo de ejecución, la información de tipo incrustada se usa en lugar de los PIA para llamar al modelo de objetos basado en COM de la aplicación de Office. Para obtener más información acerca de cómo se incrustan los tipos de PIA en la solución, vea [equivalencia de tipos y tipos de interoperabilidad incrustados](/dotnet/framework/interop/type-equivalence-and-embedded-interop-types).  
  
 Si el **Embed Interop Types** propiedad de cada referencia de PIA de Office en el proyecto está establecida en **False**, los PIA de Office debe estar instalados y registrados en la caché global de ensamblados en cada equipo del usuario final que ejecuta la solución. En la mayoría de los casos, los PIA se instalan de forma predeterminada con Office, pero también puede incluir el redistribuible de PIA como un requisito previo para una solución. Para obtener más información, consulte [requisitos previos de la solución de Office para implementación](https://msdn.microsoft.com/9f672809-43a3-40a1-9057-397ce3b5126e).  
  
### <a name="understand-the-client-profile"></a>Comprender el perfil de cliente  
 .NET Framework Client Profile constituye un subconjunto de funcionalidades de la versión completa de .NET Framework. Puede elegir como destino .NET Framework Client Profile si solo necesita utilizar las características de cliente de .NET Framework y desea proporcionar la experiencia de implementación más rápida posible para una solución de Office. Para obtener más información, consulte [perfil de cliente de .NET Framework](/dotnet/framework/deployment/client-profile).  
  
 Cuando crea un proyecto de Office que tiene como destino [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)], [!INCLUDE[net_client_v40_long](../vsto/includes/net-client-v40-long-md.md)] se establece como destino de forma predeterminada. Si desea desarrollar la solución para la versión completa de [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)], debe establecer esta opción después de crear el proyecto. Para obtener más información, consulte [Cómo: Usar como destino una versión de .NET Framework](../ide/how-to-target-a-version-of-the-dotnet-framework.md).  
  
## <a name="create-solutions-for-the-64-bit-edition-of-microsoft-office"></a>Crear soluciones para la edición de 64 bits de Microsoft Office  
 Microsoft Office está disponible en ediciones de 64 bits y 32 bits. Para crear soluciones de Office que se pueden ejecutar en ambas ediciones, la configuración de plataforma de destino para el proyecto debe establecerse en **cualquier CPU**. Este es el valor predeterminado para los proyectos de Office. Para obtener más información, consulte [soluciones de Office de compilación](../vsto/building-office-solutions.md).  
  
 Hay versiones independientes de 64 bits y 32 bits de [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] que utilizan las ediciones de 64 bits y 32 bits de Microsoft Office. Para obtener más información, consulte [Visual Studio Tools para Office runtime overview](../vsto/visual-studio-tools-for-office-runtime-overview.md).  
  
## <a name="assemblies-in-office-solutions"></a>Ensamblados en soluciones de Office  
 Al crear un proyecto de Office mediante las herramientas de desarrollo de Office en Visual Studio, el código que se escribe se compila finalmente en un ensamblado. El ensamblado se implementa en un servidor compartido o en un directorio en el equipo cliente.  
  
 Los ensamblados de las soluciones de Office se cargan a través de una aplicación de Office. Una vez cargado el ensamblado, el código del ensamblado puede responder a eventos que se produzcan en la aplicación, como, por ejemplo, cuando un usuario hace clic en un elemento de menú. El código del ensamblado también puede realizar llamadas en el modelo de objetos para automatizar y extender la aplicación, y utilizar cualquiera de las clases en [!INCLUDE[dnprdnshort](../sharepoint/includes/dnprdnshort-md.md)]. Para obtener más información, consulte [arquitectura de las personalizaciones de nivel de documento](../vsto/architecture-of-document-level-customizations.md) y [Architecture of VSTO Add-ins](../vsto/architecture-of-vsto-add-ins.md).  
  
 Las soluciones de Office usan manifiestos de implementación y de aplicación para identificar el ensamblado. Los manifiestos contienen información sobre el nombre, la versión y la ubicación del ensamblado, para que la aplicación pueda buscar y ejecutar el ensamblado adecuado, y establecer vínculos con este. Para obtener más información, consulte [los manifiestos de aplicación e implementación de soluciones de Office](../vsto/application-and-deployment-manifests-in-office-solutions.md).  
  
 Los proyectos de nivel de documento incluyen un documento además de un ensamblado. El documento actúa como el front-end de la aplicación y es donde se realiza toda la interacción del usuario. Cada documento solo puede tener un ensamblado de proyecto principal asociado a él. Sin embargo, varios documentos pueden apuntar al mismo ensamblado.  
  
 Los ensamblados en los proyectos de nivel de documento no se incrustan en el documento, sino que se almacenan en otra ubicación y se identifican mediante el manifiesto de aplicación del documento.  
  
## <a name="security-considerations-for-assemblies"></a>Consideraciones de seguridad para ensamblados  
 Para que una solución de Office se ejecute en un equipo y lo hagan también los ensamblados que esta usa, estos ensamblados deben ser de confianza. Para obtener más información acerca de la seguridad, consulte [soluciones de Office Secure](../vsto/securing-office-solutions.md).  
  
 De forma predeterminada, el ensamblado de la solución y los ensamblados a los que se hace referencia y que se encuentran en la carpeta de salida del proyecto son de confianza para ejecutarse en el equipo de desarrollo al compilar el proyecto. Para obtener más información, consulte [soluciones de Office de compilación](../vsto/building-office-solutions.md).  
  
 Por motivos de seguridad, es mejor crear proyectos en el equipo local, en lugar de desarrollarlos en una ubicación compartida. Para obtener más información, consulte [desarrollo en colaboración de las soluciones de Office](../vsto/collaborative-development-of-office-solutions.md).  
  
## <a name="referenced-assemblies"></a>Ensamblados a los que se hace referencia  
 El ensamblado puede hacer referencia a otros ensamblados, que se enumeran en las referencias del proyecto. Sin embargo, un ensamblado de proyecto de nivel de documento no puede hacer referencia a otro ensamblado de proyecto de nivel de documento.  
  
## <a name="see-also"></a>Vea también  
 [Introducción a las plantillas de proyecto de Office](../vsto/office-project-templates-overview.md)   
 [Cómo: crear proyectos de Office en Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)   
 [Proyectos de Office en el entorno de Visual Studio](../vsto/office-projects-in-the-visual-studio-environment.md)   
 [Propiedades de los proyectos de Office](../vsto/properties-in-office-projects.md)   
 [Ejecutar soluciones en diferentes versiones de Microsoft Office](../vsto/running-solutions-in-different-versions-of-microsoft-office.md)   
 [Cómo: las aplicaciones de Office de destino a través de los ensamblados de interoperabilidad primarios](../vsto/how-to-target-office-applications-through-primary-interop-assemblies.md)   
 [Manifiestos de aplicación e implementación de soluciones de Office](../vsto/application-and-deployment-manifests-in-office-solutions.md)   
 [Cómo: configurar la información de configuración para una solución de Office](../vsto/how-to-set-up-configuration-information-for-an-office-solution.md)   
 [Use la funcionalidad de Office en Visual Studio](../vsto/using-office-functionality-inside-of-visual-studio.md)   
 [Implementar una solución de Office](../vsto/deploying-an-office-solution.md)   
 [Tareas comunes en la programación de Office](../vsto/common-tasks-in-office-programming.md)   
 [Desarrollar soluciones de Office](../vsto/developing-office-solutions.md)   
 [Arquitectura de soluciones de Office en Visual Studio](../vsto/architecture-of-office-solutions-in-visual-studio.md)  
  
  