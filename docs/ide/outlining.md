---
title: Contracción y expansión de regiones de código
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- outlining
- Visual Studio, expand/collapse code
- Visual Studio, outlining
- expand/collapse code
- code [Visual Studio], outlining
- code [Visual Studio], hiding
- outlining code
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 781c9a6bc30f7d3a29bcb89e743600e6b29e6445
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/01/2020
ms.locfileid: "75585761"
---
# <a name="outlining"></a>esquematizar

Se puede ocultar algún código de la vista si se contrae una región de código para que aparezca debajo de un signo más ( **+** ). Para expandir una región contraída hay que hacer clic en su signo más. Si prefiere usar el teclado, puede presionar **CTRL**+**M**+**M** para expandir o contraer. También se puede contraer una región de esquematización si se hace doble clic en cualquier línea de la región en el margen de esquematización, que aparece justo a la izquierda del código. Para ver el contenido de una región contraída como información sobre herramientas, hay que mantener el mouse sobre la región contraída.

> [!NOTE]
> Este tema se aplica a Visual Studio para Windows. En el caso de Visual Studio para Mac, vea [Editor de código fuente (Visual Studio para Mac)](/visualstudio/mac/source-editor).

Las regiones en el margen de esquematización también se resaltan cuando se mantiene el mouse sobre el margen. El color de resaltado predeterminado puede parecer bastante pálido en algunas configuraciones de color. Se puede cambiar en **Herramientas** > **Opciones** > **Entorno** > **Fuentes y colores** > **Región contraíble**.

Al trabajar en código esquematizado, se pueden expandir las secciones en las que se desea trabajar, contraerlas cuando se haya terminado y desplazarse a otras secciones. Cuando no quiere que se muestre la esquematización, se puede usar el comando **Detener esquematización** para quitar la información de esquematización sin alterar el código subyacente.

Los comandos **Deshacer** y **Rehacer** del menú **Edición** afectan a estas acciones. **Copiar**, **Cortar**, **Pegar** y las operaciones de arrastrar y colocar conservan la información de esquematización, pero no el estado de la región contraíble. Por ejemplo, cuando copia una región que se contrae, la operación **Pegar** pegará el texto copiado como región expandida.

> [!CAUTION]
> Si se cambia una región esquematizada, se puede perder la esquematización. Por ejemplo, las eliminaciones o las operaciones Buscar y reemplazar pueden borrar el final de la región.

El submenú **Edición** > **Esquematización** contiene los siguientes comandos.

|||
|-|-|
|Ocultar selección|(**Ctrl**+**M**, **Ctrl**+**H**): contrae un bloque de código seleccionado que normalmente no estaría disponible para la esquematización, por ejemplo un bloque `if`. Para quitar la región personalizada, use **Detener ocultar actual** (o **Ctrl**+**M**, **Ctrl**+**U**). No está disponible en Visual Basic.|
|Alternar expansión de esquematización|: invierte el estado oculto o expandido actual de la sección de esquematización más interna cuando el cursor se encuentra en una sección contraída anidada.|
|Alternar toda la esquematización|(**Ctrl**+**M**, **Ctrl**+**L**): establece todas las regiones en el mismo estado contraído o expandido. Si algunas regiones están expandidas y otras están contraídas, las regiones contraídas se expanden.|
|Detener esquematización|(**Ctrl**+**M**, **Ctrl**+**P**): quita toda la información de esquematización del documento completo.|
|Detener ocultar actual|(**Ctrl**+**M**, **Ctrl**+**U**): quita la información de esquematización de la región definida por el usuario que está seleccionada actualmente. No está disponible en Visual Basic.|
|Contraer a definiciones|(**Ctrl**+**M**, **Ctrl**+**O**): contrae los miembros de todos los tipos.|
|Contraer bloque:\<límite lógico>|(C++) Contrae una región en la función que contiene el punto de inserción. Por ejemplo, si el punto de inserción está dentro de un bucle, se oculta el bucle.|
|Contraer todo el contenido de: \<estructuras lógicas>|(C++) Contrae todas las estructuras dentro de la función.|

También puede utilizar Visual Studio SDK para definir las regiones de texto que desea expandir o contraer. Vea [Tutorial: Esquematización](../extensibility/walkthrough-outlining.md).

## <a name="see-also"></a>Vea también

- [Características del editor de código](../ide/writing-code-in-the-code-and-text-editor.md)
- [Editor de código fuente (Visual Studio para Mac)](/visualstudio/mac/source-editor)
