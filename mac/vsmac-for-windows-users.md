---
title: Visual Studio para Mac dirigido a usuarios de Windows
description: Introducción a Visual Studio para Mac dirigida a desarrolladores familiarizados con el uso de Visual Studio en el sistema operativo Windows.
author: heiligerdankgesang
ms.author: dominicn
ms.date: 11/09/2020
ms.assetid: 61CB6883-08CE-470F-8599-6F7570DB756E
ms.openlocfilehash: 880811c675aac34a18a65c6eccb8ee10f3347d4c
ms.sourcegitcommit: 2cf3a03044592367191b836b9d19028768141470
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/11/2020
ms.locfileid: "94493379"
---
# <a name="visual-studio-for-mac-for-windows-users"></a>Visual Studio para Mac dirigido a usuarios de Windows

La migración de un sistema operativo a otro puede ser desalentadora. Con frecuencia, hay diferencias sutiles en las aplicaciones multiplataforma, desde la interfaz de usuario hasta la categorización de los elementos de menú. Aquí conocerá las diferencias más comunes entre Visual Studio para Mac y Visual Studio para Windows. También aprenderá algunas convenciones diferentes entre macOS y Windows.

## <a name="keyboard-shortcuts"></a>Accesos directos del teclado

Muchos desarrolladores están acostumbrados a usar el teclado para las tareas y la navegación. Algunas teclas del teclado son comunes entre los equipos Mac y Windows. Se podría pensar que las acciones del teclado, como copiar y pegar, usan las mismas combinaciones de teclas. Pero no siempre es así. Por fortuna, puede cambiar los enlaces de teclado en Visual Studio para Mac para que sean muy similares a los de Visual Studio en Windows.

La primera vez que ejecute Visual Studio para Mac verá la ventana de selección de métodos abreviados de teclado: ![Ventana de enlaces de teclado](media/ide-tour-2019-keyboard-shortcut.png)

Si quiere cambiar los enlaces de teclado más adelante, puede encontrar la configuración en las preferencias: ![Preferencias de enlaces de teclado](media/customizing-the-ide-image10a.png)

Es importante advertir que los accesos directos que emplea macOS para Windows son diferentes en todo el sistema. Cambiar las preferencias de enlace de teclado le permitirá usar los métodos abreviados de Windows conocidos en Visual Studio para Mac. Sin embargo, en otras áreas de macOS deberá estar familiarizado con los métodos abreviados de macOS.

Normalmente, la tecla modificadora Comando de macOS (⌘) puede reemplazar normalmente a la tecla Control de Windows. Estos son algunos ejemplos y otros métodos abreviados usados comúnmente:

|Tarea                   |Acceso directo de Windows         |Acceso directo de macOS      |
|-----------------------|-------------------------|--------------------|
|Copiar                   |`Ctrl + C`               |`⌘ + C`             |
|Pegar                  |`Ctrl + V`               |`⌘ + V`             |
|Cortar                    |`Ctrl + X`               |`⌘ + X`             |
|Deshacer                   |`Ctrl + Z`               |`⌘ + Z`             |
|Rehacer                   |`Ctrl + Shift + Z`       |`⌘ + Shift + Z`     |
|Eliminar a la derecha del cursor |`Delete`                 |`fn + Backspace`    |
|Eliminar palabra            |`Ctrl + Delete`          |`fn + ⌥ + Backspace`|

> [!TIP]
> Puede encontrar una lista completa de métodos abreviados de macOS en el [sitio web de soporte de Apple](https://support.apple.com/en-us/HT201236).

## <a name="menus"></a>Menús

Los menús de macOS se organizan de forma diferente a los menús de Windows. Visual Studio para Mac no es ninguna excepción. Puede encontrar algunas de las opciones de menú más comunes aquí:

|Tarea                   |Visual Studio (Windows)                                              |Visual Studio para Mac                |
|-----------------------|---------------------------------------------------------------------|-------------------------------------|
|Preferencias (opciones)  |Herramientas > Opciones...                                                   |Visual Studio > Preferencias...       |
|Extensiones             |Extensiones > Administrar extensiones                                       |Visual Studio > Extensiones...        |
|Diseños                |Ventana > Aplicar diseño de ventana > [seleccionar diseño]                       |Ver > Diseño > [Seleccionar diseño]               |
|Actualizaciones                |Ayuda > Buscar actualizaciones                                             |Visual Studio > Buscar actualizaciones... |
|Administrador de paquetes de NuGet  |Herramientas > Administrador de paquetes NuGet > Administrar paquetes NuGet para la solución... |Proyecto > Administrar paquetes NuGet...   |
|Buscar herramientas             |Editar > Buscar y reemplazar > [seleccionar herramienta]                              |Buscar > [seleccionar herramienta]               |
|Acerca de Visual Studio    |Ayuda > Acerca de Microsoft Visual Studio                                 |Visual Studio > Acerca de Visual Studio  

> [!NOTE]
> Puede encontrar información general sobre las características más comunes de Visual Studio para Mac en [Paseo por el IDE](ide-tour.md).