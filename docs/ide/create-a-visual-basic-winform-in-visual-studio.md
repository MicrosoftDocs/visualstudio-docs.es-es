---
title: Creación de una aplicación de Windows Forms con Visual Basic
description: Aprenda a crear una aplicación de Windows Forms en Visual Studio con Visual Basic, paso a paso.
ms.date: 12/04/2017
ms.prod: visual-studio-dev15
ms.topic: conceptual
ms.devlang: vb
author: TerryGLee
ms.author: tglee
manager: douge
dev_langs:
- vb
ms.workload:
- multiple
ms.openlocfilehash: 6b2844f876377e1b875a2086a1fad6c3809bd3af
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53870302"
---
# <a name="create-a-windows-forms-app-in-visual-studio-with-visual-basic"></a>Creación de una aplicación de Windows Forms en Visual Studio con Visual Basic

En esta breve introducción al entorno de desarrollo integrado de Visual Studio, creará una sencilla aplicación de Visual Basic que tiene una interfaz de usuario (IU) basada en Windows.

Si todavía no tiene instalado Visual Studio, vaya a la página de [descargas de Visual Studio](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) para instalarlo de forma gratuita.

## <a name="create-a-project"></a>Crear un proyecto

En primer lugar, crearemos un proyecto de aplicación de Visual Basic. En el tipo de proyecto se incluyen todos los archivos de plantilla que vamos a necesitar, sin necesidad de agregar nada más.

1. Abra Visual Studio 2017.

2. En la barra de menús superior, seleccione **Archivo** > **Nuevo** > **Proyecto**.

3. En el cuadro de diálogo **Nuevo proyecto** del panel izquierdo, expanda **Visual Basic** y seleccione **Escritorio de Windows**. En el panel central, elija **Aplicación de Windows Forms (.NET Framework)**. Luego, asigne al archivo el nombre `HelloWorld`.

     Si no ve la plantilla de proyecto **Aplicación de Windows Forms (.NET Framework)**, cancele haciendo clic fuera del cuadro de diálogo **Nuevo proyecto** y, en la barra de menús superior, elija **Herramientas** > **Get Tools and Features** (Obtener herramientas y características). Se iniciará el Instalador de Visual Studio. Elija la carga de trabajo **Desarrollo de escritorio de .NET** y, luego, seleccione **Modificar**.

     ![Carga de trabajo de .NET Core en el instalador de Visual Studio](../ide/media/install-dot-net-desktop-env.png)

## <a name="create-the-application"></a>Crear la aplicación

Tras seleccionar la plantilla de proyecto de Visual Basic y asignar un nombre al archivo, Visual Studio abre un formulario automáticamente. Un formulario es una interfaz de usuario de Windows. Vamos a crear una aplicación "Hello World"; para ello, agregaremos controles al formulario y, después, ejecutaremos la aplicación.

### <a name="add-a-button-to-the-form"></a>Agregar un botón al formulario

1. Haga clic en **Cuadro de herramientas** para abrir la ventana flotante Cuadro de herramientas.

     ![Clic en Cuadro de herramientas para abrir la ventana Cuadro de herramientas](../ide/media/vb-toolbox-toolwindow.png)

     Si no ve la opción flotante **Cuadro de herramientas**, puede abrirla desde la barra de menús. Para ello, haga clic en **Ver** > **Cuadro de herramientas**. También puede presionar **CTRL**+**Alt**+**X**.

2. Haga clic en el icono de **anclaje** para acoplar la ventana **Cuadro de herramientas**.

     ![Clic en el icono de anclaje para anclar la ventana del cuadro de herramientas al IDE](../ide/media/vb-pin-the-toolbox-window.png)
3. Haga clic en el control **Botón** y arrástrelo al formulario.

     ![Agregar un botón al formulario](../ide/media/vb-add-a-button-to-form1.png)

4. En la sección **Apariencia** de la ventana **Propiedades**, escriba `Click this` y presione **ENTRAR**.

     ![Adición de texto al botón en el formulario](../ide/media/vb-button-control-text.png)

     Si no ve la ventana **Propiedades**, puede abrirla desde la barra de menús. Para ello, haga clic en **Ver** > **Ventana Propiedades**. También puede presionar **F4**.

5. En la sección **Diseño** de la ventana **Propiedades**, cambie el nombre de **Button1** a `btnClickThis` y, tras ello, presione **ENTRAR**.

     ![Adición de una función al botón en el formulario](../ide/media/vb-button-control-function.png)

### <a name="add-a-label-to-the-form"></a>Agregar una etiqueta al formulario

Ya hemos agregado un control de botón para crear una acción, así que ahora vamos a agregar un control de etiqueta al que enviar texto.

1. Seleccione el control **Etiqueta** desde la ventana **Cuadro de herramientas**, arrástrelo hasta el formulario y colóquelo debajo del botón **Click this**.

2. En la sección **Diseño** de la ventana **Propiedades**, cambie el nombre de **Label1** a `lblHelloWorld` y, tras ello, presione **ENTRAR**.

### <a name="add-code-to-the-form"></a>Agregar código al formulario

1. En la ventana **Form1.vb &#91;Diseño&#93;**, haga doble clic en el botón **Click this** para abrir la ventana **Form1.vb**.

      (También puede expandir **Form1.vb** en el **Explorador de soluciones** y luego hacer clic en **Form1**).

2. En la ventana **Form1.vb**, escriba o pegue `lblHelloWorld.Text = "Hello World!"` entre las líneas **Private Sub** y **End Sub**.

     ![Agregar código al formulario](../ide/media/vb-add-code-to-the-form.png)

## <a name="run-the-application"></a>Ejecutar la aplicación

1. Haga clic en el botón **Iniciar** para ejecutar la aplicación.

     ![Clic en Iniciar para depurar y ejecutar la aplicación](../ide/media/vb-click-start-hello-world.png)

   Ocurrirán varias cosas. En el IDE de Visual Studio, se abrirá la ventana **Herramientas de diagnóstico** y, también, una ventana **Salida**. Pero fuera del IDE se abre un cuadro de diálogo **Form1**. En él verá el botón **Click this** y el texto **Label1**.

2. Haga clic en el botón **Click this** en el cuadro de diálogo **Form1**. Observe cómo el texto **Label1** cambia a **Hello World!**.

    ![Cuadro de diálogo Form1 con el texto Label1 ](../ide/media/vb-form1-dialog-hello-world.png)

¡Enhorabuena por completar este tutorial de inicio rápido! Esperamos que haya aprendido un poco sobre Visual Basic y el IDE de Visual Studio. Si quiere profundizar más, continúe con el tutorial que encontrará en la sección **Tutoriales** de la tabla de contenido.

## <a name="see-also"></a>Vea también

* [Inicio rápido: Creación de una aplicación de consola en Visual Studio con Visual Basic](quickstart-visual-basic-console.md)
* [Más información sobre IntelliSense de Visual Basic](visual-basic-specific-intellisense.md)
