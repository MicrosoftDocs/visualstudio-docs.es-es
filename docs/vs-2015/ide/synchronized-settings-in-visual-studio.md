---
title: Configuración sincronizada
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- VS.ToolsOptionsPages.Environment.RoamingSettings
ms.assetid: a3d2ea29-be5d-4012-9820-44b06adbb7dd
caps.latest.revision: 13
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 6459b6f65fd1e29fbadb01f6aa2fc51520b726b8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "72646827"
---
# <a name="synchronized-settings-in-visual-studio"></a>Configuración sincronizada en Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Al usar la misma cuenta de personalización para iniciar sesión en Visual Studio en varios equipos, su configuración se sincroniza en todos los equipos de forma predeterminada.

## <a name="synchronized-settings"></a>Configuración sincronizada
 De forma predeterminada, se sincroniza la siguiente configuración.

- La configuración de desarrollo (Deberá seleccionar un conjunto de opciones la primera vez que ejecute Visual Studio, aunque puede cambiar la selección en cualquier momento. Para obtener más información, vea [personalizar la configuración de desarrollo en Visual Studio](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3)).

- Las siguientes opciones de las páginas **Herramientas &#124; Opciones**:

  - La configuración de uso de mayúsculas y minúsculas de la barra de menús y de **Tema**, en la página de opciones **Entorno**, **General**

  - Todos los valores de la página de opciones **Entorno**, **Fuentes y colores**

  - Todos los métodos abreviados de teclado, en la página de opciones **Entorno**, **Teclado**

  - Todos los valores de la página de opciones **Entorno, Pestañas y ventanas**

  - Todos los valores de la página de opciones **Entorno**, **Inicio**

  - Todas las configuraciones de las páginas de opciones del **Editor de texto**

- Todos los valores de las páginas de opciones Diseñador XAML

- Los alias de comandos definidos por el usuario. Para obtener más información sobre cómo definir los alias de comandos, vea [alias de comandos de Visual Studio](../ide/reference/visual-studio-command-aliases.md).

- Diseños de ventana definidos por el usuario en la página **Ventana &#124; Administrar diseños de ventana**

## <a name="turning-synchronized-settings-off-for-a-particular-computer"></a>Desactivar la configuración sincronizada para un equipo concreto
 La configuración sincronizada de Visual Studio está activada de forma predeterminada. Para desactivarla en un equipo, vaya a la página **Herramientas &#124; Opciones &#124; Entorno &#124; Configuración sincronizada** y desactive la casilla.  Por ejemplo, si decide no sincronizar la configuración de Visual Studio en el equipo A, los cambios de configuración efectuados en dicho equipo no aparecerán en el equipo B ni en el equipo C. Los equipos B y C se seguirán sincronizando entre ellos, pero no lo harán con el equipo A.

## <a name="synchronizing-settings-across-visual-studio-family-products-and-editions"></a>Configuración de sincronización en todos los productos y ediciones de la familia Visual Studio
 La configuración se puede sincronizar en cualquier edición de Visual Studio 2015, incluidas las ediciones Express y Community. La configuración también se sincroniza en los productos de la familia Visual Studio como, por ejemplo, Blend. Sin embargo, es posible que estos productos de la familia tengan su propia configuración no compartida con Visual Studio. Por ejemplo, la configuración específica de Blend en el equipo A se compartirá con Blend en el equipo B, pero no con Visual Studio en el equipo A o B.

> [!WARNING]
> La configuración no se sincroniza entre Visual Studio 2013 y Visual Studio 2015. La primera vez que abra Visual Studio 2015, se migra la configuración desde Visual Studio 2013, pero no se puede volver a migrar a Visual Studio 2013 después de eso.

## <a name="see-also"></a>Consulte también
 [Personalización del IDE](../ide/personalizing-the-visual-studio-ide.md)
