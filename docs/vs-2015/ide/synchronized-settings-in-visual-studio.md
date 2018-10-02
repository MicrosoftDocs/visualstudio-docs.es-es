---
title: Configuración sincronizada en Visual Studio | Documentos de Microsoft
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- VS.ToolsOptionsPages.Environment.RoamingSettings
ms.assetid: a3d2ea29-be5d-4012-9820-44b06adbb7dd
caps.latest.revision: 13
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 1e0facac569671c880004d1fc1a7aa29487e7926
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47580272"
---
# <a name="synchronized-settings-in-visual-studio"></a>Configuración sincronizada en Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [sincronizar la configuración de Visual Studio](https://docs.microsoft.com/visualstudio/ide/synchronized-settings-in-visual-studio).  
  
Al usar la misma cuenta de personalización para iniciar sesión en Visual Studio en varios equipos, su configuración se sincroniza en todos los equipos de forma predeterminada.  
  
## <a name="synchronized-settings"></a>Configuración sincronizada  
 De forma predeterminada, se sincroniza la siguiente configuración.  
  
-   La configuración de desarrollo (Deberá seleccionar un conjunto de opciones la primera vez que ejecute Visual Studio, aunque puede cambiar la selección en cualquier momento. Para obtener más información, consulte [Personalizar la configuración de desarrollo en Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3)).  
  
-   Las siguientes opciones de las páginas **Herramientas &#124; Opciones**:  
  
    -   La configuración de uso de mayúsculas y minúsculas de la barra de menús y de **Tema**, en la página de opciones **Entorno**, **General**  
  
    -   Todos los valores de la página de opciones **Entorno**, **Fuentes y colores**  
  
    -   Todos los métodos abreviados de teclado, en la página de opciones **Entorno**, **Teclado**  
  
    -   Todos los valores de la página de opciones **Entorno, Pestañas y ventanas**  
  
    -   Todos los valores de la página de opciones **Entorno**, **Inicio**  
  
    -   Todos los valores de las páginas de opciones **Editor de texto**  
  
-   Todos los valores de las páginas de opciones Diseñador XAML  
  
-   Los alias de comandos definidos por el usuario. Para obtener más información sobre cómo se definen los alias de comandos, consulte [Alias de comandos de Visual Studio](../ide/reference/visual-studio-command-aliases.md).  
  
-   Diseños de ventana definidos por el usuario en la página **Ventana &#124; Administrar diseños de ventana**  
  
## <a name="turning-synchronized-settings-off-for-a-particular-computer"></a>Desactivar la configuración sincronizada para un equipo concreto  
 La configuración sincronizada de Visual Studio está activada de forma predeterminada. Para desactivarla en un equipo, vaya a la página **Herramientas &#124; Opciones &#124; Entorno &#124; Configuración sincronizada** y desactive la casilla.  Por ejemplo, si decide no sincronizar la configuración de Visual Studio en el equipo A, los cambios de configuración efectuados en dicho equipo no aparecerán en el equipo B ni en el equipo C. Los equipos B y C se seguirán sincronizando entre ellos, pero no lo harán con el equipo A.  
  
## <a name="synchronizing-settings-across-visual-studio-family-products-and-editions"></a>Configuración de sincronización en todos los productos y ediciones de la familia Visual Studio  
 La configuración se puede sincronizar en cualquier edición de Visual Studio 2015, incluidas las ediciones Express y Community. La configuración también se sincroniza en los productos de la familia Visual Studio como, por ejemplo, Blend. Sin embargo, es posible que estos productos de la familia tengan su propia configuración no compartida con Visual Studio. Por ejemplo, la configuración específica de Blend en el equipo A se compartirá con Blend en el equipo B, pero no con Visual Studio en el equipo A o B.  
  
> [!WARNING]
>  La configuración no se sincroniza entre Visual Studio 2013 y Visual Studio 2015. La primera vez que abra Visual Studio 2015, se migra la configuración desde Visual Studio 2013, pero no se puede volver a migrar a Visual Studio 2013 después de eso.  
  
## <a name="see-also"></a>Vea también  
 [Personalizar el IDE](../ide/personalizing-the-visual-studio-ide.md)



