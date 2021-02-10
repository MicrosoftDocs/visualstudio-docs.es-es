---
title: Sincronizar la configuración
description: Obtenga información sobre cómo sincronizar la configuración de Visual Studio en varios equipos mediante el inicio de sesión en la misma cuenta de personalización.
ms.custom: SEO-VS-2020
ms.date: 06/18/2020
ms.topic: conceptual
ms.assetid: a3d2ea29-be5d-4012-9820-44b06adbb7dd
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 396981533502f2687040f470ded9b490cab1ef7a
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99970639"
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

  - Todos los valores de las páginas de opciones **Editor de texto**, por ejemplo, las [preferencias de estilo del código](code-styles-and-code-cleanup.md).

  - Todos los valores de las páginas de opciones **Diseñador XAML**.

## <a name="turn-off-synchronized-settings-on-a-particular-computer"></a>Desactivar la configuración sincronizada en un equipo concreto

La configuración sincronizada de Visual Studio está activada de forma predeterminada. Puede desactivar la configuración sincronizada en un equipo si va a la página **Herramientas** > **Opciones** > **Entorno** > **Cuentas** y desactiva **Sincronizar la configuración en todos los dispositivos al iniciar sesión en Visual Studio**.

Por ejemplo, si decide no sincronizar la configuración en Visual Studio en el equipo "A", los cambios de configuración realizados en ese equipo no aparecerán en el equipo "B" ni en el equipo "C". Los equipos "B" y "C" se seguirán sincronizando entre ellos, pero no lo harán con el equipo "A".

> [!NOTE]
> Si decide no sincronizar la configuración dejando sin seleccionar la opción en la página **Herramientas** > **Opciones** > **Entorno** > **Cuentas**, las otras versiones o ediciones de Visual Studio que haya en el mismo equipo no se verán afectadas. Esas instalaciones en paralelo de Visual Studio seguirán sincronizando su configuración (a menos que no seleccione la opción también en ellas).

## <a name="synchronize-settings-across-visual-studio-ide-products-and-editions"></a>Sincronización de la configuración en todos los productos y ediciones del IDE de Visual Studio

La configuración se sincroniza en todas las versiones y ediciones de Visual Studio instaladas *en paralelo*. También se sincroniza en los productos del IDE de Visual Studio, incluido Blend para Visual Studio. Con todo, es posible que un producto en concreto del IDE de Visual Studio tenga su propia configuración que no se comparte con Visual Studio. Por ejemplo, la configuración específica de Blend para Visual Studio en el equipo "A" no se comparte con Visual Studio en los equipos "A" o "B".

## <a name="side-by-side-synchronized-settings"></a>Configuración sincronizada en paralelo

::: moniker range="vs-2017"

No se comparten determinadas opciones, como el diseño de ventanas de herramientas, entre distintas instalaciones en paralelo de Visual Studio. El archivo *CurrentSettings.vssettings* de *%userprofile%\Documents\Visual Studio 2017\Settings* se encuentra en una carpeta específica de la instalación que es similar a *%localappdata%\Microsoft\VisualStudio\15.0_xxxxxxxx\Settings*.

> [!NOTE]
> Para usar la nueva configuración específica de la instalación, realice una instalación nueva. Al actualizar una instalación existente de Visual Studio, usa la ubicación compartida existente.

Si actualmente tiene instalaciones en paralelo de Visual Studio y quiere usar la nueva ubicación del archivo de configuración específico de la instalación, siga estos pasos:

1. Actualice a Visual Studio 2017, versión 15.3 o posterior.

2. Use el **Asistente para importar y exportar configuraciones** a fin de exportar toda la configuración existente a una ubicación fuera de la carpeta *%localappdata%\Microsoft\VisualStudio\15.0_xxxxxxxx*.

3. Abra el **Símbolo del sistema para desarrolladores de VS 2017** y ejecute `devenv /resetuserdata`.

1. Abra Visual Studio e importe la configuración guardada desde el archivo de configuración exportado.

::: moniker-end

::: moniker range=">=vs-2019"

No se comparten determinadas opciones, como el diseño de ventanas de herramientas, entre distintas instalaciones en paralelo de Visual Studio. El archivo *CurrentSettings.vssettings* de *%userprofile%\Documents\Visual Studio 2019\Settings* se encuentra en una carpeta específica de la instalación que es similar a *%localappdata%\Microsoft\VisualStudio\16.0_xxxxxxxx\Settings*.

::: moniker-end

## <a name="reset-synchronized-settings"></a>Restablecimiento de la configuración sincronizada

Para restablecer toda la configuración a sus valores predeterminados, inicie sesión en Visual Studio y seleccione **Herramientas** > **Importar y exportar configuraciones** para abrir el **Asistente para importar y exportar configuraciones**. Seleccione **Restablecer todas las configuraciones** y siga los pasos restantes del asistente.

## <a name="see-also"></a>Vea también

- [Personalizar el IDE](../ide/personalizing-the-visual-studio-ide.md)
- [Configuración del entorno](../ide/environment-settings.md)
- [Environment > Accounts Options dialog box](reference/accounts-environment-options-dialog-box.md) (Entorno > Opciones de cuentas [Cuadro de diálogo])
- [Instalación de distintas versiones de Visual Studio en paralelo](../install/install-visual-studio-versions-side-by-side.md)
