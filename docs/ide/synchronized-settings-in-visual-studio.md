
---
title: "Sincronizar la configuración de Visual Studio | Microsoft Docs"
ms.custom: 
ms.date: 01/23/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VS.ToolsOptionsPages.Environment.RoamingSettings
ms.assetid: a3d2ea29-be5d-4012-9820-44b06adbb7dd
caps.latest.revision: 10
author: kempb
ms.author: kempb
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 0387b9a656f97d9354f95f121cad8422e93a69bc
ms.openlocfilehash: e48edfa02f059444539e0a3d8514366f94a1a1f1
ms.contentlocale: es-es
ms.lasthandoff: 08/18/2017

---
# <a name="synchronize-your-settings-in-visual-studio"></a>Sincronizar la configuración de Visual Studio

Al iniciar sesión en Visual Studio en varios equipos con la misma cuenta de personalización, su configuración se sincroniza en todos los equipos de manera predeterminada.

## <a name="synchronized-settings"></a>Configuración sincronizada

De forma predeterminada, se sincroniza la siguiente configuración.

- La configuración de desarrollo (Deberá seleccionar un conjunto de opciones la primera vez que ejecute Visual Studio, aunque puede cambiar la selección en cualquier momento. Para obtener más información, vea [Personalizar el IDE de Visual Studio](../ide/personalizing-the-visual-studio-ide.md)).

- Las siguientes opciones de las páginas **Herramientas &#124; Opciones**:

    - La configuración de uso de mayúsculas y minúsculas de la barra de menús y de **Tema**, en la página de opciones **Entorno**, **General**

    - Todos los valores de la página de opciones **Entorno**, **Fuentes y colores**

    - Todos los métodos abreviados de teclado, en la página de opciones **Entorno**, **Teclado**

    - Todos los valores de la página de opciones **Entorno, Pestañas y ventanas**

    - Todos los valores de la página de opciones **Entorno**, **Inicio**

    - Todos los valores de las páginas de opciones **Editor de texto**

    - Todos los valores de las páginas de opciones **Diseñador XAML**

- Los alias de comandos definidos por el usuario. Para obtener más información sobre cómo se definen los alias de comandos, consulte [Alias de comandos de Visual Studio](../ide/reference/visual-studio-command-aliases.md).

- Diseños de ventana definidos por el usuario en la página **Ventana &#124; Administrar diseños de ventana**

## <a name="turn-off-synchronized-settings-on-a-particular-computer"></a>Desactivar la configuración sincronizada en un equipo concreto

La configuración sincronizada de Visual Studio está activada de forma predeterminada. Para desactivarla en un equipo, vaya a la página **Herramientas &#124; Opciones &#124; Entorno &#124; Configuración sincronizada** y desactive la casilla.  Por ejemplo, si decide no sincronizar la configuración de Visual Studio en el equipo A, los cambios de configuración efectuados en dicho equipo no aparecerán en el equipo B ni en el equipo C. Los equipos B y C se seguirán sincronizando entre ellos, pero no lo harán con el equipo A.

## <a name="synchronize-settings-across-visual-studio-family-products-and-editions"></a>Sincronizar la configuración en todos los productos y ediciones de la familia Visual Studio

La configuración se puede sincronizar en cualquier edición de Visual Studio, incluida la edición Community. La configuración también se sincroniza en los productos de la familia Visual Studio. Sin embargo, es posible que estos productos de la familia tengan su propia configuración no compartida con Visual Studio. Por ejemplo, la configuración específica de un producto en el equipo A se compartirá con otro en el equipo B, pero no con Visual Studio en el equipo A o B.

## <a name="side-by-side-synchronized-settings"></a>Configuración sincronizada en paralelo

En Visual Studio 15.3 y versiones posteriores, hemos dejado de compartir determinadas opciones de configuración, como el diseño de la ventana de herramientas, entre diferentes instalaciones en paralelo de Visual Studio 2017. Para ello, se ha cambiado la ubicación del archivo `CurrentSettings.vssettings` en `%userprofile%\Documents\Visual Studio 2017\Settings` a una carpeta específica de la instalación similar a `%localappdata%\Microsoft\VisualStudio\15.0_xxxxxxxx\Settings`.

**NOTA**: Para usar la nueva configuración específica de la instalación, debe completar una instalación nueva. Al actualizar una instalación de Visual Studio 2017 existente a la versión más reciente, se usará la misma ubicación compartida. Si actualmente tiene instalaciones en paralelo de Visual Studio 2017 y decide actualizar y, para ello, quiere usar la nueva ubicación del archivo de configuración específica de la instalación, siga estos pasos:

1. Después de la actualización, use el asistente para importar y exportar configuraciones y exporte toda la configuración existente a una ubicación cualquiera fuera de la carpeta `%localappdata%\Microsoft\VisualStudio\15.0_xxxxxxxx`.
2. Abra el **símbolo del sistema para desarrolladores VS 2017** de la instalación de Visual Studio actualizada y ejecute `devenv /resetuserdata` desde ahí.
3. Inicie Visual Studio e importe la configuración guardada desde el archivo de configuración exportado.

## <a name="see-also"></a>Vea también

[Personalizar el IDE](../ide/personalizing-the-visual-studio-ide.md)

