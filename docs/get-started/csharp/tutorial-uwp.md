---
description: Creación de una aplicación para UWP en Visual Studio con XAML y C#
titleSuffix: ''
ms.custom: seodec18, get-started
ms.date: 04/04/2018
ms.prod: visual-studio-dev15
ms.technology:
- vs-ide-general
ms.topic: tutorial
ms.devlang: CSharp
author: TerryGLee
ms.author: tglee
manager: douge
dev_langs:
- CSharp
ms.workload:
- multiple
ms.openlocfilehash: 7e18e1e65d0fa21431814bf0e6abede0aa255768
ms.sourcegitcommit: 35bebf794f528d73d82602e096fd97d7b8f82c25
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/18/2018
ms.locfileid: "53562634"
---
# <a name="tutorial-create-your-first-universal-windows-platform-application-in-visual-studio-with-xaml-and-c35"></a>Tutorial: Creación de la primera aplicación para la Plataforma universal de Windows en Visual Studio con XAML y C&#35;

En esta introducción al Entorno de desarrollo integrado (IDE) de Visual Studio, de entre 5 y 10 minutos, creará una aplicación "Hello World" que se ejecuta en cualquier dispositivo Windows 10. Para ello, deberá utilizar una plantilla de proyecto de la Plataforma universal de Windows (UWP), el lenguaje XAML (Extensible Application Markup Language) y el lenguaje de programación C#.

Si todavía no ha instalado Visual Studio, vaya a la página de [descargas de Visual Studio](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) para instalarlo de forma gratuita.

## <a name="create-a-project"></a>Crear un proyecto

En primer lugar, cree un proyecto de la Plataforma universal de Windows. En el tipo de proyecto se incluyen todos los archivos de plantilla que necesita, sin necesidad de agregar nada más.

1. Abra Visual Studio 2017.

2. En la barra de menús superior, seleccione **Archivo** > **Nuevo** > **Proyecto**.

3. En el panel izquierdo del cuadro de diálogo **Nuevo proyecto**, expanda **Visual C#** y, a continuación, elija **Windows Universal**. En el panel central, elija **Aplicación vacía (Windows universal)**. Luego, asigne el nombre *HelloWorld* al proyecto y elija **Aceptar**.

   ![Plantilla de proyecto de Windows universal en el cuadro de diálogo Nuevo proyecto en el IDE de Visual Studio](media/new-project-csharp-uwp-helloworld.png)

   > [!NOTE]
   > Si no ve la plantilla de proyecto **Aplicación vacía (Windows universal)**, haga clic en el vínculo **Abrir el instalador de Visual Studio** en el panel izquierdo del cuadro de diálogo **Nuevo proyecto**.<br><br>![Haga clic en el vínculo Abrir el instalador de Visual Studio del cuadro de diálogo Nuevo proyecto](../../ide/media/vb-open-visual-studio-installer-hello-world.png)<br><br>Se iniciará el Instalador de Visual Studio. Elija la carga de trabajo **Desarrollo de la Plataforma universal de Windows** y, después, elija **Modificar**.<br><br>![Carga de trabajo de desarrollo de la Plataforma universal de Windows en el instalador de Visual Studio](media/uwp-dev-workload.png)

4. Cuando aparezca el cuadro de diálogo **Nuevo proyecto de la Plataforma universal de Windows**, elija **Aceptar**.

   ![Acepte la versión de destino predeterminada y la configuración de la versión mínima en el cuadro de diálogo Nuevo proyecto de la Plataforma universal de Windows](media/new-uwp-project-target-minver-dialog.png)

   > [!NOTE]
   > Si se trata de la primera vez que ha utilizado Visual Studio para crear una aplicación UWP, es posible que aparezca el cuadro de diálogo **Configuración**. Elija **Modo de programador** y, a continuación, elija **Sí**.<br><br>
   ![Habilite el modo de desarrollador en el cuadro de diálogo Configuración de UWP](media/enable-developer-mode.png)<br><br>Visual Studio instala un paquete de modo de desarrollador adicional. Una vez completada la instalación del paquete, cierre el cuadro de diálogo **Configuración**.

## <a name="create-the-application"></a>Crear la aplicación

Es hora de empezar a desarrollar. Deberá agregar un control de botón y una acción al botón y, a continuación, iniciar la aplicación "Hello World" para ver su aspecto.

### <a name="add-a-button-to-the-design-canvas"></a>Agregar un botón al lienzo Diseño

1. En el **Explorador de soluciones**, haga doble clic en *MainPage.xaml* para abrir una vista en dos paneles.

   ![Abrir MainPage.xaml en el Explorador de soluciones ](media/uwp-solution-explorer-MainPage-xaml.png)

   Hay dos paneles: el **Diseñador XAML**, que incluye un lienzo de diseño, y el **Editor XAML**, donde se puede agregar o modificar el código.

   ![El panel Diseñador XAML en el Editor XAML](media/uwp-xaml-editor.png)

2. Elija **Cuadro de herramientas** para abrir la ventana flotante Cuadro de herramientas.

   ![Haga clic en Cuadro de herramientas para abrir la ventana flotante Cuadro de herramientas](media/uwp-toolbox.png)

   (Si no ve la opción **Cuadro de herramientas**, puede abrirla desde la barra de menús. Para ello, elija **Ver** > **barra de herramientas**. También puede presionar **CTRL**+**Alt**+**X**.

3. Haga clic en el icono de **anclaje** para acoplar la ventana del cuadro de herramientas.

   ![Haga clic en el icono Anclaje para acoplar la ventana Cuadro de herramientas](media/uwp-toolbox-autohide.png)

4. Haga clic en el control **Botón** y arrástrelo al lienzo de diseño.

   ![Haga clic en el control Botón y arrástrelo al lienzo Diseño](media/uwp-toolbox-add-button-control.png)

   Si observa el código en el **Editor XAML**, verá que el botón también se ha agregado ahí:

   ![Haga clic en el control Botón y arrástrelo al lienzo Diseño](media/uwp-xaml-control-code-window.png)

### <a name="add-a-label-to-the-button"></a>Agregar una etiqueta al botón

1. En el **Editor XAML**, cambie el valor de Contenido del botón de "Button" a "Hello World!"

   ![Cambiar el valor del contenido del botón a Hello World](media/uwp-change-button-text-in-xaml-code-window.png)

2. Observe que el botón del **Diseñador XAML** también cambia.

   ![El botón cambia a Hello World en el lienzo de diseño](media/uwp-button-text-change-in-design-canvas.png)

### <a name="add-an-event-handler"></a>Agregar un controlador de eventos

Un "controlador de eventos" parece algo complicado, pero es simplemente otro nombre para el código que se llama cuando se produce un evento. En este caso, agrega una acción al botón "Hello World!" .

1. Haga doble clic en el control de botón del lienzo de diseño.

2. Modifique el código del controlador de eventos en *MainPage.xaml.cs*, la página de código subyacente.

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

Es el momento de compilar, implementar y ejecutar la aplicación UWP "Hello World" para ver qué aspecto tiene y cómo suena. Esta es la manera de hacerlo.

1. Elija **Equipo local** para iniciar la aplicación.

   ![Seleccionar Equipo local para iniciar y depurar la aplicación UWP](media/uwp-start-or-debug.png)

   (Como alternativa, puede elegir **Depurar** > **Iniciar depuración** en la barra de menús o presionar **F5** para iniciar la aplicación).

2. Vea la aplicación, que se muestra poco después de que desaparezca una pantalla de presentación. La aplicación debe tener un aspecto similar al siguiente:

   ![Una aplicación "Hello World" UWP](media/uwp-hello-world-app.png)

3. Haga clic en el botón **Hello World**.

   El dispositivo Windows 10 dirá literalmente: "Hello, World!"

4. Para cerrar la aplicación, haga clic en el botón **Detener depuración** de la barra de herramientas. (O bien, elija **Depurar** > **Detener depuración** en la barra de menús o presione **Mayús**+**F5**).

## <a name="next-steps"></a>Pasos siguientes

¡Enhorabuena por completar este tutorial de inicio rápido! Esperamos que haya aprendido algunos conceptos básicos sobre UWP y el IDE de Visual Studio. Para obtener más información, continúe con el tutorial siguiente:

> [!div class="nextstepaction"]
> [Crear una interfaz de usuario](/windows/uwp/design/basics/xaml-basics-ui)
