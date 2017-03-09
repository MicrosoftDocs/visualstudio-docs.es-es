---
title: "Permisos de usuario y Visual Studio | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "privilegios administrativos"
  - "permisos"
  - "permisos de usuario"
  - "Visual Studio, permisos de usuario"
ms.assetid: 70485ed7-6342-41bf-8250-7a6826e21b98
caps.latest.revision: 14
caps.handback.revision: 14
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Permisos de usuario y Visual Studio
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Por motivos de seguridad, debe ejecutar Visual Studio como un usuario normal siempre que sea posible.  
  
> [!WARNING]
>  También debe asegurarse de no compilar, iniciar ni depurar ninguna solución de Visual Studio que no proceda de una persona o una ubicación de confianza.  
  
 Puede hacer casi todo en el IDE de Visual Studio como un usuario normal, pero, se necesitan permisos de administrador para completar las tareas siguientes:  
  
|Área|Tarea|Para obtener más información|  
|----------|-----------|----------------------------------|  
|Instalación|Instalar Visual Studio.|[Instalar Visual Studio](../Topic/Installing%20Visual%20Studio%202015.md)|  
||Actualizar desde una edición de evaluación de Visual Studio.|[Cómo: Actualizar de versiones de prueba de Visual Studio](../install/how-to-upgrade-from-a-trial-edition-of-visual-studio.md)|  
||Instalar, actualizar o quitar contenido de la Ayuda local.|[Instalar y administrar el contenido local](../ide/install-and-manage-local-content.md)|  
|Tipos de aplicación|Desarrollar soluciones para SharePoint 2010.|[Requisitos para desarrollar soluciones de SharePoint](/office-dev/office-dev/requirements-for-developing-sharepoint-solutions)|  
||Adquirir una licencia de desarrollador para la [!INCLUDE[win8_appstore_long](../debugger/includes/win8_appstore_long_md.md)].|[Obtención de una licencia de desarrollador \(aplicaciones de la Tienda\)](http://go.microsoft.com/fwlink/?LinkID=241313)|  
|Cuadro de herramientas|Agregar controles COM clásicos al **Cuadro de herramientas**.|[Usar el Cuadro de herramientas](../ide/using-the-toolbox.md)|  
|Complementos|Instalar y usar complementos escritos mediante COM clásico en el IDE.|[Crear complementos y asistentes](../Topic/Creating%20Add-ins%20and%20Wizards.md)|  
|Compilación|Utilizar eventos posteriores a la compilación que registran un componente.|[Descripción de los pasos de compilación personalizada y los eventos de compilación](/visual-cpp/ide/understanding-custom-build-steps-and-build-events)|  
||Incluir un paso de registro al compilar proyectos de C\+\+.|[Descripción de los pasos de compilación personalizada y los eventos de compilación](/visual-cpp/ide/understanding-custom-build-steps-and-build-events)|  
|Depuración|Depurar aplicaciones que se ejecutan con permisos elevados.|[Preparación y configuración de la depuración](../debugger/debugger-settings-and-preparation.md)|  
||Depurar aplicaciones que se ejecutan bajo una cuenta de usuario diferente, como sitios web ASP.NET.|[Depurar aplicaciones ASP.NET y aplicaciones habilitadas para AJAX](../debugger/debugging-aspnet-and-ajax-applications.md)|  
||Depuración en zona para Aplicaciones XAML del explorador \(XBAP\).|[WPF Host \(PresentationHost.exe\)](../Topic/WPF%20Host%20\(PresentationHost.exe\).md)|  
||Usar el emulador para depurar proyectos de servicios en la nube para Microsoft Azure.|[Depurar un servicio en la nube en Visual Studio](http://go.microsoft.com/fwlink/?LinkId=266725)|  
||Configurar un firewall para depuración remota.|[Configurar las herramientas remotas en el dispositivo](../Topic/Set%20Up%20the%20Remote%20Tools%20on%20the%20Device.md)|  
|Herramientas de rendimiento|Generar perfiles de una aplicación.|[Guía básica para la generación de perfiles de rendimiento](../profiling/beginners-guide-to-performance-profiling.md)|  
|Implementación|Implementar una aplicación web en Internet Information Services \(IIS\) en un equipo local.|[Implementar una aplicación web ASP.NET en un proveedor de hospedaje mediante Visual Studio or Visual Web Developer: implementar en IIS como un entorno de prueba](http://go.microsoft.com/fwlink/?LinkId=266478)|  
|Proporcionar comentarios a Microsoft|Cambiar cómo participar en el Programa para la mejora de la experiencia del usuario de Visual Studio.|[Cómo: Enviar comentarios](../misc/how-to-send-feedback-about-visual-studio.md)|  
  
## Ejecutar Visual Studio como administrador  
 Puede iniciar Visual Studio con permisos administrativos cada vez que inicie el IDE o puede modificar el acceso directo de la aplicación para que se ejecute siempre con permisos administrativos.  Para obtener más información, vea la Ayuda de Windows.  
  
#### Para ejecutar Visual Studio con permisos administrativos en [!INCLUDE[win8](../debugger/includes/win8_md.md)], [!INCLUDE[win81](../debugger/includes/win81_md.md)], [!INCLUDE[winserver8](../debugger/includes/winserver8_md.md)] o [!INCLUDE[winblue_server_2](../ide/includes/winblue_server_2_md.md)]  
  
1.  En la pantalla **Inicio**, escriba Visual Studio.  Debe ver la versión o las versiones de Visual Studio que ha instalado.  
  
2.  Seleccione la versión de Visual Studio que desea iniciar y, a continuación, abra el menú contextual \(aparece en la parte inferior de la pantalla\).  Elija **Ejecutar como administrador**.  
  
     Cuando se inicia Visual Studio, aparece **\(Administrador\)** después del nombre de producto en la barra de título.  
  
#### Para ejecutar Visual Studio con permisos administrativos en [!INCLUDE[win7](../debugger/includes/win7_md.md)] o [!INCLUDE[winsvr08_r2](../debugger/includes/winsvr08_r2_md.md)]  
  
1.  En el menú **Inicio**, elija **Todos los programas**.  
  
2.  En la carpeta **Microsoft Visual Studio**  *versión*, seleccione **Visual Studio** *versión*, abra el menú contextual y, a continuación, elija **Ejecutar como administrador**.  
  
     Cuando se inicia Visual Studio, aparece **\(Administrador\)** después del nombre de producto en la barra de título.  
  
## Vea también  
 [Portar, migrar y actualizar proyectos de Visual Studio](../porting/porting-migrating-and-upgrading-visual-studio-projects.md)   
 [Instalar Visual Studio](../Topic/Installing%20Visual%20Studio%202015.md)