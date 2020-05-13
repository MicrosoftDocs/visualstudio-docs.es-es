---
title: IntelliSense
description: Información sobre el uso de IntelliSense en Visual Studio para Mac
author: cobey
ms.author: cobey
ms.date: 08/16/2019
ms.openlocfilehash: 07ef1d6292e4ac88ca616d0f35e3fd831cacc649
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/20/2020
ms.locfileid: "75405808"
---
# <a name="intellisense"></a>IntelliSense

IntelliSense ofrece varias características que ayudan a mejorar la experiencia de escritura y edición de código. Por ejemplo, además de la función de finalización de código, el motor de IntelliSense también proporciona listas de miembros, información de parámetros e información rápida.

En Visual Studio para Mac, IntelliSense se suministra mediante el servicio de editor principal y es compatible con muchos lenguajes, como C#, XAML, F#, JavaScript y muchos más. Visual Studio para Mac también incluye características avanzadas de IntelliSense, como la capacidad de mostrar finalizaciones de bibliotecas que todavía no se han importado en el proyecto.

## <a name="code-completion"></a>Finalización de código

Cuando escriba en un archivo compatible, como un archivo de código de C#, las finalizaciones válidas de la cadena que esté escribiendo se mostrarán en una lista de finalización y se actualizarán a medida que escribe. Además, si elimina texto, la lista se volverá a actualizar automáticamente para incluir el mayor número de posibilidades para finalizar la cadena. 

La ventana de finalización también permite filtrar las finalizaciones incluidas por tipo. Por ejemplo, es posible limitar los miembros de la lista para que solo se representen tipos como clases o delegados. Para habilitar este proceso de filtrado, se puede hacer clic en el icono que representa el tipo que se filtrará o bien usar los métodos abreviados de teclado correspondientes al tipo determinado. Los iconos, que se encuentran en la parte inferior de la ventana de finalización, son los siguientes:

| Icono                         | Nombre          | Palabra clave    | Tecla de acceso rápido |
| -----------------------------|---------------| -----------|--------|
| ![Icono Clases](media/classes-icon.png)  | class         | `class`    |  ⌥C
| ![Icono Constante](media/constant-icon.png) | constant      | `const`    |  ⌥O
| ![Icono Delegado](media/delegate-icon.png) | delegado      | `delegate` |  ⌥D
| ![Icono Enumeración](media/enums-icon.png)    | enum          | `enum`     |  ⌥E
| ![Icono Evento](media/event-icon.png)    | event         |            |  ⌥V
| ![Icono Campo](media/fields-icon.png)   | campo         |            |  ⌥F
| ![Icono Interfaz](media/interface-icon.png)| interfaz     | `interface`|  ⌥I
| ![Icono Palabra clave](media/keyword-icon.png)  | palabra clave       |            |  ⌥K
| ![Icono Método](media/method-icon.png)   | method        |            |  ⌥M
| ![Icono Espacio de nombres](media/namespace-icon.png)| espacio de nombres     | `namespace`|  ⌥N
| ![Icono Propiedades](media/props-icon.png)    | propiedad      |            |  ⌥P
| ![Icono Fragmento de código](media/snippet-icon.png)  | fragmento de código       | `class`    |  ⌥S
| ![Icono Estructura](media/struct-icon.png)   | structure     | `struct`   |  ⌥S

Al hacer clic en cualquiera de los iconos, o al presionar las teclas de acceso rápido correspondientes, la lista de finalización se limitará a los tipos definidos en el conjunto de filtros.  

![Filtrado de tipos de IntelliSense](media/intellisense-typefiltering.gif)

## <a name="parameter-window"></a>Ventana de parámetros

Otra característica de IntelliSense es la capacidad de proporcionar una lista de parámetros cuando sea necesario. La lista de parámetros muestra información sobre las firmas de método del código al que se está llamando. Al hacer clic en las flechas arriba o abajo incluidas en la firma, puede recorrer cada una de las firmas de parámetros disponibles para determinar cuáles son las más adecuadas para sus necesidades. Además de información sobre los tipos de datos permitidos podría incluirse una descripción, tal como se define en el método de destino a través de comentarios XML.

![Lista de parámetros](media/intellisense-parameter.png)

Al rellenar los parámetros, se mostrará en negrita el parámetro que esté editando en el momento, mientras que los parámetros inactivos tendrán el grosor estándar. 


## <a name="triggering-completion-window-and-parameter-window"></a>Desencadenamiento de la ventana de finalización y de la ventana de parámetros

La ventana de finalización se desencadenará automáticamente cuando escriba dentro del archivo de código fuente. Además, puede desencadenar la ventana de finalización mediante el acceso directo `control-space`. Esta combinación de teclas hará que la lista de finalización aparezca en la posición actual del símbolo de inserción. 

También puede desencadenar manualmente la aparición de la ventana de parámetros si escribe `control-shift-space`. Cuando el símbolo de inserción está en una posición válida para una lista de parámetros, esta aparecerá cerca de la posición del símbolo de inserción.

## <a name="see-also"></a>Consulte también

- [Acciones rápidas (Visual Studio en Windows)](/visualstudio/ide/quick-actions)
- [Refactorizar código (Visual Studio en Windows)](/visualstudio/ide/refactoring-in-visual-studio)
