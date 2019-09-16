---
title: 'Paso 11: Ejecución de la aplicación y prueba de otras características'
ms.date: 08/30/2019
ms.assetid: 656614d0-4fe7-4a67-8edc-c10919377d09
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
ms.devlang:
- csharp
- vb
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3e82e0002255a406f02f85cbb2636be1aa249529
ms.sourcegitcommit: 4dfe098ac0df294aad63e6b384d6575980798ca3
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/11/2019
ms.locfileid: "70887952"
---
# <a name="step-11-run-your-app-and-try-other-features"></a>Paso 11: Ejecución de la aplicación y prueba de otras características

La aplicación está finalizada y lista para ejecutarse. Puede ejecutarla y establecer el color de fondo del control <xref:System.Windows.Forms.PictureBox>. Para obtener más información e intentar mejorar la aplicación, cambie el color del formulario, personalice los botones y la casilla, y cambie las propiedades del formulario.

## <a name="how-to-run-your-app-and-set-the-background-color"></a>Procedimientos para ejecutar la aplicación y establecer el color de fondo

1. Pulse **F5** o, en la barra de menús, pulse **Depurar** > **Iniciar depuración**.

1. Antes de abrir una imagen, pulse el botón **Establecer el color de fondo**. Se abrirá el cuadro de diálogo **Color**.

     ![Cuadro de diálogo Color](../ide/media/express_colordialog.png)<br/>
*Cuadro de diálogo* ***Color***

1. Elija un color para establecer el color de fondo de PictureBox. Fíjese con atención en el método `backgroundButton_Click()` (o `BackgroundButton_Click()`) para entender cómo funciona.

    > [!NOTE]
    > Puede cargar una imagen de Internet pegando su dirección URL en el cuadro de diálogo **Abrir archivo**. Intente encontrar una imagen con un fondo transparente, para que se vea el color de fondo.

1. Elija el botón **Borrar la imagen** para asegurarse de que se borra. Después, seleccione el botón **Cerrar** para salir de la aplicación.

## <a name="try-other-features"></a>Probar otras características

* Cambie el color del formulario y de los botones mediante la propiedad **BackColor**.

* Personalice sus botones y la casilla mediante las propiedades **Font** y **ForeColor**.

* Cambie las propiedades **FormBorderStyle** y **ControlBox** del formulario.

* Use las propiedades **AcceptButton** y **CancelButton** del formulario para que, cuando el usuario pulse la tecla **Entrar** o **Esc**, los botones se seleccionen automáticamente. Haga que la aplicación abra el cuadro de diálogo **Abrir archivo** cuando el usuario presione **Entrar** y que lo cierre cuando presione **Esc**.

## <a name="next-steps"></a>Pasos siguientes

Para obtener más información, continúe con el tutorial siguiente:

> [!div class="nextstepaction"]
> [Tutorial 2: Creación de una prueba matemática cronometrada](../ide/tutorial-2-create-a-timed-math-quiz.md)

Para volver al paso anterior del tutorial, vea [Paso 10: Escribir código para botones adicionales y una casilla](../ide/step-10-write-code-for-additional-buttons-and-a-check-box.md).

## <a name="see-also"></a>Vea también

* [Más tutoriales de C#](/visualstudio/get-started/csharp/)
* [Más tutoriales de Visual Basic](/visualstudio/get-started/visual-basic/)
* [Tutorial de C++](../ide/getting-started-with-cpp-in-visual-studio.md)
