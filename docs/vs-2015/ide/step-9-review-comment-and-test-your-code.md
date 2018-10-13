---
title: 'Paso 9: Revisar, comentar y probar el código | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f26f79ba-c91b-4164-b87f-679a1b231c09
caps.latest.revision: 31
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 3743c31aeca3c6e34afa84ed8c9ee3ddd59d98a1
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49300409"
---
# <a name="step-9-review-comment-and-test-your-code"></a>Paso 9: Revisar, comentar y probar el código
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

A continuación, se agrega un comentario al código. Un comentario es una nota que no cambia la forma de comportarse del programa. Hace que resulte más fácil entender el código a la persona que lo lee. Agregar comentarios al código es un hábito recomendable. En Visual C#, se utilizan dos barras diagonales (//) para marcar una línea como comentario. En Visual Basic, se utiliza una comilla sencilla (') para marcar una línea como comentario. Después de agregar un comentario, se prueba el programa. Es recomendable ejecutar y probar el código con frecuencia mientras trabaja en sus proyectos para que pueda detectar y corregir pronto cualquier problema, antes de que la complejidad del código aumente. Esto se denomina *prueba iterativa*.  
  
 Acaba de compilar algo que funciona y, aunque todavía no está terminado, ya es capaz de cargar una imagen. Antes de agregar un comentario al código y probarlo, dedique un tiempo a revisar los conceptos del código, porque los utilizará con frecuencia:  
  
-   Al hacer doble clic en el botón **Show a picture** (Mostrar una imagen) en el Diseñador de Windows Forms, el IDE agregó automáticamente un *método* al código del programa.  
  
-   Los métodos permiten organizar el código: son la manera de agrupar las partes del código.  
  
-   Casi siempre, un método realiza una cantidad reducida de acciones en un orden concreto; por ejemplo, el método `showButton_Click()` muestra un cuadro de diálogo y, a continuación, carga una imagen.  
  
-   Un método se compone de *instrucciones* o líneas de código. Podemos considerar que un método es una manera de empaquetar instrucciones de código juntas.  
  
-   Cuando se ejecuta un método, o se le *llama*, se ejecutan las instrucciones que contiene en orden, una tras otra, empezando por la primera.  
  
     A continuación, se muestra un ejemplo de una instrucción.  
  
    ```csharp  
    pictureBox1.Load(openFileDialog1.FileName);  
    ```  
  
    ```vb  
    pictureBox1.Load(openFileDialog1.FileName)  
    ```  
  
     Las instrucciones son lo que permite que el programa haga cosas. En Visual C#, una instrucción finaliza siempre en un signo de punto y coma. En Visual Basic, el final de una línea es el final de una instrucción. (No se necesita indicar el signo de punto y coma en Visual Basic.) La instrucción anterior ordena al control `PictureBox` que cargue el archivo que el usuario ha seleccionado con el componente **OpenFileDialog**.  
  
 ![vínculo al vídeo](../data-tools/media/playvideo.gif "PlayVideo")Para obtener una versión en vídeo de este tema, vea el [Tutorial 1: Crear un visor de imágenes en Visual Basic (vídeo 5)](http://go.microsoft.com/fwlink/?LinkId=205216) o el [Tutorial 1: Crear un visor de imágenes en C# (vídeo 5)](http://go.microsoft.com/fwlink/?LinkId=205206). En estos vídeos se utilizó una versión anterior de Visual Studio, por lo que hay ligeras diferencias en algunos comandos de menú y otros elementos de la interfaz de usuario. Sin embargo, los conceptos y procedimientos funcionan de forma similar en la versión actual de Visual Studio.  
  
### <a name="to-add-comments"></a>Para agregar comentarios  
  
1.  Agregue el siguiente comentario al código.  
  
     [!code-csharp[VbExpressTutorial1Step9_10#1](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial1step9_10/cs/form1.cs#1)]
     [!code-vb[VbExpressTutorial1Step9_10#1](../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial1step9_10/vb/form1.vb#1)]  
  
    > [!NOTE]
    >  El controlador de eventos Click del botón **showButton** ya está completado y funciona. Ha empezado a escribir código, comenzando por una instrucción `if`. Una instrucción `if` es la manera de ordenar al programa: "Compruebe esto y, si se cumple, realice estas acciones". En este caso, le está diciendo al programa que abra el cuadro de diálogo **Abrir archivo** y que, si el usuario selecciona un archivo y elige el botón **Aceptar**, cargue ese archivo en PictureBox.  
  
    > [!TIP]
    >  El IDE se ha creado para facilitar la tarea de escribir código. Los *fragmentos de código* constituyen una manera de conseguirlo. Un fragmento de código es un acceso directo que se expande para crear un bloque pequeño de código.  
    >   
    >  Puede ver todos los fragmentos de código disponibles. En la barra de menús, elija **Herramientas**, **Administrador de fragmentos de código**. En Visual C#, el fragmento de código `if` está en **Visual C#**. En Visual Basic, los fragmentos de código `if` están en **Condicionales y bucles**, **Code Patterns** (Patrones de código). Este administrador se puede utilizar para examinar los fragmentos de código existentes o agregar los suyos propios.  
    >   
    >  Para activar un fragmento de código mientras está especificando el código, escríbalo y elija la tecla TAB. Muchos fragmentos de código aparecen en la ventana **IntelliSense**, motivo por el cual la tecla TAB se elige dos veces: la primera para seleccionar el fragmento de código en la ventana **IntelliSense** y la segunda para indicarle al IDE que lo use. (IntelliSense admite el fragmento de código `if`, pero no el fragmento de código `ifelse`.)  
  
2.  Guarde el programa antes de ejecutarlo, para ello, elija el botón de la barra de herramientas **Guardar todo**, que se muestra a continuación.  
  
     ![Botón de la barra de herramientas Guardar todo](../ide/media/express-iconsaveall.png "Express_IconSaveAll")  
Botón Guardar todo  
  
     Si quiere, para guardar el programa, elija **Archivo**, **Guardar todo** en la barra de menús. El procedimiento recomendado consiste en guardar desde el principio y a menudo.  
  
     Mientras se ejecuta, el programa debería parecerse a la siguiente imagen.  
  
     ![Visor de imágenes](../ide/media/express-pictureviewerdonerun.png "Express_PictureViewerDoneRun")  
Visor de imágenes  
  
### <a name="to-test-your-program"></a>Para probar el programa  
  
1.  Elija la tecla F5 o el botón de la barra de herramientas **Iniciar depuración** .  
  
2.  Elija el botón **Show a picture** (Mostrar una imagen) para ejecutar el código que acaba de escribir. Primero, el programa abre un cuadro de diálogo **Abrir archivo**. Compruebe que los filtros aparecen en la lista desplegable **Tipo de archivo** en la parte inferior del cuadro de diálogo. A continuación, navegue hasta una imagen y ábrala. Normalmente, encontrará imágenes de ejemplo que se distribuyen con el sistema operativo Windows en la carpeta **Mis documentos**, dentro de la carpeta **Mis imágenes\Imágenes de muestra**.  
  
    > [!NOTE]
    >  Si no ve ninguna imagen en el cuadro de diálogo **Select a picture file** (Seleccionar un archivo de imagen), asegúrese de que el filtro "Todos los archivos (*.\*)" esté seleccionado en la lista desplegable situada en la parte inferior derecha del cuadro de diálogo.  
  
3.  Cargue una imagen y esta aparecerá en el control PictureBox. A continuación intente cambiar el tamaño del formulario arrastrando los bordes. Como el control PictureBox está acoplado dentro de un control TableLayoutPanel, que a su vez está acoplado en el formulario, el ancho del área de imagen se ajustará al ancho del formulario y el alto ocupará el 90 por ciento superior del formulario. Por este motivo hemos utilizado los contenedores TableLayoutPanel y FlowLayoutPanel: mantienen el tamaño del formulario correcto cuando el usuario lo modifica.  
  
     En este momento, las imágenes más grandes sobrepasan los bordes del visor de imágenes. En el paso siguiente, agregará código para que las imágenes se ajusten a la ventana.  
  
### <a name="to-continue-or-review"></a>Para continuar o revisar  
  
-   Para ir al paso siguiente del tutorial, vea [Paso 10: Escribir código para botones adicionales y una casilla](../ide/step-10-write-code-for-additional-buttons-and-a-check-box.md).  
  
-   Para volver al paso anterior del tutorial, vea [Paso 8: Escribir código para el controlador de eventos del botón Mostrar una imagen](../ide/step-8-write-code-for-the-show-a-picture-button-event-handler.md).



