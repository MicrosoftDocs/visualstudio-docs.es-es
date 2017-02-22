---
title: "Paso 1: Crear un proyecto y agregar una tabla a un formulario | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 1cac4ba4-f3cd-43bd-ad5d-50fc599234e8
caps.latest.revision: 19
caps.handback.revision: 19
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Paso 1: Crear un proyecto y agregar una tabla a un formulario
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

El primer paso para crear un juego de formar parejas es crear el proyecto y agregar una tabla al formulario.  Esta tabla ayuda a alinear los iconos en una cuadrícula de 4x4 ordenada.  También establecerá varias propiedades para mejorar el aspecto del tablero de juego.  
  
### Para crear un proyecto y agregar una tabla al formulario  
  
1.  En la barra de menús, elija **Archivo**, **Nuevo**, **Proyecto**.  
  
2.  Si no usa Visual Studio Express, primero debe seleccionar un lenguaje de programación.  En la lista **Plantillas instaladas**, elija **Visual C\#** o **Visual Basic**.  
  
3.  En la lista de plantillas de proyecto, elija **Aplicación de Windows Forms**, asígnele el nombre MatchingGame y elija el botón **Aceptar**.  
  
4.  En la ventana **Propiedades**, defina las propiedades del formulario siguientes.  
  
    1.  Cambie la propiedad **Text** del formulario de **Form1** a **Matching Game**.  Este texto aparece en la parte superior de la ventana de juego.  
  
    2.  Establezca el tamaño del formulario en 550 píxeles de ancho por 550 píxeles de alto.  Puede realizar esta operación estableciendo la propiedad **Tamaño** en **550, 550** o arrastrando la esquina del formulario hasta que vea el tamaño correcto en la esquina inferior derecha del entorno de desarrollo integrado \(IDE\).  
  
5.  Muestre el cuadro de herramientas eligiendo la pestaña **Cuadro de herramientas** en el lado izquierdo del IDE.  
  
6.  Arrastre un control `TableLayoutPanel` desde la categoría **Contenedores** del cuadro de herramientas y establezca las propiedades siguientes.  
  
    1.  Establezca la propiedad **BackColor** en **CornflowerBlue**.  Para ello, abra el cuadro de diálogo **BackColor** eligiendo la flecha de lista desplegable situada junto a la propiedad **BackColor** en la ventana **Propiedades**.  A continuación, elija la pestaña **Web** en el cuadro de diálogo **BackColor** para ver una lista de nombres de colores disponibles.  
  
        > [!NOTE]
        >  Los colores no están en orden alfabético, y CornflowerBlue está casi al final de la lista.  
  
    2.  Establezca la propiedad **Dock** en **Fill**; para ello, haga clic en el botón de lista desplegable situado al lado de la propiedad y elija el botón grande del medio.  Esto expande el tamaño de la tabla de modo que cubra todo el formulario.  
  
    3.  Establezca la propiedad **CellBorderStyle** en **Inserción**.  Esta propiedad proporciona los bordes visuales entre cada celda del tablero.  
  
    4.  Elija el botón del triángulo situado en la esquina superior derecha de TableLayoutPanel para mostrar su menú de tareas.  
  
    5.  En el menú de tareas, elija **Agregar fila** para agregar dos filas más y, a continuación, elija dos veces **Agregar columna** para agregar dos columnas más.  
  
    6.  En el menú de tareas, elija **Editar filas y columnas** para abrir la ventana **Estilos de columna y fila**.  Elija cada una de las columnas, elija el botón de opción **Porcentaje** y establezca el ancho de cada columna en el 25 por ciento del ancho total.  A continuación, seleccione **Filas** en la lista desplegable de la parte superior de la ventana y establezca el alto de cada fila en el 25 por ciento.  Cuando haya terminado, elija el botón **Aceptar**.  
  
     Su TableLayoutPanel debería ser ahora una cuadrícula de 4x4, con dieciséis celdas cuadradas del mismo tamaño.  Estas filas y columnas son donde más adelante aparecerán las imágenes de icono.  
  
7.  Asegúrese de que el control TableLayoutPanel esté seleccionado en el editor de formularios.  Para comprobarlo, debe ver **tableLayoutPanel1** en la parte superior de la ventana **Propiedades**.  Si no está seleccionado, elija TableLayoutPanel en el formulario o elíjalo en el control desplegable de la parte superior de la ventana **Propiedades**.  
  
     Con el control TableLayoutPanel seleccionado, abra el cuadro de herramientas y agregue un control **Label** \(situado en la categoría **Controles comunes**\) a la celda superior izquierda de TableLayoutPanel.  Ahora, el control `Label` debería estar seleccionado en el IDE.  Establezca las siguientes propiedades para el control.  
  
    1.  Asegúrese de que la propiedad **BackColor** de la etiqueta esté establecida en **CornflowerBlue**.  
  
    2.  Establezca la propiedad **AutoSize** en **False**.  
  
    3.  Establezca la propiedad **Dock** en **Fill**.  
  
    4.  Establezca la propiedad **TextAlign** en **MiddleCenter** eligiendo el botón de lista desplegable que se encuentra al lado de la propiedad y eligiendo el botón central.  De esta forma, se asegurará de que el icono aparezca en el centro de la celda.  
  
    5.  Elija la propiedad **Font**.  Debe aparecer un botón de puntos suspensivos \(…\).  
  
    6.  Elija el botón de puntos suspensivos y establezca el valor de **Fuente**en **Webdings**, **Estilo de fuente** en **Negrita** y **Tamaño** en **72**.  
  
    7.  Establezca la propiedad **Text** de la etiqueta en la letra **c**.  
  
         La celda superior izquierda de TableLayoutPanel debería contener ahora un cuadro negro centrado sobre un fondo azul.  
  
        > [!NOTE]
        >  La fuente Webdings es una fuente de iconos que se distribuye con el sistema operativo Windows.  En el juego de formar parejas, el jugador necesita encontrar la correspondencia entre pares de iconos, de modo que se usa esta fuente para mostrar los iconos que deben coincidir.  En lugar de colocar **c** en la propiedad **Text**, pruebe a escribir letras diferentes para ver qué iconos se muestran.  Un signo de exclamación es una araña, una N mayúscula es un ojo y una coma es una guindilla.  
  
8.  Elija el control de etiqueta y cópielo en la celda siguiente en TableLayoutPanel. \(Elija las teclas Ctrl\+C o, en la barra de menús, elija **Editar**, **Copiar**\). A continuación, péguelo. \(Elija las teclas Ctrl\+V o, en la barra de menús, elija **Editar**, **Pegar**\). Una copia de la primera etiqueta aparece en la segunda celda de TableLayoutPanel.  Vuelva a pegar el control; aparecerá otra etiqueta en la tercera celda.  Siga pegando los controles `Label` hasta que se llenen todas las celdas.  
  
    > [!NOTE]
    >  Si pega demasiadas veces, el IDE agrega una nueva fila a TableLayoutPanel para que haya espacio para agregar el nuevo control de etiqueta.  La acción se puede deshacer.  Para quitar la nueva celda, elija las teclas Ctrl\+Z o, en la barra de menús, elija **Editar**, **Deshacer**.  
  
     Ya tiene diseñado el formulario.  Debería ser similar a la imagen siguiente.  
  
     ![Formulario inicial del juego de formar parejas](../ide/media/express_tut4step1.png "Express\_Tut4Step1")  
Formulario inicial del juego de formar parejas  
  
### Para continuar o revisar  
  
-   Para ir al siguiente paso del tutorial, vea [Paso 2: Agregar un objeto aleatorio y una lista de iconos](../ide/step-2-add-a-random-object-and-a-list-of-icons.md).  
  
-   Para volver al tema de la información general, vea [Tutorial 3: Crear un juego de formar parejas](../ide/tutorial-3-create-a-matching-game.md).