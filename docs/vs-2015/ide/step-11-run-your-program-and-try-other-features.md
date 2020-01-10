---
title: 'Paso 11: Ejecutar el programa y probar otras características | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: 656614d0-4fe7-4a67-8edc-c10919377d09
caps.latest.revision: 14
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: bff0467cfe9447b1cc7814d471f56ab323bb853d
ms.sourcegitcommit: c150d0be93b6f7ccbe9625b41a437541502560f5
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/10/2020
ms.locfileid: "75851579"
---
# <a name="step-11-run-your-program-and-try-other-features"></a>Paso 11: Ejecutar el programa y probar otras características
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

El programa está finalizado y listo para ejecutarse. Puede ejecutar el programa y establecer el color de fondo del control PictureBox. Para aprender más, intente mejorar el programa cambiando el color del formulario, personalizando los botones y la casilla, y cambiando las propiedades del formulario.

 ![vínculo a vídeo](../data-tools/media/playvideo.gif "PlayVideo") Para obtener una versión en vídeo de este tema, vea el [tutorial 1: crear un visor de imágenes en Visual Basic-vídeo 5 o el](https://msdn.microsoft.com/vbasic/gg315356.aspx) [tutorial 1: C# crear un visor de imágenes en-vídeo 5](https://msdn.microsoft.com/vcsharp/gg278413.aspx). En estos vídeos se utilizó una versión anterior de Visual Studio, por lo que hay ligeras diferencias en algunos comandos de menú y otros elementos de la interfaz de usuario. Sin embargo, los conceptos y procedimientos funcionan de forma similar en la versión actual de Visual Studio.

### <a name="to-run-your-program-and-set-the-background-color"></a>Para ejecutar el programa y establecer el color de fondo

1. Pulse F5 o, en la barra de menús, pulse **Depurar**, **Iniciar depuración**.

2. Antes de abrir una imagen, pulse el botón **Establecer el color de fondo**. Se abrirá el cuadro de diálogo **Color**.

     ![Color (cuadro de diálogo)](../ide/media/express-colordialog.png "Express_ColorDialog") Color (cuadro de diálogo)

3. Elija un color para establecer el color de fondo de PictureBox. Fíjese con atención en el método `backgroundButton_Click()` para entender cómo funciona.

    > [!NOTE]
    > Puede cargar una imagen de Internet pegando su dirección URL en el cuadro de diálogo **Abrir archivo**. Intente encontrar una imagen con un fondo transparente, para que se vea el color de fondo.

4. Elija el botón **Borrar la imagen** para asegurarse de que se borra. Después, salga del programa pulsando el botón **Cerrar**.

### <a name="to-try-other-features"></a>Para probar otras características

- Cambie el color del formulario y de los botones mediante la propiedad **BackColor**.

- Personalice sus botones y la casilla mediante las propiedades **Font** y **ForeColor**.

- Cambie las propiedades **FormBorderStyle** y **ControlBox** del formulario.

- Use las propiedades **AcceptButton** y **CancelButton** del formulario para que, cuando el usuario pulse la tecla ENTRAR o ESC, los botones se seleccionen automáticamente. Haga que el programa abra el cuadro de diálogo **Abrir archivo** cuando el usuario pulse ENTRAR y que lo cierre cuando el usuario pulse ESC.

### <a name="to-continue-or-review"></a>Para continuar o revisar

- Para obtener más información sobre la programación en Visual Studio, vea [Programar los conceptos](https://msdn.microsoft.com/library/65c12cca-af4f-4017-886e-2dbc00a189d6).

- Para obtener más información sobre Visual Basic, vea [Desarrollo de aplicaciones con Visual Basic](https://msdn.microsoft.com/library/1e1c0c81-6d95-4167-a98b-44b1efb6d25f).

- Para obtener más información sobre Visual C#, vea [Introducción al lenguaje C# y .NET Framework](https://msdn.microsoft.com/library/0a2dff4e-cd84-42ff-8141-e89889b24081).

- Para ir al siguiente tutorial, vea [Tutorial 2: Crear una prueba matemática cronometrada](../ide/tutorial-2-create-a-timed-math-quiz.md).

- Para volver al paso anterior del tutorial, vea [Paso 10: Escribir código para botones adicionales y una casilla](../ide/step-10-write-code-for-additional-buttons-and-a-check-box.md).
