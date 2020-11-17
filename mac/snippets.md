---
title: Fragmentos de código
description: Cómo usar fragmentos de código para programar de forma eficaz en Visual Studio para Mac
author: jmatthiesen
ms.author: jomatthi
ms.date: 11/09/2020
ms.assetid: 0FE27C0C-A861-4133-A74E-8D0505CF5342
ms.openlocfilehash: a8fdf70b4d966c644719047eca4249e432561ace
ms.sourcegitcommit: 2cf3a03044592367191b836b9d19028768141470
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/11/2020
ms.locfileid: "94493457"
---
# <a name="code-snippets"></a>Fragmentos de código

Los fragmentos de código, que se suelen denominar _plantillas de código_, son útiles para una programación eficaz, ya que permiten la inserción y edición de bloques de código escritos previamente. El uso de fragmentos de código puede resultar cómodo para agregar rápidamente patrones comunes o incluso para aprender nuevos patrones si, como desarrollador, no está seguro de la sintaxis. Hay plantillas para C#, F#, HTML, XML, Python y Razor.

En esta sección se explica cómo crear, insertar y usar fragmentos de código en el código.

## <a name="inserting-a-snippet"></a>Insertar un fragmento de código

Hay varias maneras de agregar fragmentos de código, algunas de las cuales se explican a continuación:

- **Expansión de tabulación**: empiece a escribir el nombre de la plantilla, selecciónela en la lista y presione **Tab**, **Tab** para agregarla:

  ![Expansión de tabulación en código](media/source-editor-image13.png)

- **Cuadro de herramientas**: use la ventana Cuadro de herramientas para mostrar una lista de todos los fragmentos de código. Arrastre cualquier plantilla desde el cuadro de herramientas a la posición correcta del código fuente:

  [![Fragmentos de código en el cuadro de herramientas](media/source-editor-image14-sml.png)](media/source-editor-image14.png#lightbox)

- **Comando Insertar plantillas**: actualmente no hay ningún enlace de teclado predeterminado para insertar una plantilla. Para crear uno, vaya a **Visual Studio > Preferencias > Enlaces de teclado** y busque `template`. Esto permite agregar el enlace de teclado deseado en el campo Editar enlace; luego, haga clic en **Aplicar**:

  ![Comando Insertar plantilla](media/source-editor-image15.png)

## <a name="creating-a-new-template"></a>Crear una nueva plantilla

Aunque hay muchas plantillas existentes en una serie de lenguajes que se pueden usar y editar, también se pueden agregar nuevas plantillas si se va a **Visual Studio > Preferencias > Editor de texto > Fragmentos de código**:

![Insertar nueva plantilla](media/source-editor-image12.png)

Presione los botones **Agregar** o **Editar** para crear o editar fragmentos de código.

## <a name="keywords-in-code-snippets"></a>Palabras clave en fragmentos de código

Después de insertar un fragmento de código en el editor, cualquier palabra clave definida se resalta y se puede editar mediante el uso del tabulador para pasar de una a otra. Las palabras clave se comportan como una "variable" en el fragmento de código y se definen colocando un signo de dólar `$` antes y después del nombre de la palabra clave. 

A continuación se muestra la ventana **Editar plantilla**, con la edición del fragmento de código `prop` integrado. El fragmento de código contiene dos palabras clave &ndash;`$type$` y `$name$`&ndash; que pueden tener un conjunto de propiedades adicionales (como un valor predeterminado e información sobre herramientas) en el lado derecho de la ventana:

![Ventana Editar plantilla](media/source-editor-image12z.png)

Los siguientes campos se usan para definir un fragmento de código:

- **Shortcut** (Método abreviado): el texto que el usuario escribe para insertar el fragmento de código.
- **Group** (Grupo): los fragmentos de código que se agrupan en el menú de contenido del fragmento de código usan este valor.
- **Description** (Descripción): explicación del propósito del fragmento de código.
- **Mime**: controla en qué tipos de archivo está disponible el fragmento de código.
- **Is expandable template** (Es la plantilla expandible): asegúrese de que esta opción está activada para que el fragmento de código se puede insertar en la posición del cursor escribiendo el acceso directo.
- **Is surround with template** (Está rodeado con plantilla): active esta opción para mostrar este acceso directo en el menú de contenido **Surround with...**  (Rodear con) en el editor.
- **Template text** (Texto de la plantilla): el fragmento de código real que se insertará en el editor. Se pueden definir dos marcadores de posición de palabras clave al rodear un token con signos de dólar, por ejemplo, `$type$`.
- **Keyword property panel** (Panel de propiedades de palabras clave): en el lado derecho de la ventana, utilice la lista desplegable de la parte superior para elegir una palabra clave (por ejemplo, `type`) y editar propiedades como el valor predeterminado y la información sobre herramientas.

## <a name="using-keywords-in-the-editor"></a>Uso de palabras clave en el editor

Para utilizar un fragmento de código con palabras clave, como la definida anteriormente, escriba el acceso directo y presione la tecla **Tab** dos veces y el contenido del fragmento de código se insertará en el cursor:

![Fragmento de código insertado, que muestra las palabras clave](media/source-editor-image12a.png)

Presione la tecla **Tab** para moverse entre `object` y `MyProperty`, con el fin de personalizar el fragmento de código para la clase.

Una palabra clave puede repetirse en un fragmento de código, como este ejemplo `for`, observe que la palabra clave `$i$` aparece tres veces:

![Plantilla de fragmento de código con palabras clave repetidas](media/source-editor-image12b.png)

Cuando se usa en el editor, la tecla **Tab** cambiará entre la primera `i` y `max`. Si sobrescribe `i` con otro nombre de variable, se actualizarán las tres instancias:

![Fragmento de código insertado, que muestra varias palabras clave](media/source-editor-image12c.png)

### <a name="reserved-keywords"></a>Palabras clave reservadas

Hay dos palabras clave reservadas que se puede usar en un fragmento de código:

- `$selected$`: si el fragmento de código tiene activada la opción **Is surround with template** (Está rodeado con plantilla), esta palabra clave se reemplazará por el texto que estaba resaltado en el editor cuando se eligió el fragmento de código.
- `$end$`: cuando el usuario haya terminado de editar las palabras clave de un fragmento de código, el cursor se colocará en la ubicación de la palabra clave `$end$`.

El fragmento de código `for` de la sección anterior es un ejemplo de estas dos palabras clave reservadas.

## <a name="see-also"></a>Consulte también

- [Fragmentos de código (Visual Studio en Windows)](/visualstudio/ide/code-snippets)
