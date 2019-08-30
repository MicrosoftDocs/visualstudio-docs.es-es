---
title: IntelliSense
description: Información sobre el uso de IntelliSense en Visual Studio para Mac
author: cobey
ms.author: cobey
ms.date: 08/16/2019
ms.openlocfilehash: 3e99c31b1ab4d12532d701e4626ac9c1aae7df56
ms.sourcegitcommit: 0bd63f3bc429ae059b9df6e45c6b8dcae6152940
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/26/2019
ms.locfileid: "70026574"
---
# <a name="intellisense"></a>IntelliSense

IntelliSense ofrece varias características que ayudan a mejorar la experiencia de escritura y edición de código. Por ejemplo, además de la función de finalización de código, el motor de IntelliSense también proporciona listas de miembros, información de parámetros e información rápida.

En Visual Studio para Mac, IntelliSense se suministra mediante el servicio de editor principal y es compatible con muchos lenguajes, como C#, XAML, F#, JavaScript y muchos más. Visual Studio para Mac también incluye características avanzadas de IntelliSense, como la capacidad de mostrar finalizaciones de bibliotecas que todavía no se han importado en el proyecto.

## <a name="code-completion"></a>Finalización de código

Cuando escriba en un archivo compatible, como un archivo de código de C#, las finalizaciones válidas de la cadena que esté escribiendo se mostrarán en una lista de finalización y se actualizarán a medida que escribe. Además, si elimina texto, la lista se volverá a actualizar automáticamente para incluir el mayor número de posibilidades para finalizar la cadena. 

La ventana de finalización también permite filtrar las finalizaciones incluidas por tipo. Por ejemplo, es posible limitar los miembros de la lista para que solo se representen tipos como clases o delegados. Para habilitar este proceso de filtrado, se puede hacer clic en el icono que representa el tipo que se filtrará o bien usar los métodos abreviados de teclado correspondientes al tipo determinado. Los iconos, que se encuentran en la parte inferior de la ventana de finalización, son los siguientes:

| Iconos                         | nombre          | Palabra clave    | Tecla de acceso rápido |
| -----------------------------|---------------| -----------|--------|
| ![Icono Clases](media/classes-icon.png)  | clase         | `class`    |  ⌥C
| ![Icono Constante](media/constant-icon.png) | constant      | `const`    |  ⌥O
| ![Icono Delegado](media/delegate-icon.png) | delegado      | `delegate` |  ⌥D
| ![Icono Enumeración](media/enums-icon.png)    | enum          | `enum`     |  ⌥E
| ![Icono Evento](media/event-icon.png)    | evento         |            |  ⌥V
| ![Icono Campo](media/fields-icon.png)   | campo         |            |  ⌥F
| ![Icono Interfaz](media/interface-icon.png)| interfaz     | `interface`|  ⌥I
| ![Icono Palabra clave](media/keyword-icon.png)  | palabra clave       |            |  ⌥K
| ![Icono Método](media/method-icon.png)   | método        |            |  ⌥M
| ![Icono Espacio de nombres](media/namespace-icon.png)| namespace     | `namespace`|  ⌥N
| ![Icono Propiedades](media/props-icon.png)    | propiedad      |            |  ⌥P
| ![Icono Fragmento de código](media/snippet-icon.png)  | snippet       | `class`    |  ⌥S
| ![Icono Estructura](media/struct-icon.png)   | estructura     | `struct`   |  ⌥S

Al hacer clic en cualquiera de los iconos, o al presionar las teclas de acceso rápido correspondientes, la lista de finalización se limitará a los tipos definidos en el conjunto de filtros.  

![Filtrado de tipos de IntelliSense](media/intellisense-typefiltering.gif)

## <a name="show-import-items"></a>Visualización de elementos de importación

De forma predeterminada, la finalización de IntelliSense solo mostrará las finalizaciones de las bibliotecas que se hayan importado en el proyecto. Por ejemplo, si no ha importado `System.Collections.Generic` mediante `using`, no tendrá una finalización de `List<>`. Para mostrar finalizaciones de bibliotecas que no se han importado, debe habilitar **Show Import Items** (Mostrar elementos de importación) en las preferencias de Visual Studio para Mac. Esta opción se encuentra en **Preferencias > Editor de texto >IntelliSense**:

![Opción de IntelliSense para mostrar elementos de importación](media/intellisense-showimport.png)

Una vez habilitada la opción **Show Import Items** (Mostrar elementos de importación), la lista de finalización incluirá finalizaciones que todavía no se han importado. Al seleccionar un elemento que se corresponde con una biblioteca no declarada, la instrucción `using` de esa biblioteca se agregará automáticamente al encabezado del archivo de código. También se muestra el nombre de la biblioteca a la que pertenece la finalización junto con la propia finalización.

![Lista de visualización de los elementos de importación](media/intellisense-importaction.png)

## <a name="parameter-window"></a>Ventana de parámetros

Otra característica de IntelliSense es la capacidad de proporcionar una lista de parámetros cuando sea necesario. La lista de parámetros muestra información sobre las firmas de método del código al que se está llamando. Al hacer clic en las flechas arriba o abajo incluidas en la firma, puede recorrer cada una de las firmas de parámetros disponibles para determinar cuáles son las más adecuadas para sus necesidades. Además de información sobre los tipos de datos permitidos podría incluirse una descripción, tal como se define en el método de destino a través de comentarios XML.

![Lista de parámetros](media/intellisense-parameter.png)

Al rellenar los parámetros, se mostrará en negrita el parámetro que esté editando en el momento, mientras que los parámetros inactivos tendrán el grosor estándar. 


## <a name="triggering-completion-window-and-parameter-window"></a>Desencadenamiento de la ventana de finalización y de la ventana de parámetros

La ventana de finalización se desencadenará automáticamente cuando escriba dentro del archivo de código fuente. Además, puede desencadenar la ventana de finalización mediante el acceso directo `control-space`. Esta combinación de teclas hará que la lista de finalización aparezca en la posición actual del símbolo de inserción. 

También puede desencadenar manualmente la aparición de la ventana de parámetros si escribe `control-shift-space`. Cuando el símbolo de inserción está en una posición válida para una lista de parámetros, esta aparecerá cerca de la posición del símbolo de inserción.

## <a name="see-also"></a>Vea también

- [Acciones rápidas (Visual Studio en Windows)](/visualstudio/ide/quick-actions)
- [Refactorizar código (Visual Studio en Windows)](/visualstudio/ide/refactoring-in-visual-studio)
