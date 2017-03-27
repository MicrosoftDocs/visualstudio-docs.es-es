---
title: "Reactorización de código en Herramientas de Python para Visual Studio | Microsoft Docs"
ms.custom: 
ms.date: 3/7/2017
ms.prod: visual-studio-dev15
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-python
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 76ebcb29-72d1-4958-9a63-8984c03d5c22
caps.latest.revision: 1
author: kraigb
ms.author: kraigb
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
translationtype: Human Translation
ms.sourcegitcommit: b0d84db6a16861fb9554af2a644423f906784748
ms.openlocfilehash: dc51f41277c91288c0812cb5c22f48d827d741aa
ms.lasthandoff: 03/07/2017

---

# <a name="refactoring-python-code"></a>Refactorización del código de Python

La utilidad Herramientas de Python para Visual Studio (PTVS) proporciona varios comandos para transformar y limpiar automáticamente el código fuente:

- [Cambiar nombre](#rename): cambia el nombre de la clase, el método o la variable seleccionados.
- [Extraer método](#extract-method): crea un nuevo método a partir del código seleccionado.
- [Agregar importación](#add-import): proporciona una etiqueta inteligente para agregar una importación que falta.
- [Quitar importaciones no usadas](#remove-imports): quita las importaciones no utilizadas.

<a name="rename-variable"</a>
## <a name="rename"></a>Cambiar nombre

1. Haga clic con el botón derecho en el identificador cuyo nombre desea cambiar y seleccione **Rename** (Cambiar nombre); o bien, coloque el símbolo de intercalación en ese identificador y seleccione el comando de menú **Edit > Refactor > Rename...** (Editar > Refactorizar > Cambiar nombre...) o presione F2.
1. En el diálogo **Rename** (Cambiar nombre) que aparece, escriba el nuevo nombre del identificador y seleccione **OK** (Aceptar):

  ![Mensaje de cambio de nombre para el nuevo nombre identificado](media/code-refactor-rename-1.png)

1. En el siguiente diálogo, seleccione los archivos y las instancias del código al que se va a aplicar el cambio de nombre; seleccione cualquier instancia individual para obtener una vista previa del cambio concreto:

  ![Diálogo de cambio de nombre para seleccionar dónde aplicar los cambios](media/code-refactor-rename-2.png)

1. Seleccione **Apply** (Aplicar) para realizar los cambios en los archivos de código fuente. Se trata de una acción que no se puede deshacer.

## <a name="extract-method"></a>Extraer método

1. Seleccione las líneas de código o la expresión para extraer a un método distinto.
1. Seleccione el comando de menú **Edit > Refactor > Extract method...** (Editar > Refactorizar > Extraer método...) o escriba Ctrl-R,M.
1. En el diálogo que aparece, escriba un nuevo nombre de método, indique dónde extraerlo y seleccione las variables de cierre. Las variables no seleccionadas para cierre se convierten en los argumentos de método:

  ![Diálogo de extracción de método](media/code-refactor-extract-method-1.png)

1. Seleccione **OK** (Aceptar); el código se modifica en consecuencia:

  ![Efecto de la extracción de un método](media/code-refactor-extract-method-2.png)

## <a name="add-import"></a>Agregar importación

Al colocar el símbolo de intercalación en un identificador que carece de información de tipo, PTVS proporciona una etiqueta inteligente (el icono de bombilla a la izquierda del código) cuyos comandos agregarán la instrucción `import` o `from ... import` necesaria:

![Agregar etiqueta inteligente de importación](media/code-refactor-add-import-1.png)

Las finalizaciones `import` se ofrecen para paquetes y módulos de nivel superior en el proyecto actual y la biblioteca estándar; las finalizaciones `from ... import` se ofrecerán para módulos y paquetes secundarios y para miembros de módulos. Esto incluye funciones, clases o datos exportados. Al seleccionar cualquier opción, se agrega la instrucción a la parte superior del archivo, detrás de otras importaciones, o a una instrucción `from ... import` existente si ya se importó el mismo módulo.

![Resultado de agregar una importación](media/code-refactor-add-import-2.png)

PTVS intenta filtrar miembros que no están definidos realmente en un módulo, como módulos que se importan en otros, pero no son elementos secundarios del módulo que realiza la importación. Por ejemplo, muchos módulos usan `import sys` en lugar de `from xyz import sys`, por lo que PTVS no ofrece una finalización para importar `sys` desde otros módulos, aunque a los módulos les falte un miembro `__all__` que excluye `sys`.

De forma similar, PTVS filtra las funciones que se importan desde otros módulos o desde el espacio de nombres integrado. Por ejemplo, si un módulo importa la función `settrace` desde el módulo `sys`, en teoría podría importarla desde ese módulo. Pero es mejor usar `import settrace from sys` directamente, y así PTVS ofrece esa instrucción específicamente.

Por último, si algo se va a excluir debido a las reglas anteriores, pero tiene otros valores que se incluirán (por ejemplo, porque al nombre se le asignó un valor en el módulo), PTVS sigue excluyendo la importación. Aquí se asume que el valor no debe exportarse porque está definido en otro módulo y, por tanto, es probable que la asignación adicional sea un valor ficticio que tampoco se exporta.

<a name="remove-imports"</a>
## <a name="remove-unused-imports"></a>Quitar importaciones no usadas

Al escribir código, resulta fácil terminar con instrucciones `import` para módulos que no se usan en absoluto. Dado que PTVS analiza el código, puede determinar automáticamente si una instrucción `import` es necesaria; basta con que vea si el nombre importado se usa dentro del ámbito siguiente donde se produce la instrucción.

Haga clic con el botón derecho en cualquier parte en un editor y seleccione **Remove Imports** (Quitar importaciones), que le proporciona opciones para quitar de **todos los ámbitos** o solo del **ámbito actual**:

![Menú para quitar importaciones](media/code-refactor-remove-imports-1.png)

PTVS realiza entonces los cambios adecuados en el código:

![Efecto de quitar importaciones](media/code-refactor-remove-imports-2.png)

Tenga en cuenta que PTVS no tiene en cuenta el flujo de control; el uso de un nombre delante de una instrucción `import` se tratará como si de hecho se usara el nombre. PTVS también omite todas las importaciones `from __future__`, importaciones que se realizan dentro de una definición de clase y de las instrucciones `from ... import *`.
