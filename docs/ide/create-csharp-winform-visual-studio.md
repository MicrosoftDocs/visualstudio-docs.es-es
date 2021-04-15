---
title: Creación de una aplicación de Windows Forms con C#
description: Aprenda a crear una aplicación de Windows Forms en Visual Studio con C#, paso a paso.
ms.date: 09/26/2019
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
ms.devlang: CSharp
author: j-martens
ms.author: jmartens
manager: jmartens
dev_langs:
- CSharp
ms.workload:
- multiple
ms.openlocfilehash: 26f13d12324beb0e414761ce2d79297767c5d708
ms.sourcegitcommit: 6d88913a8b5a9e5eda01d3f95205b4d138f440f8
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/13/2021
ms.locfileid: "107297124"
---
# <a name="create-a-windows-forms-app-in-visual-studio-with-c"></a>Creación de una aplicación de Windows Forms en Visual Studio con C\#

En esta breve introducción al entorno de desarrollo integrado (IDE) de Visual Studio, creará una sencilla aplicación de C# que tiene una interfaz de usuario (IU) basada en Windows.

::: moniker range="vs-2017"

Si todavía no ha instalado Visual Studio, vaya a la página de [descargas de Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) para instalarlo de forma gratuita.

::: moniker-end

::: moniker range="vs-2019"

Si todavía no ha instalado Visual Studio, vaya a la página de [descargas de Visual Studio](https://visualstudio.microsoft.com/downloads) para instalarlo de forma gratuita.

> [!NOTE]
> Algunas de las capturas de pantalla de este tutorial usan el tema oscuro. Si no está usando el tema oscuro pero le gustaría hacerlo, vea la página [Guía de inicio rápido: personalizar el IDE y el editor de Visual Studio](../ide/quickstart-personalize-the-ide.md) para obtener información sobre cómo hacerlo.

::: moniker-end

## <a name="create-a-project"></a>Crear un proyecto

En primer lugar, se creará un proyecto de aplicación C#. En el tipo de proyecto se incluyen todos los archivos de plantilla que vamos a necesitar, sin necesidad de agregar nada más.

::: moniker range="vs-2017"

1. Abra Visual Studio 2017.

1. En la barra de menús superior, elija **Archivo** > **Nuevo** > **Proyecto**.

1. En el cuadro de diálogo **Nuevo proyecto** del panel izquierdo, expanda **Visual C#** y seleccione **Escritorio de Windows**. En el panel central, elija **Aplicación de Windows Forms (.NET Framework)** . Luego, asigne al archivo el nombre `HelloWorld`.

     Si no ve la plantilla de proyecto **Aplicación de Windows Forms (.NET Framework)** , cancele haciendo clic fuera del cuadro de diálogo **Nuevo proyecto** y, en la barra de menús superior, elija **Herramientas** > **Get Tools and Features** (Obtener herramientas y características). Se iniciará el Instalador de Visual Studio. Elija la carga de trabajo **Desarrollo de escritorio de .NET** y, luego, seleccione **Modificar**.

     ![Carga de trabajo de .NET Core en el instalador de Visual Studio](../ide/media/install-dot-net-desktop-env.png)

::: moniker-end

::: moniker range="vs-2019"

1. Abra Visual Studio 2019.

1. En la ventana de inicio, elija **Crear un proyecto nuevo**.

   ![Visualización de la ventana "Crear un proyecto"](../get-started/media/vs-2019/create-new-project-dark-theme.png)

1. En la ventana **Crear un nuevo proyecto**, elija la plantilla **Windows Forms App (.NET Framework)** para C#.

   (Si lo prefiere, puede refinar la búsqueda para acceder rápidamente a la plantilla que desee. Por ejemplo, escriba *Windows Forms App* en el cuadro de búsqueda. A continuación, elija **C#** en la lista de lenguajes y, luego, **Windows** en la lista de plataformas).  

   ![Selección de la plantilla C# para la Aplicación de Windows Forms (.NET Framework)](../get-started/csharp/media/vs-2019/csharp-create-new-winforms-project-nonfiltered.png)

   > [!NOTE]
   > Si no ve la plantilla **Aplicación de Windows Forms (.NET Framework)** , puede instalarla desde la ventana **Crear un proyecto**. En el mensaje **¿No encuentra lo que busca?** , elija el vínculo **Instalar más herramientas y características**.
   >
   > ![Vínculo "Instalar más herramientas y características" del mensaje "¿No encuentra lo que busca?" que aparece en la ventana "Crear proyecto"](../get-started/media/vs-2019/not-finding-what-looking-for.png)
   >
   > A continuación, en el Instalador de Visual Studio, elija la carga de trabajo **Desarrollo de escritorio de .NET**.
   >
   > ![Carga de trabajo de .NET Core en el instalador de Visual Studio](../ide/media/install-dot-net-desktop-env.png)
   >
   > Después, elija el botón **Modificar** en el Instalador de Visual Studio. Es posible que se le pida que guarde su trabajo; si es así, hágalo. Seguidamente, elija **Continuar** para instalar la carga de trabajo. Luego, vuelva al paso 2 de este procedimiento "[Crear un proyecto](#create-a-project)".

1. En la ventana **Configurar el nuevo proyecto**, escriba *HelloWorld* en el cuadro **Nombre del proyecto**. Luego, elija **Crear**.

   ![En la ventana "Configurar el nuevo proyecto", asigne al proyecto el nombre "HelloWorld".](../get-started/csharp/media/vs-2019/csharp-name-your-winform-project-helloworld.png)

   Visual Studio se abre en el nuevo proyecto.

::: moniker-end

## <a name="create-the-application"></a>Crear la aplicación

Tras seleccionar la plantilla de proyecto de C# y asignar un nombre al archivo, Visual Studio abre un formulario automáticamente. Un formulario es una interfaz de usuario de Windows. Se va a crear una aplicación "Hello World"; para ello, se agregarán controles al formulario y, después, se ejecutará la aplicación.

### <a name="add-a-button-to-the-form"></a>Agregar un botón al formulario

1. Elija **Cuadro de herramientas** para abrir la ventana flotante Cuadro de herramientas.

     ![Elegir el cuadro de herramientas para abrir la ventana Cuadro de herramientas](../ide/media/csharp-toolbox-toolwindow.png)

     Si no ve la opción flotante **Cuadro de herramientas**, puede abrirla desde la barra de menús. Para ello, seleccione **Ver** > **Cuadro de herramientas**. También puede presionar **CTRL**+**Alt**+**X**.

1. Elija el icono **Anclar** para acoplar la ventana **Cuadro de herramientas**.

     ![Elegir el icono de anclaje para anclar la ventana del cuadro de herramientas al IDE](../ide/media/vb-pin-the-toolbox-window.png)

1. Elija el control **Botón** y arrástrelo al formulario.

     ![Agregar un botón al formulario](../ide/media/csharp-add-button-form1.png)

1. En la ventana **Propiedades**, busque **Texto**, cambie el nombre de **Button1** a `Click this` y, luego, presione **Entrar**.

     ![Adición de texto al botón en el formulario](../ide/media/vb-button-control-text.png)

     Si no ve la ventana **Propiedades**, puede abrirla desde la barra de menús. Para ello, elija **Ver** > **Ventana Propiedades**. También puede presionar **F4**.

1. En la sección **Diseño** de la ventana **Propiedades**, cambie el nombre de **Button1** a `btnClickThis` y, tras ello, presione **ENTRAR**.

     ![Adición de una función al botón en el formulario](../ide/media/vb-button-control-function.png)

   > [!NOTE]
   > Si ha ordenado la lista alfabéticamente en la ventana **Propiedades**, **Button1** aparece en cambio en la sección **(DataBindings)** .

### <a name="add-a-label-to-the-form"></a>Agregar una etiqueta al formulario

Ya hemos agregado un control de botón para crear una acción, así que ahora vamos a agregar un control de etiqueta al que enviar texto.

1. Seleccione el control **Etiqueta** desde la ventana **Cuadro de herramientas**, arrástrelo hasta el formulario y colóquelo debajo del botón **Click this**.

1. En la sección **Diseño** o en la sección **(DataBindings)** de la ventana **Propiedades**, cambie el nombre de **Label1** por `lblHelloWorld` y presione **Entrar**.

### <a name="add-code-to-the-form"></a>Agregar código al formulario

1. En la ventana **Form1.cs &#91;Diseño&#93;** , haga doble clic en el botón **Click this** para abrir la ventana **Form1.cs**.

      (También puede expandir **Form1.vb** en el **Explorador de soluciones** y luego elegir **Form1**).

1. En la ventana **Form1.cs**, después de la línea **private void**, escriba `lblHelloWorld.Text = "Hello World!";` como se muestra en la captura de pantalla siguiente:

     ![Agregar código al formulario](../get-started/csharp/media/csharp-winforms-add-code.png)

## <a name="run-the-application"></a>Ejecutar la aplicación

1. Elija el botón **Iniciar** para ejecutar la aplicación.

     ![Elegir Iniciar para depurar y ejecutar la aplicación](../ide/media/vb-click-start-hello-world.png)

   Ocurrirán varias cosas. En el IDE de Visual Studio, se abrirá la ventana **Herramientas de diagnóstico** y, también, una ventana **Salida**. Pero fuera del IDE se abre un cuadro de diálogo **Form1**. En él verá el botón **Click this** y el texto **Label1**.

1. Elija el botón **Click this** en el cuadro de diálogo **Form1**. Observe cómo el texto **Label1** cambia a **Hello World!** .

    ![Cuadro de diálogo Form1 con el texto Label1 ](../ide/media/vb-form1-dialog-hello-world.png)

1. Cierre el cuadro de diálogo **Form1** para dejar de ejecutar la aplicación.

## <a name="next-steps"></a>Pasos siguientes

Para obtener más información, continúe con el tutorial siguiente:

> [!div class="nextstepaction"]
> [Tutorial: Crear un visor de imágenes](tutorial-1-create-a-picture-viewer.md)

## <a name="see-also"></a>Vea también

* [Más tutoriales de C#](../get-started/csharp/index.yml)
* [Tutoriales de Visual Basic](../get-started/visual-basic/index.yml)
* [Tutoriales de C++](/cpp/get-started/tutorial-console-cpp)