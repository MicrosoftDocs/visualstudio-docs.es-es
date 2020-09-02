---
title: 'Cómo: Ver y editar código mediante Definición de Peek (Alt+F12) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: 45f3dd20-902a-4047-8cca-9f18216123f4
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 40772919031200466999df2dfbf651fae3ee01e7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "72670567"
---
# <a name="how-to-view-and-edit-code-by-using-peek-definition-altf12"></a>Cómo: Ver y editar código mediante Definición de Peek (Alt+F12)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Puede usar el comando **Ver la definición** para ver y editar código sin salir del código que está escribiendo. **Ver la definición** e **Ir a definición** muestran la misma información, pero **Ver la definición** la muestra en una ventana emergente, mientras que **Ir a definición** muestra el código en una ventana de código independiente. **Ir a definición** hace que el contexto (es decir, la ventana de código activa, la línea actual y la posición del cursor) cambie a la ventana de código de definición. Mediante el uso de la **definición de PEEK**, puede ver y editar la definición y moverse por el archivo de definición manteniendo su lugar en el archivo de código original.

 Se puede usar **Ver la definición** con código de C#, Visual Basic y C++. En Visual Basic, **Ver la definición** muestra un vínculo al **Examinador de objetos** para los símbolos que no tienen metadatos de definición (por ejemplo, los tipos de .NET Framework integrados).

> [!IMPORTANT]
> No puede utilizar este comando en ninguna versión Express de Visual Studio 2013.

## <a name="working-with-peek-definition"></a>Trabajar con Ver la definición

#### <a name="to-open-a-peek-definition-window"></a>Para abrir una ventana Ver la definición

1. Puede encontrar **Ver la definición** si abre el menú contextual para un método que quiere explorar. (Teclado: Alt+F12)

     En esta ilustración se muestra la ventana **Ver la definición** para un método denominado `Print()`:

     ![Ventana de Peek](../ide/media/peekwindow.png "PeekWindow")

     La ventana de definición aparece debajo de la línea `printer.Print(“Hello World!”)` en el archivo original. La ventana no oculta ningún código del archivo original. Las líneas que siguen a la llamada `printer.Print(“Hello World!”)` aparecen bajo la ventana de definición.

2. Puede mover el cursor a distintas ubicaciones de la ventana de definición de código. Todavía puede moverse por la ventana de código original encima o debajo de la ventana de definición.

3. Puede copiar una cadena de la ventana de definición y pegarla en el código original. También puede arrastrar y colocar la cadena desde la ventana de definición al código original sin eliminarla de la ventana de definición.

4. Puede cerrar la ventana de definición eligiendo la tecla Esc o el botón **Cerrar** en la pestaña de la ventana de definición.

#### <a name="to-open-a-peek-definition-window-from-within-a-peek-definition-window"></a>Para abrir una ventana Ver la definición desde una ventana Ver la definición

- Si ya tiene abierta una ventana **Ver la definición**, puede llamar a **Ver la definición** de nuevo en el código de esa ventana. Se abre otra ventana de definición. Aparece un conjunto de puntos de ruta de navegación junto a la pestaña de la ventana de definición, que se puede utilizar para navegar entre las ventanas de definición. La información sobre herramientas de cada punto muestra el nombre de archivo y la ruta acceso del archivo de definición que el punto representa.

     ![Ventana de Peek dentro de una ventana de Peek](../ide/media/peekwithinpeek.png "PeekWithinPeek")

#### <a name="to-use-peek-definition-with-multiple-results"></a>Para usar Ver la definición con varios resultados

- Si usa **Ver la definición** en código que tiene varias definiciones (por ejemplo, clases parciales), aparece una lista de resultados a la derecha de la vista de definición de código. Puede elegir cualquier resultado de la lista para mostrar su definición.

     ![Ventana de Peek de varios resultados](../ide/media/peekmultiple.png "PeekMultiple")

#### <a name="to-edit-inside-the-peek-definition-window"></a>Para editar dentro de la ventana Ver la definición

- Cuando empieza a editar dentro de una ventana **Ver la definición**, el archivo que está modificando se abre automáticamente como una pestaña independiente en el editor de código y refleja los cambios que ya ha realizado. Puede seguir haciendo, deshaciendo y guardando cambios en la ventana **Ver la definición** y la pestaña continuará reflejando esos cambios. Incluso aunque cierre la ventana sin guardar los cambios, puede hacer, deshacer y guardar más cambios en la pestaña, eligiendo exactamente dónde se quedó en la ventana.

     ![Edición dentro de una ventana de Peek](../ide/media/peekedit.png "PeekEdit")

#### <a name="to-use-keyboard-shortcuts-for-peek-definition"></a>Para utilizar métodos abreviados de teclado para Ver la definición

- Puede usar estos métodos abreviados de teclado con la ventana **Ver la definición**:

    |Funcionalidad|Método abreviado de teclado|
    |-------------------|-----------------------|
    |Abrir la ventana de definición|Alt+F12|
    |Cerrar la ventana de definición|Esc|
    |Promover la ventana de definición a una pestaña de documento normal|Mayús+Alt+Inicio|
    |Navegar entre ventanas de definición|Ctrl+Alt+- y Ctrl+Alt+=|
    |Navegar entre varios resultados|F8 y Mayús+F8|
    |Alternar entre la ventana del editor de código y la ventana de definición|Mayús+Esc|

    > [!NOTE]
    > También puede usar los mismos métodos abreviados de teclado para editar código en una ventana **Ver la definición** como haría en otros lugares en Visual Studio.

## <a name="see-also"></a>Consulte también
 [Sugerencias de productividad](../ide/productivity-tips-for-visual-studio.md)
