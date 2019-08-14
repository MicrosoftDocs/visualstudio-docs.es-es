---
title: 'Paso 11: Ejecutar el programa y probar otras características'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 656614d0-4fe7-4a67-8edc-c10919377d09
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 43cb58c65131b5cc7e01b0f59306761a3b275dc7
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/09/2019
ms.locfileid: "68925918"
---
# <a name="step-11-run-your-program-and-try-other-features"></a>Paso 11: Ejecutar el programa y probar otras características
El programa está finalizado y listo para ejecutarse. Puede ejecutar el programa y establecer el color de fondo del control <xref:System.Windows.Forms.PictureBox>. Para aprender más, intente mejorar el programa cambiando el color del formulario, personalizando los botones y la casilla, y cambiando las propiedades del formulario.

Para descargar una versión completa del ejemplo, vea [Complete Picture Viewer tutorial sample](https://code.msdn.microsoft.com/Complete-Picture-Viewer-7d91d3a8) (Ejemplo completo del tutorial de visor de imágenes).

![vínculo al vídeo](../data-tools/media/playvideo.gif)Para obtener una versión en vídeo de este tema, vea [Tutorial 1: Crear un visor de imágenes en Visual Basic - Vídeo 5](http://go.microsoft.com/fwlink/?LinkId=205216) o [Tutorial 1: Crear un visor de imágenes en C# - Vídeo 5](http://go.microsoft.com/fwlink/?LinkId=205206). En estos vídeos se utilizó una versión anterior de Visual Studio, por lo que hay ligeras diferencias en algunos comandos de menú y otros elementos de la interfaz de usuario. Sin embargo, los conceptos y procedimientos funcionan de forma similar en la versión actual de Visual Studio.

## <a name="to-run-your-program-and-set-the-background-color"></a>Para ejecutar el programa y establecer el color de fondo

1. Pulse **F5** o, en la barra de menús, pulse **Depurar** > **Iniciar depuración**.

2. Antes de abrir una imagen, pulse el botón **Establecer el color de fondo**. Se abrirá el cuadro de diálogo **Color**.

     ![Cuadro de diálogo Color](../ide/media/express_colordialog.png)
Cuadro de diálogo **Color**

3. Elija un color para establecer el color de fondo de PictureBox. Fíjese con atención en el método `backgroundButton_Click()` para entender cómo funciona.

    > [!NOTE]
    > Puede cargar una imagen de Internet pegando su dirección URL en el cuadro de diálogo **Abrir archivo**. Intente encontrar una imagen con un fondo transparente, para que se vea el color de fondo.

4. Elija el botón **Borrar la imagen** para asegurarse de que se borra. Después, salga del programa pulsando el botón **Cerrar**.

## <a name="to-try-other-features"></a>Para probar otras características

- Cambie el color del formulario y de los botones mediante la propiedad **BackColor**.

- Personalice sus botones y la casilla mediante las propiedades **Font** y **ForeColor**.

- Cambie las propiedades **FormBorderStyle** y **ControlBox** del formulario.

- Use las propiedades **AcceptButton** y **CancelButton** del formulario para que, cuando el usuario pulse la tecla **Entrar** o **Esc**, los botones se seleccionen automáticamente. Haga que el programa abra el cuadro de diálogo **Abrir archivo** cuando el usuario pulse **Entrar** y que lo cierre cuando el usuario pulse **Esc**.

## <a name="to-continue-or-review"></a>Para continuar o revisar

- Para obtener más información sobre la programación en Visual Studio, vea [Programar los conceptos](https://msdn.microsoft.com/Library/65c12cca-af4f-4017-886e-2dbc00a189d6).

- Para obtener más información sobre Visual Basic, vea [Desarrollo de aplicaciones con Visual Basic](/dotnet/visual-basic/developing-apps/index).

- Para obtener más información sobre Visual C#, vea [Introducción al lenguaje C# y .NET Framework](/dotnet/csharp/getting-started/introduction-to-the-csharp-language-and-the-net-framework).

- Para ir al siguiente tutorial, vea [Tutorial 2: Crear una prueba matemática cronometrada](../ide/tutorial-2-create-a-timed-math-quiz.md).

- Para volver al paso anterior del tutorial, vea [Paso 10: Escribir código para botones adicionales y una casilla](../ide/step-10-write-code-for-additional-buttons-and-a-check-box.md).
