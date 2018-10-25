---
title: 'Paso 3: Establecer las propiedades del formulario | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 634ef037-1525-48c8-ac7f-abf04be69376
caps.latest.revision: 20
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 64e197e3f6f34cc46d91c330b4d5f80b3c6ce578
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49848636"
---
# <a name="step-3-set-your-form-properties"></a>Paso 3: Establecer las propiedades del formulario
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Después, se usa la ventana **Propiedades** para cambiar la apariencia del formulario.  
  
 ![vínculo al vídeo](../data-tools/media/playvideo.gif "PlayVideo")Para obtener una versión en vídeo de este tema, vea el [Tutorial 1: Crear un visor de imágenes en Visual Basic (vídeo 1)](http://go.microsoft.com/fwlink/?LinkId=205209) o el [Tutorial 1: Crear un visor de imágenes en C# (vídeo 1)](http://go.microsoft.com/fwlink/?LinkId=205199). En estos vídeos se utilizó una versión anterior de Visual Studio, por lo que hay ligeras diferencias en algunos comandos de menú y otros elementos de la interfaz de usuario. Sin embargo, los conceptos y procedimientos funcionan de forma similar en la versión actual de Visual Studio.  
  
### <a name="to-set-your-form-properties"></a>Para establecer las propiedades del formulario  
  
1. Asegúrese de que está en el Diseñador de Windows Forms. En el entorno de desarrollo integrado (IDE) de Visual Studio, elija la pestaña **Form1.cs [Diseño]** (o la pestaña **Form1.vb [Diseño]** en Visual Basic).  
  
2. Elija cualquier parte del formulario **Form1** para seleccionarlo. Examine la ventana **Propiedades**, que ahora debería mostrar las propiedades del formulario. Los formularios tienen varias propiedades. Por ejemplo, puede establecer el color del primero plano y del fondo, el texto de título que aparece en la parte superior del formulario, el tamaño del formulario y otras propiedades.  
  
   > [!NOTE]
   >  Si la ventana **Propiedades** no aparece, detenga el programa eligiendo el botón cuadrado **Detener depuración** de la barra de herramientas o simplemente cierre la ventana. Si se detiene el programa y aún no ve la ventana **Propiedades**, en la barra de menús, elija **Ver**, **Ventana Propiedades**.  
  
3. Una vez seleccionado el formulario, busque la propiedad **Texto** en la ventana **Propiedades**. En función del orden de la lista, puede que deba desplazarse hacia abajo. Elija **Texto**, escriba **Visor de imágenes** y elija ENTRAR.  Ahora, el formulario debería tener el texto **Visor de imágenes** en la barra de título y la ventana **Propiedades** debería parecerse a la siguiente.  
  
    ![Ventana Propiedades](../ide/media/express-edittextproperty.png "Express_EditTextProperty")  
   Propiedades (ventana)  
  
   > [!NOTE]
   >  Las propiedades se pueden ordenar en vistas por categorías o alfabética. Puede alternar entre estas dos vistas con los botones de la ventana **Propiedades**. En este tutorial, resulta más fácil encontrar las propiedades en la vista alfabética.  
  
4. Vuelva al Diseñador de Windows Forms. Elija el controlador de arrastre inferior derecho del formulario, que es el cuadradito blanco que aparece en el vértice inferior derecho del formulario y tiene el siguiente aspecto.  
  
    ![Controlador de arrastre](../ide/media/express-bottomrt-drag.png "Express_BottomRT_Drag")  
   Controlador de arrastre  
  
    Arrastre el controlador para cambiar el tamaño del formulario de modo que resulte más ancho y un poco más alto.  
  
5. Fíjese en la ventana **Propiedades** y observe que la propiedad **Size** ha cambiado. La propiedad **Size** cambia cada vez que se cambia el tamaño del formulario. Pruebe a arrastrar el controlador del formulario para cambiar su tamaño a unas medidas aproximadas (no es necesario que sean exactas) de 550, 350, que son las que deberían funcionar bien para este proyecto. Si quiere, también puede escribir los valores directamente en la propiedad **Size** y presionar la tecla ENTRAR.  
  
6. Ejecute el programa de nuevo. Recuerde que puede utilizar cualquiera de los métodos siguientes para ejecutar el programa.  
  
   - Elija la tecla **F5**.  
  
   - En la barra de menús, seleccione **Depurar**, **Iniciar depuración**.  
  
   - En la barra de herramientas, elija el botón **Iniciar depuración**, que es similar al siguiente.  
  
      ![Botón de la barra de herramientas Iniciar depuración](../ide/media/express-icondebug.png "Express_IconDebug")  
     Botón de la barra de herramientas Iniciar depuración  
  
     Exactamente igual que antes, el IDE compila y ejecuta el programa, y aparece una ventana.  
  
7. Antes de ir al paso siguiente, detenga el programa, porque el IDE no le permitirá cambiarlo mientras está en ejecución. Recuerde que puede utilizar cualquiera de los métodos siguientes para detener el programa.  
  
   -   En la barra de herramientas, elija el botón **Detener depuración**.  
  
   -   En la barra de menús, seleccione **Depurar**, **Detener depuración**.  
  
   -   Elija el botón X de la esquina superior derecha de la ventana **Form1**.  
  
### <a name="to-continue-or-review"></a>Para continuar o revisar  
  
-   Para ir al paso siguiente del tutorial, vea [Paso 4: Diseñar un formulario con un control TableLayoutPanel](../ide/step-4-lay-out-your-form-with-a-tablelayoutpanel-control.md).  
  
-   Para volver al paso anterior del tutorial, vea [Paso 2: Ejecutar el programa](../ide/step-2-run-your-program.md).



