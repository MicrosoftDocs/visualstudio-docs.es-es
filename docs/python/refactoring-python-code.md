---
title: Refactorización del código de Python
description: Describe cómo refactorizar código de Python fácilmente en Visual Studio mediante el cambio de nombre de los identificadores, la extracción de métodos, la adición de importaciones y la retirada de las importaciones que no se usan.
ms.date: 07/12/2017
ms.prod: visual-studio-dev15
ms.technology: vs-python
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: douge
ms.workload:
- python
- data-science
ms.openlocfilehash: bc06ba43261a90dcfe6677a73c8a267a7efdcb1c
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/19/2018
ms.locfileid: "31583078"
---
# <a name="refactoring-python-code"></a>Refactorización del código de Python

Visual Studio proporciona varios comandos para transformar y limpiar automáticamente el código fuente de Python:

- [Cambiar nombre](#rename): cambia el nombre de la clase, el método o la variable seleccionados.
- [Extraer método](#extract-method): crea un nuevo método a partir del código seleccionado.
- [Agregar importación](#add-import): proporciona una etiqueta inteligente para agregar una importación que falta.
- [Quitar importaciones no usadas](#remove-unused-imports): quita las importaciones no utilizadas.

<a name="rename-variable"</a>

## <a name="rename"></a>Cambiar nombre

1. Haga clic con el botón derecho en el identificador cuyo nombre desea cambiar y seleccione **Rename** (Cambiar nombre); o bien, coloque el símbolo de intercalación en ese identificador y seleccione el comando de menú **Edit > Refactor > Rename...** (Editar > Refactorizar > Cambiar nombre...) (F2).
1. En el diálogo **Rename** (Cambiar nombre) que aparece, escriba el nuevo nombre del identificador y seleccione **OK** (Aceptar):

  ![Mensaje de cambio de nombre para el nuevo nombre identificado](media/code-refactor-rename-1.png)

1. En el siguiente diálogo, seleccione los archivos y las instancias del código al que se va a aplicar el cambio de nombre; seleccione cualquier instancia individual para obtener una vista previa del cambio concreto:

  ![Diálogo de cambio de nombre para seleccionar dónde aplicar los cambios](media/code-refactor-rename-2.png)

1. Seleccione **Apply** (Aplicar) para realizar los cambios en los archivos de código fuente. (Esta acción se no puede deshacer).

## <a name="extract-method"></a>Extraer método

1. Seleccione las líneas de código o la expresión para extraer en un método distinto.
1. Seleccione el comando de menú **Edit > Refactor > Extract method...** (Editar > Refactorizar > Extraer método...) o pulse Ctrl+R, M.
1. En el diálogo que aparece, escriba un nuevo nombre de método, indique dónde extraerlo y seleccione las variables de cierre. Las variables no seleccionadas para cierre se convierten en los argumentos de método:

  ![Diálogo de extracción de método](media/code-refactor-extract-method-1.png)

1. Seleccione **OK** (Aceptar); el código se modifica en consecuencia:

  ![Efecto de la extracción de un método](media/code-refactor-extract-method-2.png)

## <a name="add-import"></a>Agregar importación

Al colocar el símbolo de intercalación en un identificador que carece de información de tipo, Visual Studio proporciona una etiqueta inteligente (el icono de bombilla a la izquierda del código) cuyos comandos agregan la instrucción `import` o `from ... import` necesaria:

![Agregar etiqueta inteligente de importación](media/code-refactor-add-import-1.png)

Visual Studio ofrece finalizaciones de `import` para paquetes de nivel superior y módulos en el proyecto actual y la biblioteca estándar. Visual Studio también ofrece finalizaciones de `from ... import` para submódulos y subpaquetes, así como para miembros de módulo. Las finalizaciones incluyen funciones, clases o datos exportados. Al seleccionar cualquier opción, se agrega la instrucción a la parte superior del archivo, detrás de otras importaciones, o a una instrucción `from ... import` existente si ya se importó el mismo módulo.

![Resultado de agregar una importación](media/code-refactor-add-import-2.png)

Visual Studio intenta filtrar miembros que no están definidos realmente en un módulo, como módulos que se importan en otros, pero no son elementos secundarios del módulo que realiza la importación. Por ejemplo, muchos módulos usan `import sys` en lugar de `from xyz import sys`, por lo que no verá una finalización para importar `sys` desde otros módulos, aunque a los módulos les falte un miembro `__all__` que excluye `sys`.

De forma similar, Visual Studio filtra las funciones que se importan desde otros módulos o desde el espacio de nombres integrado. Por ejemplo, si un módulo importa la función `settrace` desde el módulo `sys`, en teoría podría importarla desde ese módulo. Pero es mejor usar `import settrace from sys` directamente, y así Visual Studio ofrece esa instrucción específicamente.

Por último, si algo se fuese a excluir normalmente, pero tiene otros valores que se incluirán (por ejemplo, porque al nombre se le ha asignado un valor en el módulo), Visual Studio sigue excluyendo la importación. Este comportamiento asume que el valor no debe exportarse porque está definido en otro módulo y, por tanto, es probable que la asignación adicional sea un valor ficticio que tampoco se exporta.

<a name="remove-imports"</a>

## <a name="remove-unused-imports"></a>Quitar importaciones no usadas

Al escribir código, resulta fácil terminar con instrucciones `import` para módulos que no se usan en absoluto. Dado que Visual Studio analiza el código, puede determinar automáticamente si una instrucción `import` es necesaria; basta con que vea si el nombre importado se usa dentro del ámbito siguiente donde se produce la instrucción.

Haga clic con el botón derecho en cualquier parte en un editor y seleccione **Remove Imports** (Quitar importaciones), que le proporciona opciones para quitar de **todos los ámbitos** o solo del **ámbito actual**:

![Menú para quitar importaciones](media/code-refactor-remove-imports-1.png)

Después, Visual Studio realiza los cambios adecuados en el código:

![Efecto de quitar importaciones](media/code-refactor-remove-imports-2.png)

Tenga en cuenta que Visual Studio no tiene en cuenta el flujo de control; el uso de un nombre delante de una instrucción `import` se tratará como si de hecho se usara el nombre. Visual Studio también omite todas las importaciones `from __future__`, importaciones que se realizan dentro de una definición de clase y de las instrucciones `from ... import *`.