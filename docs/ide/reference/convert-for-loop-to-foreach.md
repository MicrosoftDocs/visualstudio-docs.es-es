---
title: Refactorización del código para convertir un bucle for en una instrucción foreach
ms.date: 05/10/2018
ms.topic: reference
author: TerryGLee
ms.author: tglee
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: 3539bae5bb2174fa4728fb8b277cce4ce9c48eb9
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/01/2020
ms.locfileid: "75570250"
---
# <a name="refactoring-to-convert-between-a-for-loop-and-a-foreach-statement"></a>Refactorización para convertir un bucle for en una instrucción foreach y viceversa

En este artículo se describen las refactorizaciones de acciones rápidas que realizan la conversión entre dos estructuras de bucles. Incluye algunas razones por las que podría interesarle cambiar entre un bucle [for](/dotnet/csharp/language-reference/keywords/for) y una instrucción [foreach](/dotnet/csharp/language-reference/keywords/foreach-in) en el código.

## <a name="convert-a-for-loop-to-a-foreach-statement"></a>Convertir un bucle for en una instrucción foreach

Si tiene un bucle [for](/dotnet/csharp/language-reference/keywords/for) en el código, puede usar esta refactorización para convertirlo en una instrucción [foreach](/dotnet/csharp/language-reference/keywords/foreach-in).

Esta refactorización se aplica a lo siguiente:

- C#

> [!NOTE]
> La refactorización de acción rápida **Convertir en "foreach"** solo está disponible para bucles [for](/dotnet/csharp/language-reference/keywords/for) que contienen los tres elementos: un inicializador, la condición y el iterador.

### <a name="why-convert"></a>Motivos para efectuar la conversión

Estos son algunos de los motivos por los que le puede convenir convertir un bucle [for](/dotnet/csharp/language-reference/keywords/for) en una instrucción [foreach](/dotnet/csharp/language-reference/keywords/foreach-in):

- No use la variable de bucle local dentro del bucle salvo como índice para obtener acceso a elementos.

- Quiere simplificar el código y reducir la probabilidad de que se produzcan errores lógicos en las secciones de inicializador, condición e iterador.

### <a name="how-to-use-it"></a>Cómo se usa

1. Coloque el símbolo de inserción en la palabra clave `for`.

1. Presione **Ctrl**+ **.** o haga clic en el icono del destornillador ![icono de destornillador](../media/screwdriver-icon.png) en el margen del archivo de código.

   ![Menú Convertir en "foreach"](media/convert-to-foreach.png)

1. Seleccione **Convertir en "foreach"** . También puede seleccionar **Vista previa de cambios** para abrir el cuadro de diálogo [Vista previa de cambios](../../ide/preview-changes.md) y, después, seleccionar **Aplicar**.

## <a name="convert-a-foreach-statement-to-a-for-loop"></a>Convertir una instrucción foreach en un bucle for

Si tiene una instrucción [foreach (C#)](/dotnet/csharp/language-reference/keywords/foreach-in) o [For Each...Next (Visual Basic)](/dotnet/visual-basic/language-reference/statements/for-each-next-statement) en el código, puede usar esta refactorización para convertirla en un bucle [for](/dotnet/csharp/language-reference/keywords/for).

Esta refactorización se aplica a lo siguiente:

- C#

- Visual Basic

### <a name="why-convert"></a>Motivos para efectuar la conversión

Estos son algunos de los motivos por los que le puede convenir convertir una instrucción [foreach](/dotnet/csharp/language-reference/keywords/foreach-in) en un bucle [for](/dotnet/csharp/language-reference/keywords/for):

- Quiere usar la variable de bucle local dentro del bucle para hacer algo más que obtener acceso al elemento.

- Está [recorriendo en iteración una matriz multidimensional](/dotnet/csharp/programming-guide/arrays/using-foreach-with-arrays) y quiere tener más control sobre los elementos de la matriz.

### <a name="how-to-use-it"></a>Cómo se usa

1. Coloque el símbolo de inserción en la palabra clave `foreach` o `For Each`.

1. Presione **Ctrl**+ **.** o haga clic en el icono del destornillador ![icono de destornillador](../media/screwdriver-icon.png) en el margen del archivo de código.

   ![Menú Convertir en "for"](media/convert-to-for.png)

1. Seleccione **Convertir en "for"** . También puede seleccionar **Vista previa de cambios** para abrir el cuadro de diálogo [Vista previa de cambios](../../ide/preview-changes.md) y, después, seleccionar **Aplicar**.

1. Dado que la refactorización introduce una nueva variable de recuento de iteraciones, en la esquina superior derecha del editor aparecerá el cuadro **Cambiar nombre**. Si quiere elegir otro nombre para la variable, escríbalo y presione **Entrar** o seleccione **Aplicar** en el cuadro **Cambiar nombre**. Si no quiere elegir un nombre nuevo, presione **Esc** o seleccione **Aplicar** para descartar el cuadro **Cambiar nombre**.

> [!NOTE]
> En C#, el código generado por estas refactorizaciones usa un tipo explícito o [var](/dotnet/csharp/language-reference/keywords/var) como tipo de los elementos de la colección. El tipo en el código generado, explícito o implícito, depende de la configuración de estilo de código que queda dentro del ámbito. Estas opciones de estilo de código concretas se configuran en el nivel de máquina en **Herramientas** > **Opciones** > **Editor de texto** > **C#**  > **Estilo de código** > **General** > **Preferencias de \'var'** o en el nivel de solución en un archivo [EditorConfig](../../ide/editorconfig-language-conventions.md#implicit-and-explicit-types). Si cambia una configuración de estilo de código en **Opciones**, vuelva a abrir el archivo de código para que los cambios surtan efecto.

## <a name="see-also"></a>Vea también

- [Refactorización](../refactoring-in-visual-studio.md)
- [Vista previa de cambios](../../ide/preview-changes.md)
