---
title: Página Depuración, Diseñador de proyectos
ms.date: 06/27/2018
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vb.ProjectPropertiesDebug
helpviewer_keywords:
- Project Designer, Debug page
- Debug page in Project Designer
ms.assetid: ef11eae9-df96-4e20-aabd-2678ba317140
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a2c3e7813e5e07a0fbb8f4ebf5838c883faa0fb8
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/18/2020
ms.locfileid: "75595727"
---
# <a name="debug-page-project-designer"></a>Página Depuración, Diseñador de proyectos

Use la página **Depurar** del **Diseñador de proyectos** para establecer las propiedades del comportamiento de depuración en un proyecto de Visual Basic o C#.

Para obtener acceso a la página **Depurar**, seleccione un nodo de proyecto en el **Explorador de soluciones**. En el menú **Proyecto**, seleccione **\<NombreDeProyecto > Propiedades**. Cuando aparezca el **Diseñador de proyectos**, haga clic en la pestaña **Depurar**.

> [!NOTE]
> Este tema no se aplica a las aplicaciones de UWP. Vea [Iniciar una sesión de depuración (VB, C#, C++ y XAML)](../../debugger/start-a-debugging-session-for-a-store-app-in-visual-studio-vb-csharp-cpp-and-xaml.md) para aplicaciones UWP.

## <a name="configuration-and-platform"></a>Configuración y plataforma

Las siguientes opciones le permiten seleccionar la configuración y la plataforma que se mostrarán o modificarán.

**Configuración**

Especifica qué opciones de configuración se mostrarán o modificarán. Los valores pueden ser **Depurar** (valor predeterminado), **Versión** o **Todas las configuraciones**.

**Plataforma**

Especifica qué configuración de plataforma se mostrará o modificará. Entre las opciones se pueden incluir **Cualquier CPU** (valor predeterminado), **x64** y **x86**.

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

En este cuadro de texto, escriba el directorio desde el que se iniciará el proyecto. También puede hacer clic en el botón Examinar ( **…** ) para elegir un directorio.

**Usar máquina remota**

Para depurar la aplicación desde una máquina remota, active esta casilla y escriba la ruta de acceso al equipo remoto en el cuadro de texto.

## <a name="debugger-engines"></a>Motores de depuración

**Habilitar depuración de código nativo**

Esta opción especifica si se admite la depuración de código nativo. Active esta casilla si va a realizar llamadas a objetos COM o si inicia un programa personalizado escrito en código nativo que llama al proyecto y debe depurar el código nativo. Desactive esta casilla para deshabilitar la depuración de código no administrado. Esta casilla está desactivada de forma predeterminada.

**Habilitar depuración de SQL Server**

Active o desactive esta casilla para habilitar o deshabilitar la depuración de procedimientos SQL desde la aplicación de Visual Basic. Esta casilla está desactivada de forma predeterminada.

## <a name="see-also"></a>Vea también

- [Primer vistazo al depurador](../../debugger/debugger-feature-tour.md)
- [Configuración del proyecto para configuraciones de depuración en C#](../../debugger/project-settings-for-csharp-debug-configurations.md)
- [Configuración del proyecto para una configuración de depuración de Visual Basic](../../debugger/project-settings-for-a-visual-basic-debug-configuration.md)
- [Cómo: Depurar una aplicación ClickOnce con permisos restringidos](../../deployment/how-to-debug-a-clickonce-application-with-restricted-permissions.md)
- [Cómo: Crear y editar configuraciones](../../ide/how-to-create-and-edit-configurations.md)
