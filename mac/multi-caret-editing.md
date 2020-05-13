---
title: Edición de varios símbolos de inserción
description: Inserte texto en varias ubicaciones al editar código en Visual Studio para Mac.
author: cobey
ms.author: cobey
ms.date: 08/19/2019
ms.openlocfilehash: a21bebda057a772017fa1481e18f9801d1fbcbdf
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/20/2020
ms.locfileid: "75439053"
---
# <a name="multi-caret-editing"></a>Edición de varios símbolos de inserción

La edición de varios símbolos de inserción permite agregar _n_ puntos de inserción en un momento determinado. En el modo de varios símbolos de inserción, puede agregar símbolos de inserción adicionales al documento mediante clics del mouse o comandos del teclado. El símbolo de inserción principal se indica mediante un cursor rojo, mientras que los secundarios se muestran en color claro-azul. Se puede deshabilitar el modo de edición de varios símbolos de inserción con la tecla `ESC`.

## <a name="enabling-multi-caret-editing"></a>Habilitación de la edición de varios símbolos de inserción

### <a name="keyboard"></a>Teclado

Puede habilitar de varias maneras el modo de varios símbolos de inserción con teclado. En la tabla siguiente se proporcionan los métodos abreviados de teclado disponibles para indicar modos específicos de edición de varios símbolos de inserción:

| Tecla de acceso rápido  | Acción                        | 
|---------| ------------------------------|
|  ⌥⇧.   | Incluir siguiente símbolo de inserción coincidente    | 
|  ⌥⇧;   | Incluir símbolos de inserción en todas las coincidencias | 
|  ⌥⇧,   | Quitar el último símbolo de intercalación             | 
|  ⌥⇧/   | Bajar el último símbolo de intercalación          | 

Cada uno de estos comportamientos se delimita a la posición actual del símbolo de inserción al invocar el comando. Por ejemplo, si el símbolo de inserción se encuentra al principio de la palabra "name" e invoca "Incluir símbolos de inserción en todas las coincidencias" (⌥ ⇧;) cada instancia de la palabra "name" del documento actual tendrá un símbolo de inserción incluido al principio de la palabra. Del mismo modo, si invoca el comando "Incluir siguiente símbolo de inserción coincidente" (⌥ ⇧), se colocará un símbolo de inserción en la siguiente instancia de la palabra "name". Este comando se puede invocar varias veces.

![teclado de varios símbolos de inserción](media/multi-caret-keyboard.gif)

## <a name="mousetouchpad"></a>Mouse/panel táctil

Con el cursor, podrá seleccionar puntos de inserción específicos para los distintos símbolos de inserción. Mientras los métodos abreviados de teclado se enlazan a cadenas coincidentes, puede incluir manualmente un símbolo de inserción en cualquier parte del documento con el cursor. Cuando se han establecido los símbolos de inserción, cada uno de ellos devolverá las entradas de las teclas que escriba en el teclado.

Para usar el mouse para incluir varios símbolos de inserción, debe mantener presionado ⌘ ⌥ y hacer clic en la ubicación en la que desea que se escriban los símbolos de inserción. Estará en modo de inserción siempre y cuando se mantengan presionadas las teclas ⌘ ⌥. Si incluye un símbolo de inserción en una ubicación incorrecta, puede quitar dicho símbolo si continúa manteniendo ⌘ ⌥ y vuelve a hacer clic en la misma área. Cuando ya tenga todos los símbolos de inserción en donde desea que estén, suelte las teclas ⌘ ⌥ y empiece a escribir. El siguiente GIF muestra cómo seleccionar un conjunto de puntos de inserción, así como quitar los puntos establecidos erróneamente.

![varios símbolos de inserción con el mouse](media/multi-caret-mouse.gif)

## <a name="see-also"></a>Consulte también

- [Acciones rápidas (Visual Studio en Windows)](/visualstudio/ide/quick-actions)
- [Refactorizar código (Visual Studio en Windows)](/visualstudio/ide/refactoring-in-visual-studio)
