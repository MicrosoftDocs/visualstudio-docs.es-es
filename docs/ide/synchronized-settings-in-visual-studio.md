---
title: Sincronizar la configuración
ms.date: 11/21/2018
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
ms.openlocfilehash: ecac148e745eff956151af71a37b23f67a816f56
ms.sourcegitcommit: dd839de3aa24ed7cd69f676293648c6c59c6560a
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/27/2018
ms.locfileid: "52388496"
---
# <a name="synchronize-visual-studio-settings-across-multiple-computers"></a>Sincronizar la configuración de Visual Studio en varios equipos

Al iniciar sesión en Visual Studio en varios equipos con la misma cuenta de personalización, se puede sincronizar la configuración entre todos los equipos.

## <a name="synchronized-settings"></a>Configuración sincronizada

De forma predeterminada, se sincroniza la configuración siguiente:

- Configuración de desarrollo. La primera vez que se abre Visual Studio, se selecciona una colección de opciones que luego se puede cambiar en cualquier momento. Para obtener más información, vea [Configuración del entorno](../ide/environment-settings.md).

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

- [Personalizar el IDE](../ide/personalizing-the-visual-studio-ide.md)
- [Configuración del entorno](../ide/environment-settings.md)
- [Environment > Accounts Options dialog box](reference/synchronized-settings-environment-options-dialog-box.md) (Entorno > Opciones de cuentas [Cuadro de diálogo])
