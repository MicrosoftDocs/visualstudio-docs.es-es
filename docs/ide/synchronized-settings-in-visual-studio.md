---
title: Sincronizar la configuración
ms.date: 01/23/2017
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- VS.ToolsOptionsPages.Environment.RoamingSettings
ms.assetid: a3d2ea29-be5d-4012-9820-44b06adbb7dd
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 633767e66a4b3d976999574c885a3e6f7a06ddcf
ms.sourcegitcommit: 4cd4aef53e7035d23e7d1d0f66f51ac8480622a1
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/05/2018
ms.locfileid: "34766134"
---
# <a name="synchronize-visual-studio-settings-across-multiple-computers"></a>Sincronizar la configuración de Visual Studio en varios equipos

Al iniciar sesión en Visual Studio en varios equipos con la misma cuenta de personalización, se puede sincronizar la configuración entre todos los equipos.

## <a name="synchronized-settings"></a>Configuración sincronizada

De forma predeterminada, se sincroniza la configuración siguiente:

- Configuración de desarrollo. Tendrá que seleccionar un conjunto de opciones la primera vez que ejecute Visual Studio, aunque puede cambiar la selección en cualquier momento. Para más información, vea [Personalizar el IDE de Visual Studio](../ide/personalizing-the-visual-studio-ide.md).

- Los alias de comandos definidos por el usuario. Para obtener más información sobre cómo se definen los alias de comandos, consulte [Alias de comandos de Visual Studio](../ide/reference/visual-studio-command-aliases.md).

- Diseños de ventana definidos por el usuario en la página **Ventana** > **Administrar diseños de ventana**.

- Las siguientes opciones en las páginas **Herramientas** > **Opciones**:

   - La configuración de uso de mayúsculas y minúsculas de la barra de menús y de Tema en la página de opciones **Entorno** > **General**.

   - Todos los valores de la página de opciones **Entorno** > **Fuentes y colores**.

   - Todos los métodos abreviados de teclado en la página de opciones **Entorno** > **Teclado**.

   - Todos los valores de la página de opciones **Entorno** > **Pestañas y ventanas**.

   - Todos los valores de la página de opciones **Entorno** > **Inicio**.

   - Todos los valores de las páginas de opciones **Editor de texto**.

   - Todos los valores de las páginas de opciones **Diseñador XAML**.

## <a name="turn-off-synchronized-settings-on-a-particular-computer"></a>Desactivar la configuración sincronizada en un equipo concreto

La configuración sincronizada de Visual Studio está activada de forma predeterminada. Puede desactivar la configuración sincronizada en un equipo si va a la página **Herramientas** > **Opciones** > **Entorno** > **Cuentas** y desactiva **Sincronizar la configuración en todos los dispositivos al iniciar sesión en Visual Studio**. Por ejemplo, si decide no sincronizar la configuración de Visual Studio en el equipo "A", los cambios de configuración realizados en ese equipo no aparecerán en el equipo "B" ni en el equipo "C". Los equipos "B" y "C" se seguirán sincronizando entre ellos, pero no lo harán con el equipo "A".

## <a name="reset-settings"></a>Restablecer la configuración

Puede restablecer todas las configuraciones a una colección de valores predeterminados si sigue estos pasos:

1. En Visual Studio, seleccione **Herramientas** > **Importar y exportar configuraciones** para abrir el **Asistente para importar y exportar configuraciones**.

1. En el **Asistente para importar y exportar configuraciones**, seleccione **Restablecer todas las configuraciones** y, después, haga clic en **Siguiente**.

   ![Asistente para importar y exportar configuraciones en Visual Studio](media/reset-all-settings.png)

1. En la página **Guardar configuración actual**, haga clic en **Sí** o **No**, y después en **Siguiente**.

1. En la página **Elija una colección de configuraciones predeterminada**, seleccione una colección y, después, haga clic en **Finalizar**.

   ![Colecciones de configuraciones en Visual Studio](media/settings-collections.png)

1. En la página **Restablecimiento completado**, haga clic en **Cerrar**.

## <a name="synchronize-settings-across-visual-studio-family-products-and-editions"></a>Sincronizar la configuración en todos los productos y ediciones de la familia Visual Studio

La configuración se puede sincronizar en cualquier edición de Visual Studio, incluida la edición Community. La configuración también se sincroniza en los productos de la familia Visual Studio. Pero es posible que estos productos de la familia tengan su propia configuración que no se comparta con Visual Studio. Por ejemplo, la configuración específica de un producto en el equipo "A" se comparte con otro producto en el equipo "B", pero no con Visual Studio en los equipos "A" o "B".

## <a name="side-by-side-synchronized-settings"></a>Configuración sincronizada en paralelo

En Visual Studio 2017 versión 15.3 y posteriores, determinadas opciones como el diseño de ventanas de herramientas no se comparten entre otras instalaciones en paralelo de Visual Studio 2017. El archivo *CurrentSettings.vssettings* de *%userprofile%\Documents\Visual Studio 2017\Settings* se encuentra en una carpeta específica de la instalación que es similar a *%localappdata%\Microsoft\VisualStudio\15.0_xxxxxxxx\Settings*.

> [!NOTE]
> Para usar la nueva configuración específica de la instalación, realice una instalación nueva. Al actualizar una instalación de Visual Studio 2017 existente a la versión más reciente, se usa la ubicación compartida existente.

Si actualmente tiene instalaciones en paralelo de Visual Studio 2017 y quiere usar la nueva ubicación del archivo de configuración específico de la instalación, siga estos pasos:

1. Actualice a Visual Studio 2017, versión 15.3 o posterior.

1. Use el **Asistente para importar y exportar configuraciones** para exportar toda la configuración existente a una ubicación fuera de la carpeta *%localappdata%\Microsoft\VisualStudio\15.0_xxxxxxxx*.

1. Abra el **símbolo del sistema para desarrolladores de VS 2017** de la instalación de Visual Studio actualizada y ejecute `devenv /resetuserdata`.

1. Inicie Visual Studio e importe la configuración guardada desde el archivo de configuración exportado.

## <a name="see-also"></a>Vea también

[Personalizar el IDE](../ide/personalizing-the-visual-studio-ide.md)
