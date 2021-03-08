---
title: Creación de la primera aplicación de consola con Visual Basic
description: Aprenda a crear una aplicación de consola Hello World sencilla en Visual Studio con Visual Basic, paso a paso.
ms.custom: seodec18
ms.date: 03/23/2019
ms.technology: vs-ide-general
ms.prod: visual-studio-windows
ms.topic: quickstart
ms.devlang: vb
author: ornellaalt
ms.author: ornella
manager: jmartens
dev_langs:
- vb
ms.workload:
- multiple
ms.openlocfilehash: 34b412d254d0775b57f2c9befaae71ce25c6ae75
ms.sourcegitcommit: 5654b7a57a9af111a6f29239212d76086bc745c9
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/03/2021
ms.locfileid: "101683859"
---
# <a name="quickstart-create-your-first-console-app-in-visual-studio-with-visual-basic"></a>Inicio rápido: Crear la primera aplicación de consola en Visual Studio con Visual Basic

En esta introducción al entorno de desarrollo integrado (IDE) de Visual Studio, de entre 5 y 10 minutos, creará una sencilla aplicación de Visual Basic que se ejecuta en la consola.

::: moniker range="vs-2017"

Si todavía no ha instalado Visual Studio, vaya a la página de [descargas de Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) para instalarlo de forma gratuita.

::: moniker-end

::: moniker range="vs-2019"

Si todavía no ha instalado Visual Studio, vaya a la página de [descargas de Visual Studio](https://visualstudio.microsoft.com/downloads) para instalarlo de forma gratuita.

::: moniker-end

## <a name="create-a-project"></a>Crear un proyecto

En primer lugar, crearemos un proyecto de aplicación de Visual Basic. En el tipo de proyecto se incluyen todos los archivos de plantilla que vamos a necesitar, sin necesidad de agregar nada más.

::: moniker range="vs-2017"

1. Abra Visual Studio 2017.

2. En la barra de menús superior, elija **Archivo** > **Nuevo** > **Proyecto**.

3. En el panel de la izquierda del cuadro de diálogo **Nuevo proyecto**, expanda **Visual Basic** y seleccione **.NET Core**. En el panel central, elija **Aplicación de consola (.NET Core)** . Luego, asigne el nombre *HelloWorld* al proyecto.

   ![Plantilla de proyecto Aplicación de consola (.NET Core) en el cuadro de diálogo Nuevo proyecto en el IDE de Visual Studio](../ide/media/new-project-vb-dotnetcore-helloworld-console-app.png)

     Si no ve la plantilla de proyecto **Aplicación de consola (.NET Core)**, haga clic en el vínculo **Abrir el instalador de Visual Studio** en el panel izquierdo del cuadro de diálogo **Nuevo proyecto**.

   ![Clic en el vínculo Abrir el instalador de Visual Studio del cuadro de diálogo Nuevo proyecto](../ide/media/vb-open-visual-studio-installer-hello-world.png)

     Se iniciará el Instalador de Visual Studio. Elija la carga de trabajo **Desarrollo multiplataforma de .NET Core** y, después, elija **Modificar**.

     ![Carga de trabajo Desarrollo multiplataforma de .NET Core en el instalador de Visual Studio](../ide/media/dot-net-core-xplat-dev-workload.png)

::: moniker-end

::: moniker range="vs-2019"

> [!NOTE]
> Algunas de las capturas de pantalla de este artículo de inicio rápido usan el tema oscuro. Si no está usando el tema oscuro pero le gustaría hacerlo, vea la página [Guía de inicio rápido: personalizar el IDE y el editor de Visual Studio](quickstart-personalize-the-ide.md) para obtener información sobre cómo hacerlo.

1. Abra Visual Studio 2019.

1. En la ventana de inicio, elija **Crear un proyecto nuevo**.

   ![Visualización de la ventana "Crear un proyecto"](../get-started/media/vs-2019/create-new-project-dark-theme.png)

1. En la ventana **Crear un nuevo proyecto**, elija **Visual Basic** en la lista Idioma. A continuación, seleccione **Windows** en la lista Plataforma y **Consola** en la lista Tipos de proyecto.

   Después de aplicar los filtros de lenguaje, plataforma y tipo de proyecto, elija la plantilla **Aplicación de consola** y, luego, **Siguiente**.

   :::image type="content" source="../get-started/visual-basic/media/vs-2019/vb-create-new-project-console-net-core.png" alt-text="Elección de la plantilla Visual Basic para Aplicación de consola":::

   > [!NOTE]
   > Si no ve la plantilla **Aplicación de consola**, puede instalarla desde la ventana **Crear un nuevo proyecto**. En el mensaje **¿No encuentra lo que busca?** , elija el vínculo **Instalar más herramientas y características**.
   >
   > ![Vínculo "Instalar más herramientas y características" del mensaje "¿No encuentra lo que busca?" que aparece en la ventana "Crear proyecto"](../get-started/media/vs-2019/not-finding-what-looking-for.png) 
   > 
   > Luego, en el Instalador de Visual Studio, elija la carga de trabajo **Desarrollo multiplataforma de .NET Core**.
   >
   > ![Carga de trabajo Desarrollo multiplataforma de .NET Core en el instalador de Visual Studio](../get-started/media/dot-net-core-xplat-dev-workload.png)
   >
   > Después, elija el botón **Modificar** en el Instalador de Visual Studio. Es posible que se le pida que guarde su trabajo; si es así, hágalo. Seguidamente, elija **Continuar** para instalar la carga de trabajo. Luego, vuelva al paso 2 de este procedimiento "[Crear un proyecto](#create-a-project)".

1. En la ventana **Configurar el nuevo proyecto**, escriba *WhatIsYourName* en el cuadro **Nombre del proyecto**. Después, elija **Siguiente**.

   :::image type="content" source="../get-started/visual-basic/media/vs-2019/vb-name-your-project-whatname.png" alt-text="En la ventana &quot;Configurar el nuevo proyecto&quot;, asigne al proyecto el nombre &quot;WhatIsYourName&quot;.":::

1. En la ventana **Información adicional**, **.NET Core 3.1** ya debe estar seleccionado para la plataforma de destino. Si no es así, seleccione **.NET Core 3.1**. Luego, elija **Crear**.

   :::image type="content" source="../get-started/visual-basic/media/vs-2019/vb-target-framework.png" alt-text="En la ventana &quot;Información adicional&quot;, asegúrese de que está seleccionado .NET Core 3.1":::

   Visual Studio se abre en el nuevo proyecto.

::: moniker-end

## <a name="create-the-application"></a>Crear la aplicación

Tras seleccionar la plantilla de proyecto de Visual Basic y asignar un nombre al proyecto, Visual Studio crea automáticamente una sencilla aplicación llamada "Hello World". Llama al método <xref:System.Console.WriteLine%2A> para mostrar la cadena literal "Hola mundo" en la ventana de la consola.

![Visualización del código de Hello World predeterminado de la plantilla](../ide/media/vb-console-helloworld-template.png)

Si hace clic en el botón **HelloWorld** en el IDE, puede ejecutar el programa en modo de depuración.

  ![Clic en el botón Hello World para ejecutar el programa en modo de depuración](../ide/media/vb-console-hello-world-button.png)

Al hacerlo, la ventana de consola se mostrará un momento antes de cerrarse. Esto ocurre porque el método `Main` finaliza en cuanto se ejecuta su única instrucción, con lo cual la aplicación termina.

### <a name="add-some-code"></a>Agregar algo de código

Vamos a agregar código para pausar la aplicación y solicitar una entrada de usuario.

1. Agregue el código siguiente inmediatamente después de llamar al método <xref:System.Console.WriteLine%2A>:

   ```vb
   Console.Write("Press any key to continue...")
   Console.ReadKey(true)
   ```

    Esto hace que el programa se quede en pausa hasta que se presione una tecla.

2. En la barra de menús, seleccione **Compilar** > **Compilar solución**.

   De esta forma, el programa se compila en un lenguaje intermedio (IL) que se convierte en código binario mediante un compilador Just-In-Time (JIT).

## <a name="run-the-application"></a>Ejecutar la aplicación

1. Haga clic en el botón **HelloWorld** de la barra de herramientas.

   ![Clic en el botón Hello World para ejecutar el programa desde la barra de herramientas](../ide/media/vb-console-hello-world-button.png)

2. Presione cualquier tecla para cerrar la ventana de consola.

   ![Ventana de consola que muestra "Hello World" y "Press any key to continue"](../ide/media/vb-console-hello-world-press-any-key.png)

## <a name="next-steps"></a>Pasos siguientes

¡Enhorabuena por completar este tutorial de inicio rápido! Esperamos que haya aprendido un poco sobre Visual Basic y el IDE de Visual Studio. Para obtener más información, continúe con el tutorial siguiente.

> [!div class="nextstepaction"]
> [Introducción a Visual Basic en Visual Studio](../get-started/visual-basic/tutorial-console.md)
