---
title: 'Paso 1: Creación de un proyecto de aplicación de Windows Forms'
ms.date: 08/30/2019
ms.assetid: 16ac2422-e720-4e3a-b511-bc2a54201a86
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: be7b9bd67ed88b9f59ed279211bf15c96ae59569
ms.sourcegitcommit: 6eed0372976c0167b9a6d42ba443f9a474b8bb91
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2019
ms.locfileid: "71119016"
---
# <a name="step-1-create-a-windows-forms-app-project"></a>Paso 1: Creación de un proyecto de aplicación de Windows Forms

Al crear un visor de imagen, el primer paso consiste en crear un proyecto de aplicación de Windows Forms.

::: moniker range="vs-2017"

## <a name="open-visual-studio-2017"></a>Abra Visual Studio 2017

1. En la barra de menús, elija **Archivo** > **Nuevo** > **Proyecto**. El cuadro de diálogo debe ser similar a la de la siguiente captura de pantalla:

     ![Cuadro de diálogo Nuevo proyecto](../ide/media/newprojectdialogcallouts.png)<br/>*Cuadro de diálogo* ***Nuevo proyecto***

2. En la parte izquierda del cuadro de diálogo **Nuevo proyecto** elija **Visual C#** o **Visual Basic**, y después **Escritorio de Windows**.

3. En la lista de plantillas de proyecto, elija **Aplicación de Windows Forms (.NET Framework)** . Asigne un nombre al nuevo formulario *PictureViewer* y, después, pulse el botón **Aceptar**.

    >[!NOTE]
    >Si no ve la plantilla **Aplicación de Windows Forms (.NET Framework)** , use el instalador de Visual Studio para instalar la carga de trabajo **Desarrollo de escritorio de .NET**.<br/><br/>![Carga de trabajo de desarrollo de escritorio de .NET en el instalador de Visual Studio](../ide/media/dot-net-desktop-dev-workload.png)<br/><br/> Para obtener más información, vea la página [Instalación de Visual Studio](../install/install-visual-studio.md).

::: moniker-end

::: moniker range="vs-2019"

## <a name="open-visual-studio-2019"></a>Apertura de Visual Studio 2019

1. En la ventana de inicio, elija **Crear un proyecto nuevo**.

   ![Visualización de la ventana "Crear un proyecto"](../get-started/media/vs-2019/create-new-project-dark-theme.png)

1. En el cuadro de búsqueda de la ventana **Crear un proyecto**, escriba *Windows Forms*. A continuación, elija **Escritorio** en la lista **Tipo de proyecto**.

   Después de aplicar el filtro **Tipo de proyecto**, elija la plantilla **Aplicación de Windows Forms (.NET Framework)** para C# o Visual Basic, y después seleccione **Siguiente**.

   ![Selección de la plantilla C# para la Aplicación de Windows Forms (.NET Framework)](./media/create-new-project-search-winforms-filtered.png)

   > [!NOTE]
   > Si no ve la plantilla **Aplicación de Windows Forms (.NET Framework)** , puede instalarla desde la ventana **Crear un proyecto nuevo**. En el mensaje **¿No encuentra lo que busca?** , elija el vínculo **Instalar más herramientas y características**.
   >
   > ![Vínculo "Instalar más herramientas y características" del mensaje "¿No encuentra lo que busca?" que aparece en la ventana "Crear proyecto"](../get-started/media/vs-2019/not-finding-what-looking-for.png)
   >
   > A continuación, en el Instalador de Visual Studio, elija la carga de trabajo **Desarrollo de escritorio de .NET**.
   >
   > ![Carga de trabajo de .NET Core en el instalador de Visual Studio](../ide/media/install-dot-net-desktop-env.png)
   >
   > Después, elija el botón **Modificar** en el Instalador de Visual Studio. Es posible que se le pida que guarde su trabajo; si es así, hágalo. Seguidamente, elija **Continuar** para instalar la carga de trabajo.

1. En la ventana **Configurar el nuevo proyecto**, escriba *PictureViewer* en el cuadro **Nombre del proyecto**. Luego, elija **Crear**.

::: moniker-end

Visual Studio crea una solución para la aplicación. Una solución actúa como un contenedor de todos los proyectos y archivos necesarios para la aplicación. Estos términos se explicarán con más detalle en secciones posteriores de este tutorial.

## <a name="about-the-windows-forms-app-project"></a>Acerca del proyecto de aplicación de Windows Forms

1. El entorno de desarrollo contiene tres ventanas: una ventana principal, el **Explorador de soluciones** y la ventana **Propiedades**.

     Si falta alguna de estas ventanas, puede restaurar el diseño de ventanas predeterminado. En la barra de menús, seleccione **Ventana** > **Restablecer diseños de ventana**.

     También puede mostrar ventanas mediante comandos de menú. En la barra de menús, pulse **Ver** > **Ventana Propiedades** o **Explorador de soluciones**.

     Si hay otras ventanas abiertas, ciérrelas con el botón **Cerrar** (x) de la esquina superior derecha.

    ::: moniker range="vs-2017"

    * **Ventana principal** En esta ventana, realizará la mayor parte del trabajo, como ejecutar formularios y editar código. La ventana muestra un formulario en el **Editor de formularios**. En la parte superior de la ventana, aparecerán las pestañas **Página principal** y **Form1.cs [Diseño]** . (En Visual Basic, el nombre de la pestaña termina con *.vb* en lugar de *.cs*).

    ::: moniker-end

    ::: moniker range=">=vs-2019"

    * **Ventana principal** En esta ventana, realizará la mayor parte del trabajo, como ejecutar formularios y editar código. La ventana muestra un formulario en el **Editor de formularios**.

    ::: moniker-end

    * **Ventana Explorador de soluciones** En esta ventana, puede ver todos los elementos de la solución y navegar por ellos.

    Al seleccionar un archivo, cambia el contenido de la ventana **Propiedades**. Si abre un archivo de código (que finaliza en *.cs* para C# y en *.vb* para Visual Basic), aparece el archivo de código o un diseñador para él. Un diseñador es una superficie visual en la que se pueden agregar controles, como botones y listas. En los formularios de Visual Studio, el diseñador se llama **Diseñador de Windows Forms**.

    * **Ventana Propiedades** En esta ventana, puede cambiar las propiedades de los elementos elegidos en las otras ventanas. Por ejemplo, si elige Form1, puede cambiar el título mediante la propiedad **Text** y el color de fondo mediante la propiedad **Backcolor**.

      > [!NOTE]
      > En la línea superior del **Explorador de soluciones** se muestra **Solución "PictureViewer" (1 proyecto)** , lo que significa que Visual Studio ha creado una solución. Una solución puede contener varios proyectos, pero, por ahora, trabajará con soluciones que contengan un solo proyecto.

1. En la barra de menús, pulse **Archivo** > **Guardar todo**.

     Como alternativa, seleccione el botón **Guardar todo** de la barra de herramientas que se muestra en la imagen siguiente.

     ![Botón de la barra de herramientas Guardar todo](../ide/media/express_iconsaveall.png)<br/>
     *Botón de la barra de herramientas* ***Guardar todo***

     Visual Studio rellena automáticamente el nombre de la carpeta y el nombre del proyecto, y después guarda el proyecto en la carpeta de proyectos.

## <a name="next-steps"></a>Pasos siguientes

* Para ir al siguiente paso del tutorial, vea **[Paso 2: Ejecución de la aplicación](../ide/step-2-run-your-program.md)** .

* Para volver al tema de información general, vea [Tutorial 1: Crear un visor de imágenes](../ide/tutorial-1-create-a-picture-viewer.md).

## <a name="see-also"></a>Vea también

* [Tutorial 2: Creación de una prueba matemática cronometrada](tutorial-2-create-a-timed-math-quiz.md)
* [Tutorial 3: Creación de un juego de formar parejas](tutorial-3-create-a-matching-game.md)
