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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 0d8ba826e332141a3ee53a70185f0e8e18e465f4
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "63443218"
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
||Actualizar desde una edición de evaluación de Visual Studio.|[Cómo: Actualizar desde una edición de prueba de Visual Studio](../install/how-to-upgrade-from-a-trial-edition-of-visual-studio.md)|
||Instalar, actualizar o quitar contenido de la Ayuda local.|[Instalar y administrar el contenido local](../ide/install-and-manage-local-content.md)|
|Tipos de aplicación|Desarrollar soluciones para SharePoint 2010.|[Requisitos para desarrollar soluciones de SharePoint](http://msdn.microsoft.com/library/ae8ff69d-4540-4380-ab0b-845f7108e89c)|
||Adquirir una licencia de desarrollador para la [!INCLUDE[win8_appstore_long](../includes/win8-appstore-long-md.md)].|[Obtener una licencia de desarrollador (aplicaciones de la Tienda Windows)](http://go.microsoft.com/fwlink/?LinkID=241313)|
|Cuadro de herramientas|Agregar controles COM clásicos al **Cuadro de herramientas**.|[Usar el cuadro de herramientas](../ide/using-the-toolbox.md)|
|Complementos|Instalar y usar complementos escritos mediante COM clásico en el IDE.|[Crear complementos y asistentes](http://msdn.microsoft.com/library/c5a47c21-6668-4de3-898d-afa969317e73)|
|Compilación|Utilizar eventos posteriores a la compilación que registran un componente.|[Descripción de los pasos de compilación personalizada y los eventos de compilación](http://msdn.microsoft.com/library/beb2f017-3e9f-4b2c-9b57-2572fd2628e4)|
||Incluir un paso de registro al compilar proyectos de C++.|[Descripción de los pasos de compilación personalizada y los eventos de compilación](http://msdn.microsoft.com/library/beb2f017-3e9f-4b2c-9b57-2572fd2628e4)|
|Depuración|Depurar aplicaciones que se ejecutan con permisos elevados.|[Configuración y preparación de la depuración](../debugger/debugger-settings-and-preparation.md)|
||Depurar aplicaciones que se ejecutan bajo una cuenta de usuario diferente, como sitios web ASP.NET.|[Depurar aplicaciones de ASP.NET y AJAX](../debugger/debugging-aspnet-and-ajax-applications.md)|
||Depuración en zona para Aplicaciones XAML del explorador (XBAP).|[WPF Host (PresentationHost.exe)](http://msdn.microsoft.com/library/3215bfa1-722c-4ac8-a7c5-bdd02d30afbd)|
||Usar el emulador para depurar proyectos de servicios en la nube para Microsoft Azure.|[Depurar un servicio en la nube en Visual Studio](http://go.microsoft.com/fwlink/?LinkId=266725)|
||Configurar un firewall para depuración remota.|[Configurar las herramientas remotas en el dispositivo](http://msdn.microsoft.com/library/90f45630-0d26-4698-8c1f-63f85a12db9c)|
|Herramientas de rendimiento|Generar perfiles de una aplicación.|[Guía básica para la generación de perfiles de rendimiento](../profiling/beginners-guide-to-performance-profiling.md)|
|Implementación|Implementar una aplicación web en Internet Information Services (IIS) en un equipo local.|[Deploying an ASP.NET Web Application to a Hosting Provider using Visual Studio or Visual Web Developer: Deploying to IIS as a Test Environment](http://go.microsoft.com/fwlink/?LinkId=266478) (Implementar una aplicación web ASP.NET en un proveedor de host mediante Visual Studio o Visual Web Developer: implementar en IIS como entorno de prueba)|
|Proporcionar comentarios a Microsoft|Cambiar cómo participar en el Programa para la mejora de la experiencia del usuario de Visual Studio.|[Cómo: Enviar comentarios](../misc/how-to-send-feedback-about-visual-studio.md)|

## <a name="running-visual-studio-as-an-administrator"></a>Ejecutar Visual Studio como administrador
 Puede iniciar Visual Studio con permisos administrativos cada vez que inicie el IDE o puede modificar el acceso directo de la aplicación para que se ejecute siempre con permisos administrativos. Para obtener más información, vea la Ayuda de Windows.

#### <a name="to-run-visual-studio-with-administrative-permissions-on-includewin8includeswin8-mdmd-includewin81includeswin81-mdmd-includewinserver8includeswinserver8-mdmd-or-includewinblueserver2includeswinblue-server-2-mdmd"></a>Para ejecutar Visual Studio con permisos administrativos en [!INCLUDE[win8](../includes/win8-md.md)], [!INCLUDE[win81](../includes/win81-md.md)], [!INCLUDE[winserver8](../includes/winserver8-md.md)] o [!INCLUDE[winblue_server_2](../includes/winblue-server-2-md.md)]

1. En la pantalla **Inicio**, escriba **Visual Studio**. Debe ver la versión o las versiones de Visual Studio que ha instalado.

2. Seleccione la versión de Visual Studio que desea iniciar y, a continuación, abra el menú contextual (aparece en la parte inferior de la pantalla). Elija **Ejecutar como administrador**.

     Cuando se inicia Visual Studio, aparece **(Administrador)** después del nombre de producto en la barra de título.

#### <a name="to-run-visual-studio-with-administrative-permissions-on-includewin7includeswin7-mdmd-or-includewinsvr08r2includeswinsvr08-r2-mdmd"></a>Para ejecutar Visual Studio con permisos administrativos en [!INCLUDE[win7](../includes/win7-md.md)] o [!INCLUDE[winsvr08_r2](../includes/winsvr08-r2-md.md)]

1. En el menú **Inicio**, elija **Todos los programas**.

2. En la carpeta **Microsoft Visual Studio** *versión*, seleccione **Visual Studio** *versión*, abra el menú contextual y después elija **Ejecutar como administrador**.

     Cuando se inicia Visual Studio, aparece **(Administrador)** después del nombre de producto en la barra de título.

## <a name="see-also"></a>Vea también
 [Portar, migrar y actualizar proyectos de Visual Studio](../porting/porting-migrating-and-upgrading-visual-studio-projects.md) [Instalar Visual Studio 2015](../install/install-visual-studio-2015.md)
