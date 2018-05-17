---
title: Refactorización del código para convertir un bucle for en una instrucción foreach
ms.date: 05/10/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: douge
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: 34758473bcbee8ccad7d9dff9df2f1478ca1202c
ms.sourcegitcommit: 046a9adc5fa6d6d05157204f5fd1a291d89760b7
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/11/2018
---
# <a name="refactoring-to-convert-between-a-for-loop-and-a-foreach-statement"></a>Refactorización para convertir un bucle for en una instrucción foreach y viceversa

Estas refactorizaciones se aplican a:

- C#

## <a name="convert-a-for-loop-to-a-foreach-statement"></a>Convertir un bucle for en una instrucción foreach

Si tiene un bucle [for](/dotnet/csharp/language-reference/keywords/for) en el código, puede usar esta refactorización para convertirlo en una instrucción [foreach](/dotnet/csharp/language-reference/keywords/foreach-in).

### <a name="why-convert"></a>Motivos para efectuar la conversión

Estos son algunos de los motivos por los que le puede convenir convertir un bucle [for](/dotnet/csharp/language-reference/keywords/for) en una instrucción [foreach](/dotnet/csharp/language-reference/keywords/foreach-in):

- No usa la variable de recuento de iteraciones dentro del bucle salvo como índice para obtener acceso al elemento.

- Quiere simplificar el código y reducir la probabilidad de que se produzcan errores lógicos en las instrucciones de inicializador, condición e iteración.

### <a name="how-to-use-it"></a>Cómo se usa

1. Coloque el cursor en la primera línea del bucle `for`.

1. Presione **Ctrl**+**.** o haga clic en el icono del destornillador ![icono de destornillador](../media/screwdriver-icon.png) en el margen del archivo de código.

   ![Menú Convertir en "foreach"](media/convert-to-foreach.png)

1. Seleccione **Convertir en "foreach"**. También puede seleccionar **Vista previa de cambios** para abrir el cuadro de diálogo [Vista previa de cambios](../../ide/preview-changes.md) y, después, seleccionar **Aplicar**.

## <a name="convert-a-foreach-statement-to-a-for-loop"></a>Convertir una instrucción foreach en un bucle for

Si tiene una instrucción [foreach](/dotnet/csharp/language-reference/keywords/foreach-in) en el código, puede usar esta refactorización para convertirla en un bucle [for](/dotnet/csharp/language-reference/keywords/for).

### <a name="why-convert"></a>Motivos para efectuar la conversión

Estos son algunos de los motivos por los que le puede convenir convertir una instrucción [foreach](/dotnet/csharp/language-reference/keywords/foreach-in) en un bucle [for](/dotnet/csharp/language-reference/keywords/for):

- Quiere usar la variable de recuento de iteraciones dentro del bucle para hacer algo más que obtener acceso al elemento.

- Está [recorriendo en iteración una matriz multidimensional](/dotnet/csharp/programming-guide/arrays/using-foreach-with-arrays) y quiere tener más control sobre los elementos de la matriz.

### <a name="how-to-use-it"></a>Cómo se usa

1. Coloque el cursor en la primera línea de la instrucción `foreach`.

1. Presione **Ctrl**+**.** o haga clic en el icono del destornillador ![icono de destornillador](../media/screwdriver-icon.png) en el margen del archivo de código.

   ![Menú Convertir en "for"](media/convert-to-for.png)

1. Seleccione **Convertir en "for"**. También puede seleccionar **Vista previa de cambios** para abrir el cuadro de diálogo [Vista previa de cambios](../../ide/preview-changes.md) y, después, seleccionar **Aplicar**.

1. Dado que la refactorización introduce una nueva variable de recuento de iteraciones, en la esquina superior derecha del editor aparecerá el cuadro **Cambiar nombre**. Si quiere elegir otro nombre para la variable, escríbalo y presione **Entrar** o seleccione **Aplicar** en el cuadro **Cambiar nombre**. Si no quiere elegir un nombre nuevo, presione **Esc** o seleccione **Aplicar** para descartar el cuadro **Cambiar nombre**.

## <a name="see-also"></a>Vea también

- [Refactorización](../refactoring-in-visual-studio.md)
- [Vista previa de cambios](../../ide/preview-changes.md)