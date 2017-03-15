---
title: "P&#225;gina Depuraci&#243;n, Dise&#241;ador de proyectos | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vb.ProjectPropertiesDebug"
helpviewer_keywords: 
  - "Diseñador de proyectos, página Depuración"
  - "Página Depuración del Diseñador de proyectos"
ms.assetid: ef11eae9-df96-4e20-aabd-2678ba317140
caps.latest.revision: 32
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 32
---
# P&#225;gina Depuraci&#243;n, Dise&#241;ador de proyectos
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

> [!WARNING]
>  Este tema no se aplica a las aplicaciones del almacén de Windows.  Vea [Iniciar una sesión de depuración \(VB, C\#, C\+\+ y XAML\)](../../debugger/start-a-debugging-session-for-a-store-app-in-visual-studio-vb-csharp-cpp-and-xaml.md) en el Centro de desarrollo de Windows.  
  
 Utilice la página **DepurarDiseñador de proyectos** para establecer las propiedades para depurar el comportamiento en un proyecto de Visual Basic o C\#.  
  
 Para tener acceso a la página **Depurar** , seleccione un nodo de proyecto en **Explorador de soluciones**.  En el menú **Proyecto** , elija *NombreDelProyecto***Propiedades**.  Cuando aparezca **Diseñador de proyectos** , haga clic en la pestaña **Depurar** .  
  
## Configuración y plataforma  
 Las opciones siguientes permiten seleccionar la configuración y la plataforma que se van a mostrar o modificar.  
  
 **Configuración**  
 Especifica qué opciones de configuración se van a mostrar o modificar.  Los valores pueden ser **Depurar** \(valor predeterminado\), **Liberar**, o **Todas las config.** Para obtener más información, vea [Debug and Release Project Configurations](http://msdn.microsoft.com/es-es/0440b300-0614-4511-901a-105b771b236e).  
  
 **Plataforma**  
 Especifica qué opciones de plataforma se van a mostrar o modificar.  Las opciones pueden incluir **cualquier CPU** \(valor predeterminado\), **x64**, y **x86**.  Para obtener más información, vea [Debug and Release Project Configurations](http://msdn.microsoft.com/es-es/0440b300-0614-4511-901a-105b771b236e).  
  
## Acción de inicio  
 **Acción de inicio** indica el elemento que se debe iniciar cuando se depure la aplicación: el proyecto, un programa personalizado, una dirección URL o nada.  De forma predeterminada, esta opción se establece en **Proyecto de inicio**.  **Acción de inicio** Que establece en la página **Depurar** determina el valor de la propiedad de `StartAction` .  
  
 **Iniciar proyecto**  
 Elija esta opción para especificar que el archivo ejecutable \(para los proyectos de aplicación Windows y de aplicación de consola\) debe iniciar cuando se depure la aplicación.  Esta opción está seleccionada de forma predeterminada.  
  
 **Iniciar programa externo**  
 Elija esta opción para especificar que se debe iniciar un programa concreto cuando se depure la aplicación.  
  
 **Inicie el explorador con una dirección URL**  
 Elija esta opción para especificar que una dirección URL determinada debe tener acceso cuando se depure la aplicación.  
  
## Opciones de inicio  
 **Argumentos de la línea de comandos**  
 En este cuadro de texto, escriba los argumentos de la línea de comandos que se van a utilizar para la depuración.  
  
 **Directorio de trabajo**  
 En este cuadro de texto, escriba el directorio desde el que se iniciará el proyecto.  O haga clic en el botón Examinar \(**...**\) para elegir un directorio.  
  
 **Usar equipo remoto**  
 Para depurar la aplicación de un equipo remoto, active esta casilla, y escriba en la ruta de acceso al equipo remoto en el cuadro de texto.  
  
## Habilitar depuradores  
 **Habilitar depuración de código no administrado**  
 Esta opción especifica si se admite la depuración de código nativo.  Active esta casilla si va a realizar llamadas a objetos COM o si inicia un programa personalizado escrito en código nativo que llama al proyecto y debe depurar el código nativo.  Desactive esta casilla para deshabilitar la depuración de código no administrado.  Esta casilla está desactivada de forma predeterminada.  
  
 **Habilitar depuración de SQL Server**  
 Active o desactive esta casilla para habilitar o deshabilitar la depuración de los procedimientos de SQL de la aplicación de Visual Basic.  Esta casilla está desactivada de forma predeterminada.  
  
 **Habilitar el proceso de hospedaje de Visual Studio**  
 Active esta casilla para habilitar el proceso de hospedaje de Visual Studio.  Esta casilla se encuentra activada de forma predeterminada.  Para obtener más información, vea [Proceso de alojamiento \(vshost.exe\)](../../ide/hosting-process-vshost-exe.md).  
  
 Para depurar en una zona de seguridad, debe permitir a esta opción y **Depurar esta aplicación con el conjunto de permisos seleccionados** en [Configuración de seguridad avanzada \(Cuadro de diálogo\)](../../ide/reference/advanced-security-settings-dialog-box.md).  
  
## Vea también  
 [Depurar en Visual Studio](../../debugger/debugging-in-visual-studio.md)   
 [Configuración del proyecto para configuraciones de depuración en C\#](../../debugger/project-settings-for-csharp-debug-configurations.md)   
 [Configuración del proyecto para una configuración de depuración de Visual Basic](../../debugger/project-settings-for-a-visual-basic-debug-configuration.md)   
 [Managing Debugging Properties](http://msdn.microsoft.com/es-es/92474d16-e7fe-4fac-9287-6bd6b3a7eb68)   
 [Cómo: Depurar una aplicación ClickOnce con permisos restringidos](../../deployment/how-to-debug-a-clickonce-application-with-restricted-permissions.md)   
 [Cómo: Crear y editar configuraciones](../../ide/how-to-create-and-edit-configurations.md)