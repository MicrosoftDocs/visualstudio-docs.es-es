---
title: "Página Depuración, Diseñador de proyectos | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vb.ProjectPropertiesDebug
helpviewer_keywords:
- Project Designer, Debug page
- Debug page in Project Designer
ms.assetid: ef11eae9-df96-4e20-aabd-2678ba317140
caps.latest.revision: "32"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: a16f39d9f9ba6c3e0790a53c85d0824178083953
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="debug-page-project-designer"></a>Página Depuración, Diseñador de proyectos
> [!WARNING]
>  Este tema no se aplica a las aplicaciones de UWP. Vea [Start a debug session (VB, C#, C++ and XAML)](../../debugger/start-a-debugging-session-for-a-store-app-in-visual-studio-vb-csharp-cpp-and-xaml.md) (Iniciar una sesión de depuración (VB, C#, C++ y XAML)) en el Centro de desarrollo de Windows.  
  
 Use la página **Depurar** del **Diseñador de proyectos** para establecer las propiedades del comportamiento de depuración en un proyecto de Visual Basic o C#.  
  
 Para obtener acceso a la página **Depurar**, seleccione un nodo de proyecto en el **Explorador de soluciones**. En el menú **Proyecto**, seleccione **Propiedades de** *NombreDelProyecto*. Cuando aparezca el **Diseñador de proyectos**, haga clic en la pestaña **Depurar**.  
  
## <a name="configuration-and-platform"></a>Configuración y plataforma  
 Las siguientes opciones le permiten seleccionar la configuración y la plataforma que se mostrarán o modificarán.  
  
 **Configuración**  
 Especifica qué opciones de configuración se mostrarán o modificarán. Los valores pueden ser **Depurar** (valor predeterminado), **Versión** o **Todas las configuraciones**. Para obtener más información, consulte [Configuraciones Debug y Release](http://msdn.microsoft.com/en-us/0440b300-0614-4511-901a-105b771b236e).  
  
 **Plataforma**  
 Especifica qué configuración de plataforma se mostrará o modificará. Entre las opciones se pueden incluir **Cualquier CPU** (valor predeterminado), **x64** y **x86**. Para obtener más información, consulte [Configuraciones Debug y Release](http://msdn.microsoft.com/en-us/0440b300-0614-4511-901a-105b771b236e).  
  
## <a name="start-action"></a>Acción de inicio  
 **Acción de inicio** indica el elemento que se iniciará cuando se depure la aplicación: el proyecto, un programa personalizado, una dirección URL o ninguno. De forma predeterminada, el valor de esta opción es **Iniciar proyecto**. El valor de **Acción de inicio** en la página **Depurar** determina el valor de la propiedad `StartAction`.  
  
 **Iniciar proyecto**  
 Elija esta opción para especificar que se debe iniciar el ejecutable (para los proyectos de aplicación de Windows y aplicación de consola) cuando se depure la aplicación. Esta opción está seleccionada de forma predeterminada.  
  
 **Iniciar programa externo**  
 Elija esta opción para especificar que se debe iniciar un programa específico cuando se depure la aplicación.  
  
 **Iniciar explorador con la dirección URL**  
 Elija esta opción para especificar que se debe tener acceso a una dirección URL específica cuando se depure la aplicación.  
  
## <a name="start-options"></a>Opciones de inicio  
 **Argumentos de la línea de comandos**  
 En este cuadro de texto, escriba los argumentos de la línea de comandos que se usarán para la depuración.  
  
 **Directorio de trabajo**  
 En este cuadro de texto, escriba el directorio desde el que se iniciará el proyecto. También puede hacer clic en el botón Examinar (**…**) para elegir un directorio.  
  
 **Usar máquina remota**  
 Para depurar la aplicación desde una máquina remota, active esta casilla y escriba la ruta de acceso al equipo remoto en el cuadro de texto.  
  
## <a name="enable-debuggers"></a>Habilitar depuradores  
 **Habilitar depuración de código no administrado**  
 Esta opción especifica si se admite la depuración de código nativo. Active esta casilla si va a realizar llamadas a objetos COM o si inicia un programa personalizado escrito en código nativo que llama al proyecto y debe depurar el código nativo. Desactive esta casilla para deshabilitar la depuración de código no administrado. Esta casilla está desactivada de forma predeterminada.  
  
 **Habilitar depuración de SQL Server**  
 Active o desactive esta casilla para habilitar o deshabilitar la depuración de procedimientos SQL desde la aplicación de Visual Basic. Esta casilla está desactivada de forma predeterminada.  
  
 **Habilitar el proceso de hospedaje de Visual Studio**  
 Active esta casilla para habilitar el proceso de hospedaje de Visual Studio. Esta casilla se encuentra activada de forma predeterminada. Para obtener más información, vea [Proceso de alojamiento (vshost.exe)](../../ide/hosting-process-vshost-exe.md).  
  
 Para depurar en una zona de seguridad, debe habilitar esta opción y **Depurar esta aplicación con el conjunto de permisos seleccionados** en el [cuadro de diálogo Configuración de seguridad avanzada](../../ide/reference/advanced-security-settings-dialog-box.md).  
  
## <a name="see-also"></a>Vea también  
 [Depurar en Visual Studio](../../debugger/debugging-in-visual-studio.md)   
 [Configuración de proyectos para configuraciones de depuración en C#](../../debugger/project-settings-for-csharp-debug-configurations.md)   
 [Configuración de proyectos para una configuración de depuración en Visual Basic](../../debugger/project-settings-for-a-visual-basic-debug-configuration.md)   
 [Administrar propiedades de depuración](http://msdn.microsoft.com/en-us/92474d16-e7fe-4fac-9287-6bd6b3a7eb68)   
 [Cómo: Depurar una aplicación ClickOnce con permisos restringidos](../../deployment/how-to-debug-a-clickonce-application-with-restricted-permissions.md)   
 [Cómo: Crear y editar configuraciones](../../ide/how-to-create-and-edit-configurations.md)