---
title: 'Paso 5: agregar controladores de eventos Enter para los controles NumericUpDown'
ms.date: 11/04/2016
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
dev_langs:
- CSharp
- VB
ms.assetid: 45a99a5d-c881-4298-b74d-adb481dec5ee
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 17fb9ba8e82739ddb0a420f52b6f7f945a6454b8
ms.sourcegitcommit: 2ae2436dc3484b9dfa10e0483afba1e5a02a52eb
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/25/2020
ms.locfileid: "77579833"
---
# <a name="step-5-add-enter-event-handlers-for-the-numericupdown-controls"></a>Paso 5: Agregar controladores de eventos Enter para los controles NumericUpDown

En la quinta parte de este tutorial, agregará <xref:System.Windows.Forms.Control.Enter> controladores de eventos Enter para hacer que sea un poco más fácil escribir las respuestas a los problemas de la prueba. Este código seleccionará y borrará el valor actual de cada uno de los controles <xref:System.Windows.Forms.NumericUpDown> en cuanto el jugador lo elija y comience a escribir un valor diferente.

> [!NOTE]
> Este tema forma parte de una serie de tutoriales sobre conceptos de codificación básicos. Para obtener información general sobre el tutorial, vea [Tutorial 2: Crear una prueba matemática cronometrada](../ide/tutorial-2-create-a-timed-math-quiz.md).

## <a name="to-verify-the-default-behavior"></a>Para comprobar el comportamiento predeterminado

1. Ejecute el programa e inicie la prueba.

     En el control **NumericUpDown** del problema de suma, el cursor parpadea junto a **0** (cero).

2. Escriba **3** y observe que en el control aparece **30**.

3. Escriba **5** y observe que aparece **350**, aunque cambia a **100** después de un segundo.

     Antes de corregir este problema, piense en lo que está sucediendo. Piense por qué no desapareció **0** cuando escribió **3** y por qué **350** cambió a **100**, aunque esto no sucedió inmediatamente.

     Este comportamiento puede parecer extraño, pero tiene sentido dada la lógica del código. Al pulsar el botón **Iniciar**, la propiedad **Enabled** del botón está establecida en **False**; y el botón aparece atenuado y no está disponible. El programa cambia la selección actual (foco) al control que tiene el siguiente valor TabIndex más bajo, que es el control NumericUpDown del problema de suma. Al presionar la tecla **Tab** para ir a un control NumericUpDown, el cursor se coloca automáticamente al principio del control; este es el motivo por el cual los números que se escriben aparecen en el lado izquierdo y no en el derecho. Cuando se especifica un número mayor que el valor de la propiedad **MaximumValue**, que está establecida en 100, el número especificado se reemplaza por el valor de esta propiedad.

## <a name="to-add-an-enter-event-handler-for-a-numericupdown-control"></a>Para agregar un controlador de eventos Enter en un control NumericUpDown

1. Pulse el primer control **NumericUpDown** (denominado "suma") del formulario y, después, en el cuadro de diálogo **Propiedades**, pulse el icono **Eventos** de la barra de herramientas.

   ![Botón Eventos en la barra de herramientas de propiedades](media/control-properties-events.png)

   En la pestaña **Eventos** del cuadro de diálogo **Propiedades** se muestran todos los eventos del elemento elegido en el formulario a los que se puede responder (que pueden controlarse). Dado que eligió el control NumericUpDown, todos los eventos enumerados pertenecen a ese control.

2. Seleccione el evento **Entrar**, escriba `answer_Enter` y, después, presione la tecla **Entrar**.

   ![Escriba el nombre del método del controlador de eventos.](media/enter-event.png)

   Acaba de agregar un controlador de eventos Enter para el control NumericUpDown de suma y ha denominado el controlador **answer_Enter**.

3. En el método del controlador de eventos **answer_Enter**, agregue el código siguiente:

     [!code-vb[VbExpressTutorial3Step5_6#11](../ide/codesnippet/VisualBasic/step-5-add-enter-event-handlers-for-the-numericupdown-controls_1.vb)]
     [!code-csharp[VbExpressTutorial3Step5_6#11](../ide/codesnippet/CSharp/step-5-add-enter-event-handlers-for-the-numericupdown-controls_1.cs)]

     [!INCLUDE [devlang-control-csharp-vb](./includes/devlang-control-csharp-vb.md)]

     Este código puede parecer complejo, pero puede entenderlo si lo examina paso a paso. En primer lugar, fíjese en la parte superior del método: `object sender` en C# o `sender As System.Object` en Visual Basic. Este parámetro hace referencia al objeto que tiene el evento que se genera, lo que se conoce como remitente. En este caso, el objeto remitente es el control NumericUpDown. Por lo tanto, en la primera línea del método, se especifica que el remitente no es simplemente un objeto genérico, sino que se trata específicamente de un control NumericUpDown. (Cada control NumericUpDown es un objeto, pero no todos los objetos son un control NumericUpDown.) El control NumericUpDown se denomina **answerBox** en este método, porque se usará para todos los controles NumericUpDown del formulario, no solo para el control NumericUpDown de suma. Dado que la variable answerBox se declara en este método, su ámbito solo se aplica a este método. Es decir, la variable solo se puede utilizar en este método.

     En la línea siguiente se comprueba si se ha llevado a cabo correctamente la conversión (de tipos) de answerBox: de un objeto a un control NumericUpDown. Si la conversión fuera incorrecta, la variable tendría un valor de `null` (en C#) o de `Nothing` (en Visual Basic). La tercera línea obtiene la longitud de la respuesta que aparece en el control NumericUpDown y la cuarta línea selecciona el valor actual del control en función de esa longitud. Ahora, cuando el jugador elige el control, Visual Studio genera este evento, con lo que se selecciona la respuesta actual. En cuanto el jugador empiece a escribir otra respuesta, se borrará la respuesta anterior y se reemplazará por la nueva.

4. En el **Diseñador de Windows Forms**, elija el control **NumericUpDown** de resta.

5. En la página **Eventos** del cuadro de diálogo **Propiedades**, desplácese hacia abajo hasta el evento **Enter**, seleccione la flecha de lista desplegable al final de la fila y, después, pulse el controlador de eventos `answer_Enter` que acaba de agregar.

6. Repita el paso anterior para los controles NumericUpDown de producto y cociente.

7. Guarde el programa y ejecútelo.

     Al elegir un control **NumericUpDown**, el valor existente se selecciona automáticamente y se borra cuando empieza a escribir un valor diferente.

## <a name="to-continue-or-review"></a>Para continuar o revisar

- Para ir al siguiente paso del tutorial, consulte **[Paso 6: Agregar un problema de resta](../ide/step-6-add-a-subtraction-problem.md)** .

- Para volver al paso anterior del tutorial, vea [Paso 4: Agregar el método CheckTheAnswer()](../ide/step-4-add-the-checktheanswer-parens-method.md).
