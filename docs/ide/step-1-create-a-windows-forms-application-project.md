---
title: 'Paso 1: Crear un proyecto de aplicación de Windows Forms'
ms.date: 01/26/2019
ms.topic: conceptual
ms.assetid: 16ac2422-e720-4e3a-b511-bc2a54201a86
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6ccf9ebad32a82f88740e4f7dc0c920d348b6d48
ms.sourcegitcommit: 87d7123c09812534b7b08743de4d11d6433eaa13
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/01/2019
ms.locfileid: "57223005"
---
# <a name="step-1-create-a-windows-forms-application-project"></a>Paso 1: Crear un proyecto de aplicación de Windows Forms

Cuando se crea un visor de imagen, el primer paso consiste en crear un proyecto de aplicación de Windows Forms.

 ![vínculo al vídeo](../data-tools/media/playvideo.gif)Para obtener una versión en vídeo de este tema, vea [Tutorial 1: Create a picture viewer in Visual Basic - Video 1](http://go.microsoft.com/fwlink/?LinkId=205209) (Crear un visor de imágenes en Visual Basic [vídeo 1]) o [Tutorial 1: Create a picture viewer in C# - Video 1](http://go.microsoft.com/fwlink/?LinkId=205199) (Crear un visor de imágenes en C# [vídeo 1]). En estos vídeos se utilizó una versión anterior de Visual Studio, por lo que hay ligeras diferencias en algunos comandos de menú y otros elementos de la interfaz de usuario. Sin embargo, los conceptos y procedimientos funcionan de forma similar en la versión actual de Visual Studio.

## <a name="to-create-a-windows-forms-application-project"></a>Para crear un proyecto de Aplicación de Windows Forms

1. En la barra de menús, elija **Archivo** > **Nuevo** > **Proyecto**. El cuadro de diálogo debe tener un aspecto similar al que se muestra a continuación.

     ![Cuadro de diálogo Nuevo proyecto](../ide/media/newprojectdialogcallouts.png)<br/>
*Cuadro de diálogo **Nuevo proyecto***

2. Elija **Visual C#** o **Visual Basic** en la parte izquierda del cuadro de diálogo **Nuevo proyecto**.

3. En la lista de plantillas, elija **Aplicación de Windows Forms (.NET Framework)**. Asigne un nombre al nuevo formulario **PictureViewer** y, después, pulse el botón **Aceptar**.

    >[!NOTE]
    >Si no ve la plantilla **Aplicación de Windows Forms (.NET Framework)**, use el instalador de Visual Studio para instalar la carga de trabajo **Desarrollo de escritorio de .NET**.<br/><br/>![Carga de trabajo de desarrollo de escritorio de .NET en el instalador de Visual Studio](../ide/media/dot-net-desktop-dev-workload.png)<br/><br/> Para obtener más información, vea la página [Instalación de Visual Studio](../install/install-visual-studio.md).

     Visual Studio crea una solución para el programa. Una solución actúa como un contenedor de todos los proyectos y archivos necesarios para el programa. Estos términos se explicarán con más detalle en secciones posteriores de este tutorial.

4. El entorno de desarrollo contiene tres ventanas: una ventana principal, el **Explorador de soluciones** y la ventana **Propiedades**.

     Si falta alguna de estas ventanas, restaure el diseño de ventana predeterminado; para ello, en la barra de menús, pulse **Ventana** > **Restablecer diseño de la ventana**. También puede mostrar ventanas mediante comandos de menú. En la barra de menús, pulse **Ver** > **Ventana Propiedades** o **Explorador de soluciones**. Si hay otras ventanas abiertas, ciérrelas con el botón **Cerrar** (x) de la esquina superior derecha.

    ::: moniker range="vs-2017"

    - **Ventana principal** En esta ventana, realizará la mayor parte del trabajo, como ejecutar formularios y editar código. La ventana muestra un formulario en el **Editor de formularios**. En la parte superior de la ventana, aparecerán las pestañas **Página principal** y **Form1.cs [Diseño]**. (En Visual Basic, el nombre de la pestaña termina con *.vb* en lugar de *.cs*).

    ::: moniker-end

    ::: moniker range=">=vs-2019"

    - **Ventana principal** En esta ventana, realizará la mayor parte del trabajo, como ejecutar formularios y editar código. La ventana muestra un formulario en el **Editor de formularios**.

    ::: moniker-end

    - **Ventana Explorador de soluciones** En esta ventana, puede ver todos los elementos de la solución y navegar por ellos. Al seleccionar un archivo, cambia el contenido de la ventana **Propiedades**. Si abre un archivo de código (que finaliza en *.cs* para Visual C# y en *.vb* para Visual Basic), aparece el archivo de código o un diseñador para él. Un diseñador es una superficie visual en la que se pueden agregar controles, como botones y listas. En los formularios de Visual Studio, el diseñador se llama **Diseñador de Windows Forms**.

    - **Ventana Propiedades** En esta ventana, puede cambiar las propiedades de los elementos elegidos en las otras ventanas. Por ejemplo, si elige Form1, puede cambiar el título mediante la propiedad **Text** y el color de fondo mediante la propiedad **Backcolor**.

    > [!NOTE]
    > En la línea superior del **Explorador de soluciones** se muestra **Solución "PictureViewer" (1 proyecto)**, lo que significa que Visual Studio ha creado una solución. Una solución puede contener varios proyectos, pero, por ahora, trabajará con soluciones que contengan un solo proyecto.

6. En la barra de menús, pulse **Archivo** > **Guardar todo**.

     Si quiere, también puede pulsar el botón **Guardar todo** de la barra de herramientas que se muestra en la ilustración siguiente.

     ![Botón de la barra de herramientas Guardar todo](../ide/media/express_iconsaveall.png)<br/>
*Botón de la barra de herramientas **Guardar todo***

     Visual Studio rellena automáticamente el nombre de la carpeta y el nombre del proyecto, y después guarda el proyecto en la carpeta de proyectos.

## <a name="to-continue-or-review"></a>Para continuar o revisar

- Para ir al siguiente paso del tutorial, vea [Paso 2: Ejecutar el programa](../ide/step-2-run-your-program.md).

- Para volver al tema de información general, vea [Tutorial 1: Crear un visor de imágenes](../ide/tutorial-1-create-a-picture-viewer.md).

## <a name="see-also"></a>Vea también

- [Creación de una nueva aplicación de Windows Forms](/dotnet/framework/winforms/creating-a-new-windows-form/)