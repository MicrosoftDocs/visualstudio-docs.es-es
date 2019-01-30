---
title: Ejecutar como administrador
ms.date: 06/05/2018
ms.prod: visual-studio-dev15
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio, user permissions
- user permissions
- administrative privileges
- permissions
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 09fe84a9cd48f85ffac1f98b9300e1bdbad96ade
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/25/2019
ms.locfileid: "55012201"
---
# <a name="user-permissions-and-visual-studio"></a>Permisos de usuario y Visual Studio

Por motivos de seguridad, debe ejecutar Visual Studio como un usuario normal siempre que sea posible.

> [!WARNING]
> También debe asegurarse de no compilar, iniciar ni depurar ninguna solución de Visual Studio que no proceda de una persona o una ubicación de confianza.

En el IDE de Visual Studio puede hacerlo prácticamente todo como un usuario normal. Necesita permisos de administrador para completar las tareas siguientes:

|Área|Tarea|Para obtener más información|
|----------|----------| - |
|Instalación|Instalar Visual Studio.|[Instalar Visual Studio](../install/install-visual-studio.md)|
||Instalar, actualizar o quitar contenido local de Ayuda.|[Instalar y administrar el contenido local de Ayuda](../help-viewer/install-manage-local-content.md)|
|Cuadro de herramientas|Agregar controles COM clásicos al **Cuadro de herramientas**.|[Cuadro de herramientas](../ide/reference/toolbox.md)|
|Compilación|Utilizar eventos posteriores a la compilación que registran un componente.|[Descripción de los pasos de compilación personalizada y los eventos de compilación](/cpp/ide/understanding-custom-build-steps-and-build-events)|
||Incluir un paso de registro al compilar proyectos de C++.||
|Depuración|Depurar aplicaciones que se ejecutan con permisos elevados.|[Preparación y configuración del depurador](../debugger/debugger-settings-and-preparation.md)|
||Depurar aplicaciones que se ejecutan bajo una cuenta de usuario diferente, como sitios web ASP.NET.|[Depuración de aplicaciones de ASP.NET y AJAX](../debugger/how-to-enable-debugging-for-aspnet-applications.md)|
||Depurar en zona para Aplicaciones XAML del explorador (XBAP).|[WPF Host (PresentationHost.exe)](/dotnet/framework/wpf/app-development/wpf-host-presentationhost-exe)|
||Usar el emulador para depurar proyectos de servicios en la nube para Microsoft Azure.|[Depurar un servicio en la nube en Visual Studio](/azure/vs-azure-tools-debug-cloud-services-virtual-machines)|
||Configurar firewall para depuración remota.|[Depuración remota](../debugger/remote-debugging.md)|
|Herramientas de rendimiento|Generar perfiles de una aplicación.|[Guía básica para la generación de perfiles de rendimiento](../profiling/beginners-guide-to-performance-profiling.md)|
|Implementación|Implementar una aplicación web en Internet Information Services (IIS) en un equipo local.|[Implementación de una aplicación web de ASP.NET con Visual Studio](/aspnet/web-forms/overview/older-versions-getting-started/deployment-to-a-hosting-provider/)|

## <a name="run-visual-studio-as-an-administrator"></a>Ejecutar Visual Studio como administrador

Si tiene que ejecutar Visual Studio como administrador, siga estos pasos para abrir el IDE:

> [!NOTE]
> Estas instrucciones corresponden a Windows 10. Son similares para otras versiones de Windows.

1. Abra el menú **Inicio** y desplácese hasta Visual Studio 2017.

1. En el menú contextual o que aparece al hacer clic con el botón derecho de **Visual Studio 2017**, seleccione **Más** > **Ejecutar como administrador**.

   Cuando se inicia Visual Studio, aparece **(Administrador)** después del nombre de producto en la barra de título.

También puede modificar el acceso directo a la aplicación para ejecutarla siempre con permisos administrativos.

## <a name="see-also"></a>Vea también

- [Portar, migrar y actualizar proyectos de Visual Studio](../porting/port-migrate-and-upgrade-visual-studio-projects.md)
- [Instalar Visual Studio](../install/install-visual-studio.md)