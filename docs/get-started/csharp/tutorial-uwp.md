---
title: Creación de una aplicación para UWP con Visual Studio y C#
description: Creación de una aplicación para UWP en Visual Studio con XAML y C#
titleSuffix: ''
ms.custom: seodec18, get-started, SEO-VS-2020
ms.date: 09/20/2019
ms.technology: vs-ide-general
ms.topic: tutorial
ms.devlang: CSharp
author: ornellaalt
ms.author: ornella
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- multiple
ms.openlocfilehash: 3c1f541c94804f8f5f454f6299a116a8bd1386e7
ms.sourcegitcommit: 4ae5e9817ad13edd05425febb322b5be6d3c3425
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/11/2020
ms.locfileid: "90037281"
---
# <a name="tutorial-create-your-first-universal-windows-platform-application-in-visual-studio-with-xaml-and-c35"></a>Tutorial: Creación de la primera aplicación para la Plataforma universal de Windows en Visual Studio con XAML y C&#35;

En esta introducción al Entorno de desarrollo integrado (IDE) de Visual Studio, creará una aplicación "Hola mundo" que se ejecuta en cualquier dispositivo Windows 10. Para ello, deberá utilizar una plantilla de proyecto de la Plataforma universal de Windows (UWP), el lenguaje XAML (Extensible Application Markup Language) y el lenguaje de programación C#.

::: moniker range="vs-2017"
Si todavía no ha instalado Visual Studio, vaya a la página de [descargas de Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) para instalarlo de forma gratuita.
::: moniker-end
::: moniker range="vs-2019"
Si todavía no ha instalado Visual Studio, vaya a la página de [descargas de Visual Studio](https://visualstudio.microsoft.com/downloads) para instalarlo de forma gratuita.
::: moniker-end

## <a name="create-a-project"></a>Crear un proyecto

En primer lugar, cree un proyecto de la Plataforma universal de Windows. En el tipo de proyecto se incluyen todos los archivos de plantilla que necesita, sin necesidad de agregar nada más.

::: moniker range="vs-2017"
1. Abra Visual Studio.

1. En la barra de menús superior, elija **Archivo** > **Nuevo** > **Proyecto**.

1. En el panel izquierdo del cuadro de diálogo **Nuevo proyecto**, expanda **Visual C#** y, a continuación, elija **Windows Universal**. En el panel central, elija **Aplicación vacía (Windows universal)** . Luego, asigne el nombre *HelloWorld* al proyecto y elija **Aceptar**.

   > [!NOTE]
   > Asegúrese de que la ubicación del proyecto de origen se encuentra en una unidad con el formato **New Technology File System (NTFS)** , como la del sistema operativo (SO). De lo contrario, es posible que tenga problemas para compilar y ejecutar el proyecto. 

   ![Plantilla de proyecto de Windows universal en el cuadro de diálogo Nuevo proyecto en el IDE de Visual Studio](media/new-project-csharp-uwp-helloworld.png)

   > [!NOTE]
   > Si no ve la plantilla de proyecto **Aplicación vacía (Windows universal)** , haga clic en el vínculo **Abrir el instalador de Visual Studio** en el panel izquierdo del cuadro de diálogo **Nuevo proyecto**.<br><br>![Haga clic en el vínculo Abrir el instalador de Visual Studio del cuadro de diálogo Nuevo proyecto](../../ide/media/vb-open-visual-studio-installer-hello-world.png)<br><br>Se iniciará el Instalador de Visual Studio. Elija la carga de trabajo **Desarrollo de la Plataforma universal de Windows** y, después, elija **Modificar**.<br><br>![Carga de trabajo de desarrollo de la Plataforma universal de Windows en el instalador de Visual Studio](media/uwp-dev-workload.png)

1. Acepte la **versión de destino** predeterminada y la configuración de la **versión mínima** en el cuadro de diálogo **Nuevo proyecto de la Plataforma universal de Windows**.

   ![Acepte la versión de destino predeterminada y la configuración de la versión mínima en el cuadro de diálogo Nuevo proyecto de la Plataforma universal de Windows](media/new-uwp-project-target-minver-dialog.png)
::: moniker-end

::: moniker range=">=vs-2019"
1. Abra Visual Studio y, en la ventana de inicio, elija **Crear un proyecto**.

1. En la pantalla **Crear un nuevo proyecto**, escriba *Windows universal* en el cuadro de búsqueda, elija la plantilla de C# para **Aplicación vacía (Windows universal)** y haga clic en **Siguiente**.

   ![Captura de pantalla de Crear un nuevo proyecto](media/vs-2019/uwp-create-new-project.png)

   > [!NOTE]
   > Si no ve la plantilla de proyecto **Aplicación vacía (Windows universal)** , haga clic en el vínculo **Instalar más herramientas y características**.<br><br>![Clic en el vínculo Instalar más herramientas y características](media/vs-2019/uwp-not-finding.png)<br><br>Se iniciará el Instalador de Visual Studio. Elija la carga de trabajo **Desarrollo de la Plataforma universal de Windows** y, después, elija **Modificar**.<br><br>![Carga de trabajo de desarrollo de la Plataforma universal de Windows en el instalador de Visual Studio](media/uwp-dev-workload.png)

1. Asigne un nombre al proyecto, _HelloWorld_, y seleccione **Crear**.

   ![Pantalla Configurar el proyecto](media/vs-2019/uwp-configure-your-project.png)

1. Acepte la **versión de destino** predeterminada y la configuración de la **versión mínima** en el cuadro de diálogo **Nuevo proyecto de la Plataforma universal de Windows**.

   ![Acepte la versión de destino predeterminada y la configuración de la versión mínima en el cuadro de diálogo Nuevo proyecto de la Plataforma universal de Windows](media/vs-2019/new-uwp-project-target-minver-dialog.png)
::: moniker-end

   > [!NOTE]
   > Si se trata de la primera vez que ha utilizado Visual Studio para crear una aplicación UWP, es posible que aparezca el cuadro de diálogo **Configuración**. Elija **Modo de programador** y, a continuación, elija **Sí**.<br><br>
   > ![Habilite el modo de desarrollador en el cuadro de diálogo Configuración de UWP](media/enable-developer-mode.png)<br><br>Visual Studio instala un paquete de modo de desarrollador adicional. Una vez completada la instalación del paquete, cierre el cuadro de diálogo **Configuración**.

## <a name="create-the-application"></a>Crear la aplicación

Es hora de empezar a desarrollar. Deberá agregar un control de botón y una acción al botón y, a continuación, iniciar la aplicación "Hello World" para ver su aspecto.

### <a name="add-a-button-to-the-design-canvas"></a>Agregar un botón al lienzo Diseño

1. En el **Explorador de soluciones**, haga doble clic en *MainPage.xaml* para abrir una vista en dos paneles.

   ::: moniker range="vs-2017"
   ![Abrir MainPage.xaml en el Explorador de soluciones ](media/uwp-solution-explorer-MainPage-xaml.png)
   ::: moniker-end
   ::: moniker range=">=vs-2019"
   ![Abrir MainPage.xaml en el Explorador de soluciones](media/vs-2019/uwp-solution-explorer-mainpage-xaml.png)
   ::: moniker-end

   Hay dos paneles: el **Diseñador XAML**, que incluye un lienzo de diseño, y el **Editor XAML**, donde se puede agregar o modificar el código.

   ![El panel Diseñador XAML en el Editor XAML](media/uwp-xaml-editor.png)

1. Elija **Cuadro de herramientas** para abrir la ventana flotante Cuadro de herramientas.

   ![Haga clic en Cuadro de herramientas para abrir la ventana flotante Cuadro de herramientas](media/uwp-toolbox.png)

   (Si no ve la opción **Cuadro de herramientas**, puede abrirla desde la barra de menús. Para ello, elija **Ver** > **barra de herramientas**. También puede presionar **CTRL**+**Alt**+**X**.

1. Haga clic en el icono de **anclaje** para acoplar la ventana del cuadro de herramientas.

   ![Haga clic en el icono Anclaje para acoplar la ventana Cuadro de herramientas](media/uwp-toolbox-autohide.png)

1. Haga clic en el control **Botón** y arrástrelo al lienzo de diseño.

   ![Haga clic en el control Botón y arrástrelo al lienzo Diseño](media/uwp-toolbox-add-button-control.png)

   Si observa el código en el **Editor XAML**, verá que el botón también se ha agregado ahí:

   ![Mostrar Botón en el Editor XAML](media/uwp-xaml-control-code-window.png)

### <a name="add-a-label-to-the-button"></a>Agregar una etiqueta al botón

1. En el **Editor XAML**, cambie el valor de Contenido del botón de "Button" a "Hello World!"

   ![Cambiar el valor del contenido del botón a Hello World](media/uwp-change-button-text-in-xaml-code-window.png)

1. Observe que el botón del **Diseñador XAML** también cambia.

   ![El botón cambia a Hello World en el lienzo de diseño](media/uwp-button-text-change-in-design-canvas.png)

### <a name="add-an-event-handler"></a>Agregar un controlador de eventos

Un "controlador de eventos" parece algo complicado, pero es simplemente otro nombre para el código que se llama cuando se produce un evento. En este caso, agrega una acción al botón "Hello World!" .

1. Haga doble clic en el control de botón del lienzo de diseño.

1. Modifique el código del controlador de eventos en *MainPage.xaml.cs*, la página de código subyacente.

   Aquí es donde las cosas se ponen interesantes. El controlador de eventos predeterminado tiene el aspecto siguiente:

   ![El controlador de eventos Button_Click predeterminado ](media/uwp-button-click-code.png)

   Vamos a cambiarlo para que tenga este aspecto:

   ![El nuevo controlador de eventos Button_Click asincrónico ](media/uwp-add-hello-world-async-code.png)

   Este es el código que se debe copiar y pegar:

   ```C#
   private async void Button_Click(object sender, RoutedEventArgs e)
         {
             MediaElement mediaElement = new MediaElement();
             var synth = new Windows.Media.SpeechSynthesis.SpeechSynthesizer();
             Windows.Media.SpeechSynthesis.SpeechSynthesisStream stream = await synth.SynthesizeTextToStreamAsync("Hello, World!");
             mediaElement.SetSource(stream, stream.ContentType);
             mediaElement.Play();
         }
   ```

#### <a name="what-did-we-just-do"></a>¿Qué acabamos de hacer?

El código usa algunas API de Windows para crear un objeto de síntesis de voz y, a continuación, le proporciona algún texto para que lo pronuncie. (Para obtener más información sobre el uso de `SpeechSynthesis`, vea <xref:System.Speech.Synthesis>).

## <a name="run-the-application"></a>Ejecutar la aplicación

::: moniker range="vs-2017"
Es el momento de compilar, implementar y ejecutar la aplicación UWP "Hello World" para ver qué aspecto tiene y cómo suena. Esta es la manera de hacerlo.

1. Use el botón de reproducción (es el que tiene escrito **Máquina local**) para iniciar la aplicación en la máquina local.

   ![Seleccionar Equipo local para iniciar y depurar la aplicación UWP](media/uwp-start-or-debug.png)

   (Como alternativa, puede seleccionar **Depurar** > **Iniciar depuración** en la barra de menús o presionar F5 para iniciar la aplicación).

1. Vea la aplicación, que se muestra poco después de que desaparezca una pantalla de presentación. La aplicación debe tener un aspecto similar al siguiente:

   ![Una aplicación "Hello World" UWP](media/uwp-hello-world-app.png)

1. Haga clic en el botón **Hello World**.

   El dispositivo Windows 10 dirá literalmente: "Hello, World!"

1. Para cerrar la aplicación, haga clic en el botón **Detener depuración** de la barra de herramientas. (O bien, elija **Depurar** > **Detener depuración** en la barra de menús o presione Mayús+F5).

::: moniker-end
::: moniker range=">=vs-2019"
Es el momento de compilar, implementar y ejecutar la aplicación UWP "Hello World" para ver qué aspecto tiene y cómo suena. Esta es la manera de hacerlo.

1. Use el botón de reproducción (es el que tiene escrito **Máquina local**) para iniciar la aplicación en la máquina local.

   ![Seleccionar Equipo local para iniciar y depurar la aplicación UWP](media/uwp-start-or-debug.png)

   (Como alternativa, puede seleccionar **Depurar** > **Iniciar depuración** en la barra de menús o presionar F5 para iniciar la aplicación).

1. Vea la aplicación, que se muestra poco después de que desaparezca una pantalla de presentación. La aplicación debe tener un aspecto similar al siguiente:

   ![Aplicación "Hola mundo" para UWP](media/vs-2019/uwp-hello-world-app.png)

1. Haga clic en el botón **Hello World**.

   El dispositivo Windows 10 dirá literalmente: "Hello, World!"

1. Para cerrar la aplicación, haga clic en el botón **Detener depuración** de la barra de herramientas. (O bien, elija **Depurar** > **Detener depuración** en la barra de menús o presione Mayús+F5).

::: moniker-end

## <a name="next-steps"></a>Pasos siguientes

Enhorabuena por completar este tutorial. Esperamos que haya aprendido algunos conceptos básicos sobre UWP y el IDE de Visual Studio. Para obtener más información, continúe con el tutorial siguiente:

> [!div class="nextstepaction"]
> [Crear una interfaz de usuario](/windows/uwp/design/basics/xaml-basics-ui)

## <a name="see-also"></a>Vea también

- [Información general sobre UWP](/windows/uwp/get-started/universal-application-platform-guide)
- [Obtener muestras de aplicaciones para UWP](/windows/uwp/get-started/get-uwp-app-samples)
