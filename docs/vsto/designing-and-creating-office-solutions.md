---
title: Diseñar y crear soluciones de Office
description: Obtenga información sobre cómo Visual Studio proporciona plantillas de proyecto que puede usar para crear varios tipos diferentes de soluciones de Office.
ms.custom: SEO-VS-2020
ms.date: 08/14/2019
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office solutions [Office development in Visual Studio], creating
- Office development in Visual Studio, creating solutions
- solutions [Office development in Visual Studio], creating
- Office project types in Visual Studio
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: df634a7c242819e4f41a6fddeae4099a3d25fae2
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99897637"
---
# <a name="design-and-create-office-solutions"></a>Diseñar y crear soluciones de Office

Visual Studio proporciona plantillas de proyecto que puede usar para crear varios tipos distintos de soluciones de Office. En esta sección de la documentación se describen las plantillas de proyecto y se ofrecen instrucciones sobre cómo crear proyectos de Office. Para obtener información sobre cómo implementar personalizaciones de código y de interfaz de usuario después de haber creado el proyecto, vea [desarrollar soluciones de Office](../vsto/developing-office-solutions.md).

[!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

[!include[Add-ins note](includes/addinsnote.md)]

## <a name="create-office-projects"></a>Crear proyectos de Office
 Antes de empezar, debe determinar los requisitos y el tipo de solución que mejor se adapta a sus necesidades. Por ejemplo, si su solución de Office debe ejecutarse cada vez que se utiliza la aplicación, un complemento de VSTO será lo que mejor se adapte a sus requisitos. Si el código está estrechamente integrado con un único documento, cree una personalización de nivel de documento. Estos tipos de proyecto están disponibles como plantillas de proyecto de Visual Studio. Para obtener más información sobre las plantillas de proyecto de Office que se incluyen con Visual Studio, vea [información general sobre las plantillas de proyecto de Office](../vsto/office-project-templates-overview.md). Para obtener más información sobre cómo crear proyectos de Office, vea [Cómo: crear proyectos de Office en Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

 Los proyectos de Office tienen características y elementos de proyecto que difieren de otros tipos de proyectos de Visual Studio. Por ejemplo, cuando se crea un proyecto de nivel de documento, el documento o el libro del proyecto se puede abrir y editar en Visual Studio. Para obtener más información, vea [proyectos de Office en el entorno de Visual Studio](../vsto/office-projects-in-the-visual-studio-environment.md).

## <a name="choose-a-net-framework-version"></a>Elegir una versión de .NET Framework
 Después de seleccionar el tipo de proyecto que mejor se adapte a sus requisitos, puede elegir qué versión de .NET Framework se utilizará en el proceso de desarrollo. Puede elegir como destino las siguientes versiones de .NET Framework en los proyectos de Office:

- [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]

- [!INCLUDE[net_client_v40_long](../vsto/includes/net-client-v40-long-md.md)]

- [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)]

  La versión de .NET Framework que elija para el proyecto es necesaria en los equipos de los usuarios finales para que la solución se ejecute. Por ejemplo, si el proyecto tiene como destino [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] , [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] es necesario en los equipos de los usuarios finales. En este ejemplo, la solución no se ejecutará si solo el .NET Framework 3,5 está instalado en los equipos de los usuarios finales.

  Si migra un proyecto de complemento de VSTO que tiene como destino .NET Framework 3.5, Visual Studio cambia el marco de trabajo de destino del proyecto a [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] o a una versión posterior, según la versión de Office que haya instalado.

  Sin embargo, una vez que Visual Studio cambie el marco de trabajo de destino, deberá modificar parte del código del proyecto si utiliza determinadas características. Para obtener más información sobre cómo cambiar la versión de .NET Framework de destino, consulte [How to: target a version of the .NET Framework](../ide/visual-studio-multi-targeting-overview.md). Para obtener más información sobre los cambios que es posible que deba realizar en el proyecto, vea [migrar soluciones de Office al .NET Framework 4 o posterior](../vsto/migrating-office-solutions-to-the-dotnet-framework-4-or-later.md).

  Si Visual Studio cambia el .NET Framework de destino del proyecto y usa ClickOnce para implementar la solución, asegúrese de que también selecciona la versión correspondiente del .NET Framework en el cuadro de diálogo **requisitos previos** . Esta selección no cambia automáticamente al cambiar la plataforma de destino del proyecto. Para obtener más información, consulte [Cómo: instalar los requisitos previos en los equipos de los usuarios finales para ejecutar soluciones de Office](/previous-versions/bb608608(v=vs.110)).

> [!NOTE]
> No podrá elegir como destino la versión .NET Framework 3.5 o alguna versión anterior en proyectos de Office que cree mediante [!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)]. Los proyectos de Office que cree mediante [!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)] requieren características que se introdujeron por primera vez en [!INCLUDE[net_client_v40_long](../vsto/includes/net-client-v40-long-md.md)].

### <a name="understand-when-the-office-pias-are-required-on-end-user-computers"></a>Saber cuándo se necesitan los PIA de Office en los equipos de los usuarios finales
 De forma predeterminada, no es necesario instalar los ensamblados de interoperabilidad primarios (PIA) de Office en los equipos de los usuarios finales si la propiedad **incrustar tipos de interoperabilidad** de cada referencia de Pia de Office en el proyecto está establecida en **true**, que es el valor predeterminado. En este escenario, la información de tipo de los tipos de PIA que utiliza la solución se incrusta en el ensamblado de la solución al compilar el proyecto. La información de tipo incrustada se usa en tiempo de ejecución en lugar de los PIA para llamar al modelo de objetos basado en COM de la aplicación de Office. Para obtener más información sobre cómo se incrustan los tipos de los PIA en la solución, vea equivalencia de tipos [y tipos de interoperabilidad incrustados](/dotnet/framework/interop/type-equivalence-and-embedded-interop-types).

 Si la propiedad **incrustar tipos de interoperabilidad** de cada referencia de Pia de Office en el proyecto está establecida en **false**, se deben instalar y registrar los PIA de Office en la caché global de ensamblados en cada equipo del usuario final que ejecute la solución. En la mayoría de los casos, los PIA se instalan de forma predeterminada con Office, pero también puede incluir el redistribuible de PIA como un requisito previo para una solución. Para obtener más información, consulte [requisitos previos de la solución de Office para la implementación](/previous-versions/bb608617(v=vs.110)).

### <a name="understand-the-client-profile"></a>Descripción del perfil de cliente
 .NET Framework Client Profile constituye un subconjunto de funcionalidades de la versión completa de .NET Framework. Puede elegir como destino .NET Framework Client Profile si solo necesita utilizar las características de cliente de .NET Framework y desea proporcionar la experiencia de implementación más rápida posible para una solución de Office. Para obtener más información, consulte [.NET Framework Client Profile](/dotnet/framework/deployment/client-profile).

 Cuando crea un proyecto de Office que tiene como destino [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)], [!INCLUDE[net_client_v40_long](../vsto/includes/net-client-v40-long-md.md)] se establece como destino de forma predeterminada. Si desea desarrollar todo [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] , debe establecer esta opción después de crear el proyecto. Para obtener más información, vea [Cómo: Usar una versión de .NET Framework como destino](../ide/visual-studio-multi-targeting-overview.md).

## <a name="create-solutions-for-the-64-bit-edition-of-microsoft-office"></a>Cree soluciones para la edición de 64 bits de Microsoft Office
 Microsoft Office está disponible en ediciones de 64 bits y 32 bits. Para crear soluciones de Office que se puedan ejecutar en cualquier edición, la configuración de destino de la plataforma para el proyecto debe establecerse en **cualquier CPU**. Este es el valor predeterminado para los proyectos de Office. Para obtener más información, vea [compilar soluciones de Office](../vsto/building-office-solutions.md).

 Hay versiones independientes de 64 bits y 32 bits de [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] que utilizan las ediciones de 64 bits y 32 bits de Microsoft Office. Para obtener más información, vea [información general de Visual Studio Tools para Office Runtime](../vsto/visual-studio-tools-for-office-runtime-overview.md).

## <a name="assemblies-in-office-solutions"></a>Ensamblados en soluciones de Office
 Al crear un proyecto de Office mediante las herramientas de desarrollo de Office en Visual Studio, el código que se escribe se compila finalmente en un ensamblado. El ensamblado se implementa en un servidor compartido o en un directorio en el equipo cliente.

 Los ensamblados de las soluciones de Office se cargan a través de una aplicación de Office. Una vez cargado el ensamblado, el código del ensamblado puede responder a eventos que se produzcan en la aplicación, como, por ejemplo, cuando un usuario hace clic en un elemento de menú. El código del ensamblado también puede realizar llamadas en el modelo de objetos para automatizar y extender la aplicación, y utilizar cualquiera de las clases en [!INCLUDE[dnprdnshort](../sharepoint/includes/dnprdnshort-md.md)]. Para obtener más información, vea [arquitectura de las personalizaciones de nivel de documento](../vsto/architecture-of-document-level-customizations.md) y [arquitectura de los complementos de VSTO](../vsto/architecture-of-vsto-add-ins.md).

 Las soluciones de Office usan manifiestos de implementación y de aplicación para identificar el ensamblado. Los manifiestos contienen información sobre el nombre, la versión y la ubicación del ensamblado, para que la aplicación pueda buscar y ejecutar el ensamblado adecuado, y establecer vínculos con este. Para obtener más información, vea [manifiestos de aplicación e implementación en soluciones de Office](../vsto/application-and-deployment-manifests-in-office-solutions.md).

 Los proyectos de nivel de documento incluyen un documento además de un ensamblado. El documento actúa como el front-end de la aplicación y es donde se realiza toda la interacción del usuario. Cada documento solo puede tener un ensamblado de proyecto principal asociado a él. Sin embargo, varios documentos pueden apuntar al mismo ensamblado.

 Los ensamblados en los proyectos de nivel de documento no se incrustan en el documento, sino que se almacenan en otra ubicación y se identifican mediante el manifiesto de aplicación del documento.

## <a name="security-considerations-for-assemblies"></a>Consideraciones de seguridad para ensamblados
 Para que una solución de Office se ejecute en un equipo y lo hagan también los ensamblados que esta usa, estos ensamblados deben ser de confianza. Para obtener más información acerca de la seguridad, consulte [protección de soluciones de Office](../vsto/securing-office-solutions.md).

 De forma predeterminada, el ensamblado de la solución y los ensamblados a los que se hace referencia y que se encuentran en la carpeta de salida del proyecto son de confianza para ejecutarse en el equipo de desarrollo al compilar el proyecto. Para obtener más información, vea [compilar soluciones de Office](../vsto/building-office-solutions.md).

 Por motivos de seguridad, es mejor crear proyectos en el equipo local, en lugar de desarrollarlos en una ubicación compartida. Para obtener más información, vea [desarrollo en colaboración de las soluciones de Office](../vsto/collaborative-development-of-office-solutions.md).

## <a name="referenced-assemblies"></a>Ensamblados a los que se hace referencia
 El ensamblado puede hacer referencia a otros ensamblados, que se enumeran en las referencias del proyecto. Sin embargo, un ensamblado de proyecto de nivel de documento no puede hacer referencia a otro ensamblado de proyecto de nivel de documento.

## <a name="see-also"></a>Vea también
- [Información general de plantillas de proyecto de Office](../vsto/office-project-templates-overview.md)
- [Cómo: crear proyectos de Office en Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)
- [Proyectos de Office en el entorno de Visual Studio](../vsto/office-projects-in-the-visual-studio-environment.md)
- [Propiedades de los proyectos de Office](../vsto/properties-in-office-projects.md)
- [Ejecutar soluciones en diferentes versiones de Microsoft Office](../vsto/running-solutions-in-different-versions-of-microsoft-office.md)
- [Cómo: dirigirse a aplicaciones de Office a través de ensamblados de interoperabilidad primarios](../vsto/how-to-target-office-applications-through-primary-interop-assemblies.md)
- [Manifiestos de implementación y aplicación en soluciones de Office](../vsto/application-and-deployment-manifests-in-office-solutions.md)
- [Cómo: configurar la información de configuración de una solución de Office](../vsto/how-to-set-up-configuration-information-for-an-office-solution.md)
- [Usar la funcionalidad de Office dentro de Visual Studio](../vsto/using-office-functionality-inside-of-visual-studio.md)
- [Implementar una solución de Office](../vsto/deploying-an-office-solution.md)
- [Tareas comunes en la programación de Office](../vsto/common-tasks-in-office-programming.md)
- [Desarrollo de soluciones de Office](../vsto/developing-office-solutions.md)
- [Arquitectura de las soluciones de Office en Visual Studio](../vsto/architecture-of-office-solutions-in-visual-studio.md)