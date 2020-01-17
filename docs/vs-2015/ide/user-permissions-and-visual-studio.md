---
title: Establecimiento de permisos | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio, user permissions
- user permissions
- administrative privileges
- permissions
ms.assetid: 70485ed7-6342-41bf-8250-7a6826e21b98
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: aa01cb77e8a003438721984da13f46de350104ea
ms.sourcegitcommit: 939407118f978162a590379997cb33076c57a707
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 01/13/2020
ms.locfileid: "75918996"
---
# <a name="user-permissions-and-visual-studio"></a>Permisos de usuario y Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Por motivos de seguridad, debe ejecutar Visual Studio como un usuario normal siempre que sea posible.

> [!WARNING]
> También debe asegurarse de no compilar, iniciar ni depurar ninguna solución de Visual Studio que no proceda de una persona o una ubicación de confianza.

 Puede hacer casi todo en el IDE de Visual Studio como un usuario normal, pero, se necesitan permisos de administrador para completar las tareas siguientes:

|Área|Tarea|Para obtener más información|
|----------|----------|--------------------------|
|Instalación|Instalar Visual Studio.|[Instalación de Visual Studio 2015](../install/install-visual-studio-2015.md)|
||Actualizar desde una edición de evaluación de Visual Studio.|[Cómo: Actualizar a partir de una edición de prueba de Visual Studio](../install/how-to-upgrade-from-a-trial-edition-of-visual-studio.md)|
||Instalar, actualizar o quitar contenido de la Ayuda local.|[Instalar y administrar el contenido local](../ide/install-and-manage-local-content.md)|
|Tipos de aplicación|Desarrollar soluciones para SharePoint 2010.|[Requisitos para desarrollar soluciones de SharePoint](https://msdn.microsoft.com/library/ae8ff69d-4540-4380-ab0b-845f7108e89c)|
||Adquirir una licencia de desarrollador para la [!INCLUDE[win8_appstore_long](../includes/win8-appstore-long-md.md)].|[Obtener una licencia de desarrollador (aplicaciones de la Tienda Windows)](https://msdn.microsoft.com/library/windows/apps/hh974578.aspx)|
|Cuadro de herramientas|Agregar controles COM clásicos al **Cuadro de herramientas**.|[Usar el cuadro de herramientas](../ide/using-the-toolbox.md)|
|Complementos|Instalar y usar complementos escritos mediante COM clásico en el IDE.|[Crear complementos y asistentes](https://msdn.microsoft.com/library/c5a47c21-6668-4de3-898d-afa969317e73)|
|Compilación|Utilizar eventos posteriores a la compilación que registran un componente.|[Descripción de los pasos de compilación personalizada y los eventos de compilación](https://msdn.microsoft.com/library/beb2f017-3e9f-4b2c-9b57-2572fd2628e4)|
||Incluir un paso de registro al compilar proyectos de C++.|[Descripción de los pasos de compilación personalizada y los eventos de compilación](https://msdn.microsoft.com/library/beb2f017-3e9f-4b2c-9b57-2572fd2628e4)|
|Depuración|Depurar aplicaciones que se ejecutan con permisos elevados.|[Configuración y preparación de la depuración](../debugger/debugger-settings-and-preparation.md)|
||Depurar aplicaciones que se ejecutan bajo una cuenta de usuario diferente, como sitios web ASP.NET.|[Depurar aplicaciones de ASP.NET y AJAX](../debugger/debugging-aspnet-and-ajax-applications.md)|
||Depuración en zona para Aplicaciones XAML del explorador (XBAP).|[WPF Host (PresentationHost.exe)](https://msdn.microsoft.com/library/3215bfa1-722c-4ac8-a7c5-bdd02d30afbd)|
||Usar el emulador para depurar proyectos de servicios en la nube para Microsoft Azure.|[Depurar un servicio en la nube en Visual Studio](../azure/vs-azure-tools-debug-cloud-services-virtual-machines.md)|
||Configurar un firewall para depuración remota.|[Configurar las herramientas remotas en el dispositivo](https://msdn.microsoft.com/library/90f45630-0d26-4698-8c1f-63f85a12db9c)|
|Herramientas de rendimiento|Generar perfiles de una aplicación.|[Guía básica para la generación de perfiles de rendimiento](../profiling/beginners-guide-to-performance-profiling.md)|
|Implementación|Implementar una aplicación web en Internet Information Services (IIS) en un equipo local.|[Implementar una aplicación web ASP.NET en un proveedor de hospedaje mediante Visual Studio o Visual Web Developer: Implementación en IIS como entorno de prueba](https://www.asp.net/web-forms/tutorials/deployment/deployment-to-a-hosting-provider/Deployment-to-a-Hosting-Provider-Deploying-to-IIS-as-a-Test-Environment-5-of-12)|
|Proporcionar comentarios a Microsoft|Cambiar cómo participar en el Programa para la mejora de la experiencia del usuario de Visual Studio.|[Cómo: enviar comentarios](../misc/how-to-send-feedback-about-visual-studio.md)|

## <a name="running-visual-studio-as-an-administrator"></a>Ejecutar Visual Studio como administrador
 Puede iniciar Visual Studio con permisos administrativos cada vez que inicie el IDE o puede modificar el acceso directo de la aplicación para que se ejecute siempre con permisos administrativos. Para obtener más información, vea la Ayuda de Windows.

#### <a name="to-run-visual-studio-with-administrative-permissions-on-includewin8includeswin8-mdmd-includewin81includeswin81-mdmd-includewinserver8includeswinserver8-mdmd-or-includewinblue_server_2includeswinblue-server-2-mdmd"></a>Para ejecutar Visual Studio con permisos administrativos en [!INCLUDE[win8](../includes/win8-md.md)], [!INCLUDE[win81](../includes/win81-md.md)], [!INCLUDE[winserver8](../includes/winserver8-md.md)] o [!INCLUDE[winblue_server_2](../includes/winblue-server-2-md.md)]

1. En la pantalla **Inicio**, escriba **Visual Studio**. Debe ver la versión o las versiones de Visual Studio que ha instalado.

2. Seleccione la versión de Visual Studio que desea iniciar y, a continuación, abra el menú contextual (aparece en la parte inferior de la pantalla). Elija **Ejecutar como administrador**.

     Cuando se inicia Visual Studio, aparece **(Administrador)** después del nombre de producto en la barra de título.

#### <a name="to-run-visual-studio-with-administrative-permissions-on-includewin7includeswin7-mdmd-or-includewinsvr08_r2includeswinsvr08-r2-mdmd"></a>Para ejecutar Visual Studio con permisos administrativos en [!INCLUDE[win7](../includes/win7-md.md)] o [!INCLUDE[winsvr08_r2](../includes/winsvr08-r2-md.md)]

1. En el menú **Inicio**, elija **Todos los programas**.

2. En la carpeta **Microsoft Visual Studio** *Versión*, seleccione **Visual Studio** *Version*, abra el menú contextual y, luego, elija **Ejecutar como administrador**.

     Cuando se inicia Visual Studio, aparece **(Administrador)** después del nombre de producto en la barra de título.

## <a name="see-also"></a>Vea también
 [Portar, migrar y actualizar proyectos de Visual Studio](../porting/porting-migrating-and-upgrading-visual-studio-projects.md) [Instalación de Visual Studio 2015](../install/install-visual-studio-2015.md)
