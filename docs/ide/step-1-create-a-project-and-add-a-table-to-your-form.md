---
title: 'Paso 1: Crear un proyecto y agregar una tabla a un formulario'
description: Aprenda a crear el proyecto del juego de formar parejas y a agregar una tabla al formulario.
ms.custom: SEO-VS-2020
ms.date: 10/15/2019
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
ms.assetid: 1cac4ba4-f3cd-43bd-ad5d-50fc599234e8
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1a8ae9b17df85431945b19d65f5435ac081b4a1c
ms.sourcegitcommit: df6ba39a62eae387e29f89388be9e3ee5ceff69c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/02/2020
ms.locfileid: "96480725"
---
# <a name="step-1-create-a-project-and-add-a-table-to-your-form"></a>Paso 1: Crear un proyecto y agregar una tabla a un formulario

El primer paso para crear un juego de formar parejas es crear el proyecto y agregar una tabla al formulario. Esta tabla ayuda a alinear los iconos en una cuadrícula de 4x4 ordenada. También establecerá varias propiedades para mejorar el aspecto del tablero de juego.

## <a name="to-create-a-project-and-add-a-table-to-your-form"></a>Para crear un proyecto y agregar una tabla al formulario

::: moniker range="vs-2017"

1. En la barra de menús, elija **Archivo** > **Nuevo** > **Proyecto**.

1. Elija **Visual C#** o **Visual Basic** en la parte izquierda del cuadro de diálogo **Nuevo proyecto** y, a continuación, elija **Escritorio de Windows**.

1. En la lista de plantillas, elija la plantilla **Aplicación de Windows Forms (.NET Framework)**, denomínela *MatchingGame* y, después, haga clic en el botón **Aceptar**.

    Aparecerá un formulario denominado *Form1.cs* o *Form1.vb*, según el lenguaje de programación elegido.

   > [!NOTE]
   > Si no ve la plantilla **Aplicación de Windows Forms (.NET Framework)**, use el instalador de Visual Studio para instalar la carga de trabajo **Desarrollo de escritorio de .NET**.<br/><br/>![Carga de trabajo de desarrollo de escritorio de .NET en el instalador de Visual Studio](../ide/media/dot-net-desktop-dev-workload.png)<br/><br/> Para obtener más información, vea la página [Instalación de Visual Studio](../install/install-visual-studio.md).

::: moniker-end

::: moniker range="vs-2019"

1. En la ventana de inicio, elija **Crear un proyecto nuevo**.

   ![Visualización de la ventana "Crear un proyecto"](../get-started/media/vs-2019/create-new-project-dark-theme.png)

1. En el cuadro de búsqueda de la ventana **Crear un proyecto**, escriba *Windows Forms*. A continuación, elija **Escritorio** en la lista **Tipo de proyecto**.

   Después de aplicar el filtro **Tipo de proyecto**, elija la plantilla **Aplicación de Windows Forms (.NET Framework)** para C# o Visual Basic, y después seleccione **Siguiente**.

   ![Elección de la plantilla de C# o Visual Basic para la Aplicación de Windows Forms (.NET Framework)](./media/create-new-project-search-winforms-filtered.png)

   > [!NOTE]
   > Si no ve la plantilla **Aplicación de Windows Forms (.NET Framework)** , puede instalarla desde la ventana **Crear un proyecto**. En el mensaje **¿No encuentra lo que busca?** , elija el vínculo **Instalar más herramientas y características**.
   >
   > ![Vínculo "Instalar más herramientas y características" del mensaje "¿No encuentra lo que busca?" que aparece en la ventana "Crear proyecto"](../get-started/media/vs-2019/not-finding-what-looking-for.png)
   >
   > A continuación, en el Instalador de Visual Studio, elija la carga de trabajo **Desarrollo de escritorio de .NET**.
   >
   > ![Carga de trabajo de .NET Core en el instalador de Visual Studio](../ide/media/install-dot-net-desktop-env.png)
   >
   > Después, elija el botón **Modificar** en el Instalador de Visual Studio. Es posible que se le pida que guarde su trabajo; si es así, hágalo. Seguidamente, elija **Continuar** para instalar la carga de trabajo.

1. En la ventana **Configurar el nuevo proyecto**, escriba *MatchingGame* en el cuadro **Nombre del proyecto**. Luego, elija **Crear**.

::: moniker-end

## <a name="to-set-properties-for-a-form"></a>Para establecer las propiedades de un formulario

1. En la ventana **Propiedades**, defina las propiedades del formulario siguientes.

   1. Cambie la propiedad **Text** del formulario de **Form1** a **Matching Game**. Este texto aparece en la parte superior de la ventana de juego.

   2. Establezca el tamaño del formulario en 550 píxeles de ancho por 550 píxeles de alto. Puede realizar esta operación estableciendo la propiedad **Tamaño** en **550, 550** o arrastrando la esquina del formulario hasta que vea el tamaño correcto en la esquina inferior derecha del entorno de desarrollo integrado (IDE).

2. Muestre el cuadro de herramientas pulsando la pestaña **Cuadro de herramientas** en el lado izquierdo del IDE.

3. Arrastre un control <xref:System.Windows.Forms.TableLayoutPanel> desde la categoría **Contenedores** del cuadro de herramientas y establezca las propiedades siguientes.

   1. Establezca la propiedad **BackColor** en **CornflowerBlue**. Para ello, abra el cuadro de diálogo **BackColor** pulsando la flecha de lista desplegable situada junto a la propiedad **BackColor** en la ventana **Propiedades**.  A continuación, pulse la pestaña **Web** en el cuadro de diálogo **BackColor** para ver una lista de nombres de colores disponibles.

      > [!NOTE]
      > Los colores no están en orden alfabético, y **CornflowerBlue** está casi al final de la lista.

   2. Establezca la propiedad **Dock** en **Fill**; para ello, haga clic en el botón de lista desplegable situado al lado de la propiedad y pulse el botón grande del medio. Esto expande el tamaño de la tabla de modo que cubra todo el formulario.

   3. Establezca la propiedad **CellBorderStyle** en **Inserción**. Esta propiedad proporciona los bordes visuales entre cada celda del tablero.

   4. Elija el botón del triángulo situado en la esquina superior derecha de TableLayoutPanel para mostrar su menú de tareas.

   5. En el menú de tareas, pulse **Agregar fila** para agregar dos filas más y, después, pulse dos veces **Agregar columna** para agregar dos columnas más.

   6. En el menú de tareas, pulse **Editar filas y columnas** para abrir la ventana **Estilos de columna y fila**. Pulse cada una de las columnas, pulse el botón de opción **Porcentaje** y establezca el ancho de cada columna en el 25 por ciento del ancho total. Después, seleccione **Filas** en la lista desplegable de la parte superior de la ventana y establezca el alto de cada fila en el 25 por ciento. Cuando termine, elija el botón **Aceptar**.

      Su TableLayoutPanel debería ser ahora una cuadrícula de 4x4, con dieciséis celdas cuadradas del mismo tamaño. Estas filas y columnas son donde más adelante aparecerán las imágenes de icono.

4. Asegúrese de que el control TableLayoutPanel esté seleccionado en el editor de formularios. Para comprobarlo, debe ver **tableLayoutPanel1** en la parte superior de la ventana **Propiedades**. Si no está seleccionado, pulse TableLayoutPanel en el formulario o elíjalo en el control desplegable de la parte superior de la ventana **Propiedades**.

    Con el control TableLayoutPanel seleccionado, abra el cuadro de herramientas y agregue un control <xref:System.Windows.Forms.Label> (situado en la categoría **Controles comunes**) a la celda superior izquierda de TableLayoutPanel. Ahora, el control Label debería estar seleccionado en el IDE. Establezca las siguientes propiedades para el control.

   1. Asegúrese de que la propiedad **BackColor** de la etiqueta esté establecida en **CornflowerBlue**.

   2. Establezca la propiedad **AutoSize** en **False**.

   3. Establezca la propiedad **Dock** en **Fill**.

   4. Establezca la propiedad **TextAlign** en **MiddleCenter** pulsando el botón de lista desplegable que se encuentra al lado de la propiedad y pulsando el botón central. De esta forma, se asegurará de que el icono aparezca en el centro de la celda.

   5. Pulse la propiedad **Font**. Debe aparecer un botón de puntos suspensivos (**…**).

   6. Pulse el botón de puntos suspensivos y establezca el valor de **Fuente** en **Webdings**, **Estilo de fuente** en **Negrita** y **Tamaño** en **48**.

   7. Establezca la propiedad **Text** de la etiqueta en la letra **c**.

        La celda superior izquierda de TableLayoutPanel debería contener ahora un cuadro negro centrado sobre un fondo azul.

       > [!NOTE]
       > La fuente Webdings es una fuente de iconos que se distribuye con el sistema operativo Windows. En el juego de formar parejas, el jugador necesita encontrar la correspondencia entre pares de iconos, de modo que se usa esta fuente para mostrar los iconos que deben coincidir. En lugar de colocar **c** en la propiedad **Text**, pruebe a escribir letras diferentes para ver qué iconos se muestran. Un signo de exclamación es una araña, una N mayúscula es un ojo y una coma es una guindilla.

5. Elija el control Label y cópielo en la celda siguiente en TableLayoutPanel. (Pulse las teclas **Ctrl**+**C** o, en la barra de menús, pulse **Editar** > **Copiar**). A continuación, péguelo. (Pulse las teclas **Ctrl**+**V** o, en la barra de menús, pulse **Editar** > **Pegar**). Una copia de la primera etiqueta aparece en la segunda celda de TableLayoutPanel. Vuelva a pegar el control; aparecerá otra etiqueta en la tercera celda. Siga pegando los controles Label hasta que se llenen todas las celdas.

   > [!NOTE]
   > Si pega demasiadas veces, el IDE agrega una nueva fila a TableLayoutPanel para que haya espacio para agregar el nuevo control Label. La acción se puede deshacer. Para quitar la nueva celda, pulse las teclas **Ctrl**+**Z** o, en la barra de menús, pulse **Editar** > **Deshacer**.

    Ya tiene diseñado el formulario. Debería tener un aspecto similar a la imagen siguiente.

    ![Formulario inicial del juego de formar parejas](../ide/media/express_tut4step1.png)<br/>*Formulario inicial del juego de formar parejas*

## <a name="to-continue-or-review"></a>Para continuar o revisar

- Para ir al paso siguiente del tutorial, vea [Paso 2: Agregar un objeto aleatorio y una lista de iconos](../ide/step-2-add-a-random-object-and-a-list-of-icons.md).

- Para volver al tema de información general, vea [Tutorial 3: Crear un juego de formar parejas](../ide/tutorial-3-create-a-matching-game.md).
