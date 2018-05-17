---
title: Permisos de usuario y Visual Studio
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio, user permissions
- user permissions
- administrative privileges
- permissions
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 08b12e09348a28276d0c5d2f375b26e75c1ac3c5
ms.sourcegitcommit: 56018fb1f52f17bf35ae2ce71c50c763486e6173
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="user-permissions-and-visual-studio"></a>Permisos de usuario y Visual Studio

Por motivos de seguridad, debe ejecutar Visual Studio como un usuario normal siempre que sea posible.

> [!WARNING]
> También debe asegurarse de no compilar, iniciar ni depurar ninguna solución de Visual Studio que no proceda de una persona o una ubicación de confianza.

Puede hacer casi todo en el IDE de Visual Studio como un usuario normal, pero, se necesitan permisos de administrador para completar las tareas siguientes:

|Área|Tarea|Para obtener más información|
|----------|----------|--------------------------|
|Instalación|Instalar Visual Studio.|[Instalar Visual Studio](../install/install-visual-studio.md)|
||Instalar, actualizar o quitar contenido de la Ayuda local.|[Instalar y administrar el contenido local](../ide/install-and-manage-local-content.md)|
|Tipos de aplicación|Desarrollar soluciones para SharePoint.|[Requisitos para desarrollar soluciones de SharePoint](../sharepoint/requirements-for-developing-sharepoint-solutions.md)|  
||Adquirir una licencia de desarrollador para la [!INCLUDE[win8_appstore_long](../debugger/includes/win8_appstore_long_md.md)].|[Obtener una licencia de desarrollador](http://go.microsoft.com/fwlink/?LinkID=241313)|
|Cuadro de herramientas|Agregar controles COM clásicos al **Cuadro de herramientas**.|[Cuadro de herramientas](../ide/reference/toolbox.md)|
|Complementos|Instalar y usar complementos escritos mediante COM clásico en el IDE.|[Crear complementos y asistentes](http://msdn.microsoft.com/Library/c5a47c21-6668-4de3-898d-afa969317e73)|
|Compilación|Utilizar eventos posteriores a la compilación que registran un componente.|[Descripción de los pasos de compilación personalizada y los eventos de compilación](/cpp/ide/understanding-custom-build-steps-and-build-events)|
||Incluir un paso de registro al compilar proyectos de C++.|[Descripción de los pasos de compilación personalizada y los eventos de compilación](/cpp/ide/understanding-custom-build-steps-and-build-events)|
|Depuración|Depurar aplicaciones que se ejecutan con permisos elevados.|[Preparación y configuración del depurador](../debugger/debugger-settings-and-preparation.md)|
||Depurar aplicaciones que se ejecutan bajo una cuenta de usuario diferente, como sitios web ASP.NET.|[Depuración de aplicaciones de ASP.NET y AJAX](../debugger/debugging-aspnet-and-ajax-applications.md)|
||Depuración en zona para Aplicaciones XAML del explorador (XBAP).|[WPF Host (PresentationHost.exe)](/dotnet/framework/wpf/app-development/wpf-host-presentationhost-exe)|
||Usar el emulador para depurar proyectos de servicios en la nube para Microsoft Azure.|[Depurar un servicio en la nube en Visual Studio](http://go.microsoft.com/fwlink/?LinkId=266725)|
||Configurar un firewall para depuración remota.|[Depuración remota](../debugger/remote-debugging.md)|
|Herramientas de rendimiento|Generar perfiles de una aplicación.|[Guía básica para la generación de perfiles de rendimiento](../profiling/beginners-guide-to-performance-profiling.md)|
|Implementación|Implementar una aplicación web en Internet Information Services (IIS) en un equipo local.|[Deploy an ASP.NET Web Application to a hosting provider using Visual Studio or Visual Web Developer: Deploy to IIS as a test environment](http://go.microsoft.com/fwlink/?LinkId=266478) (Implementar una aplicación web ASP.NET en un proveedor de host mediante Visual Studio o Visual Web Developer: implementar en IIS como entorno de prueba)|
>>>>>>> 346075117af3d2bd1fddd9c3aca24516a39fa6a3

## <a name="run-visual-studio-as-an-administrator"></a>Ejecutar Visual Studio como administrador

Puede iniciar Visual Studio con permisos administrativos cada vez que inicie el IDE o puede modificar el acceso directo de la aplicación para que se ejecute siempre con permisos administrativos. Para obtener más información, vea la Ayuda de Windows.

### <a name="run-visual-studio-with-administrative-permissions"></a>Ejecutar Visual Studio con permisos administrativos

Estas instrucciones corresponden a Windows 10. Son similares para otras versiones de Windows.

1. Abra el menú **Inicio** y desplácese hasta Visual Studio 2017.

1. En el menú contextual o que aparece al hacer clic con el botón derecho de **Visual Studio 2017**, seleccione **Más** > **Ejecutar como administrador**.

     Cuando se inicia Visual Studio, aparece **(Administrador)** después del nombre de producto en la barra de título.

## <a name="see-also"></a>Vea también

- [Portar, migrar y actualizar proyectos de Visual Studio](../porting/port-migrate-and-upgrade-visual-studio-projects.md)
- [Instalar Visual Studio](../install/install-visual-studio.md)