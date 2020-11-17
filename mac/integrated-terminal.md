---
title: 'Visual Studio para Mac: terminal integrado'
description: Trabajo con el terminal integrado en Visual Studio para Mac.
author: jmatthiesen
ms.author: jomatthi
ms.date: 05/14/2020
ms.assetid: EFD53CE9-8174-4FE4-8863-2984D22FD921
ms.openlocfilehash: f91c2b1c3f06f8f1fbe54e32fde70b9fe88c5f5d
ms.sourcegitcommit: 2cf3a03044592367191b836b9d19028768141470
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/11/2020
ms.locfileid: "94492877"
---
# <a name="integrated-terminal"></a>Terminal integrado
En Visual Studio para Mac, puede abrir una ventana de terminal integrado, que se inicia al principio en la raíz de la solución. El terminal puede resultar útil en distintos tipos de situaciones: la ejecución de tareas de front-end (por ejemplo: NPM, NG o Vue), la administración de contenedores, la ejecución de comandos avanzados de Git, la ejecución de comandos de Entity Framework, la visualización de la salida de la CLI de dotnet, la adición de paquetes NuGet, etc. 

Para abrir el terminal:
- Use el método abreviado de teclado **Ctrl + "** para mostrar u ocultar la ventana de terminal.
- Use el menú **Ver** \> **Terminal**.
- Use el comando **terminal** de la barra de búsqueda.

![*Terminal integrado de Visual Studio para Mac inmediatamente después de iniciarse.*](media/integrated-terminal-intro.png)

De forma predeterminada, cuando se inicia, el terminal hace lo siguiente:
- Establecer el directorio de trabajo en la ruta de acceso de la solución actual.
- Cargar el shell del sistema predeterminado.

## <a name="search"></a>Buscar
Puede buscar en el contenido de la ventana de terminal mediante el menú **Buscar > Búsqueda...** .

![*Experiencia de búsqueda en el terminal integrado de Visual Studio para Mac*](media/integrated-terminal-search.png)

## <a name="terminal-keyboard-shortcuts"></a>Métodos abreviados de teclado de terminal
|Comandos|Métodos abreviados de teclado|
|-|-|
|Mostrar u ocultar la ventana de terminal|**Ctrl+ "**|
|Crear una instancia de terminal|**Ctrl+'**|
|Retroceder una página|**RePág**|
|Avanzar una página|**AvPág**|
|Desplazarse por los comandos usados anteriormente|**↑**, **↓**|
|Aumentar el tamaño de fuente|**⌘+**|
|Reducir el tamaño de fuente|**⌘-**|

## <a name="multiple-instances"></a>Varias instancias
Pueden ejecutarse varias instancias del terminal en cualquier momento. Puede crear otra instancia mediante el método abreviado de teclado **Ctrl+"** . Puede cambiar de una instancia a otra haciendo clic en la pestaña de cada instancia, o bien con el acceso directo **Ctrl+Tab** para usar el cuadro de diálogo del selector de ventanas.

![*Varias instancias de terminal en Visual Studio para Mac*](media/integrated-terminal-multiple-instances.png) 

## <a name="customizing-the-terminal-window"></a>Personalización de la ventana de terminal
### <a name="configuring-the-terminal-font"></a>Configuración de la fuente de terminal
Puede cambiar la fuente y el tamaño usados para el contenido de terminal en el panel Preferencias > Entorno > Fuentes. De forma predeterminada, la fuente será la misma que la del contenido de la Ventana de salida, es decir, Menlo normal de tamaño 11. Se puede establecer en cualquier fuente, independientemente de la fuente del editor.

![*Personalización de la configuración de fuente para el terminal integrado*](media/integrated-terminal-change-font.png)

### <a name="reusing-system-terminal-customizations"></a>Reutilización de las personalizaciones de terminal del sistema
El terminal integrado usa los mismos valores predeterminados y la misma configuración que el terminal del sistema macOS. Esto significa que las personalizaciones de terminal (zsh, oh-my-zsh, etc.) también funcionan en el terminal integrado.
