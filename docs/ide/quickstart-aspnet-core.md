---
title: Uso de Visual Studio para crear una aplicación web ASP.NET Core en C# | Microsoft Docs
ms.custom: ''
ms.date: 10/10/2017
ms.reviewer: ''
ms.suite: ''
ms.technology: vs-acquisition
ms.tgt_pltfrm: ''
ms.topic: quickstart
author: TerryGLee
ms.author: tglee
manager: ghogen
dev_langs:
- CSharp
ms.workload:
- aspnet
- dotnetcore
ms.openlocfilehash: 654dd237dab7f0f320c399e3da1b4f1d24537750
ms.sourcegitcommit: e01ccb5ca4504a327d54f33589911f5d8be9c35c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/15/2018
---
# <a name="quickstart-use-visual-studio-to-create-your-first-aspnet-core-web-app"></a>Inicio rápido: uso de Visual Studio para crear su primera aplicación web ASP.NET Core

En esta introducción al entorno de desarrollo integrado (IDE) de Visual Studio, con una duración de entre 5 y 10 minutos, creará una sencilla aplicación web C# ASP.NET Core.

Si todavía no tiene instalado Visual Studio, vaya a la página de [descargas de Visual Studio](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs) para instalarlo de forma gratuita.

## <a name="create-a-project"></a>Crear un proyecto

En primer lugar, creará un proyecto de aplicación web ASP.NET Core. En el tipo de proyecto se incluyen los archivos de plantilla, que constituyen una aplicación web funcional por sí mismos, sin necesidad de agregar nada más.

1. Abra Visual Studio 2017.

1. En la barra de menús superior, seleccione **Archivo** > **Nuevo** > **Proyecto...**

1. En el panel de la izquierda del cuadro de diálogo **Nuevo proyecto**, expanda **Visual C#** y seleccione **.NET Core**. En el panel central, elija **Aplicación web ASP.NET Core** y después elija **Aceptar**.

     Si no ve la categoría de plantilla de proyecto de **.NET Core**, elija el vínculo **Abrir el instalador de Visual Studio** en el panel de la izquierda. Se iniciará el Instalador de Visual Studio. Elija la carga de trabajo **Desarrollo de ASP.NET y web** y después elija **Modificar**.

     ![Carga de trabajo ASP.NET en el instalador de Visual Studio](../ide/media/quickstart-aspnet-workload.png)

1. En el cuadro de diálogo **Nueva aplicación web ASP.NET Core**, seleccione **ASP.NET Core 2.0** en el menú desplegable situado en la parte superior. Si en la lista no aparece **ASP.NET Core 2.0**, debe instalarlo siguiendo el vínculo **Descargar** que aparece en una barra amarilla en la parte superior del cuadro de diálogo. Elija **Aceptar**.

   ![Cuadro de diálogo Nueva aplicación web ASP.NET Core](../ide/media/quickstart-aspnet-core20.png)

## <a name="explore-the-ide"></a>Explorar el IDE

1. En la barra de herramientas del **Explorador de soluciones**, expanda la carpeta **Páginas** y después elija **About.cshtml** para abrirla en el editor. Este archivo se corresponde con una página denominada **Información** de la aplicación web.

1. En el editor, elija `AboutModel`, y después presione **F12** o elija **Ir a definición** en el menú contextual (clic con el botón derecho). Este comando le lleva a la definición de la clase `AboutModel` de C#.

   ![Menú contextual Ir a definición](../ide/media/quickstart-aspnet-gotodefinition.png)

1. A continuación, limpiaremos las directivas `using` en la parte superior del archivo empleando un acceso directo sencillo. Elija cualquiera de las directivas atenuadas y aparecerá una bombilla [Acciones rápidas](../ide/quick-actions.md) justo debajo del símbolo de intercalación o en el margen izquierdo. Elija la bombilla y después elija **Eliminar instrucciones Using innecesarias**.

     La instrucciones Using innecesarias se eliminan del archivo.

1. Cambie el cuerpo del método `OnGet()` por el código siguiente:

 ```csharp
 public void OnGet()
 {
     string directory = Environment.CurrentDirectory;
     Message = String.Format("Your directory is {0}.", directory);
 }
 ```

1. Verá dos líneas de subrayado ondulado debajo de **Environment** y **String**, ya que estos tipos no están dentro del ámbito. Abra la barra de herramientas **Lista de errores** para ver los mismos errores en la lista. Si no ve la barra de herramientas **Lista de errores**, elija **Ver** > **Lista de errores** en la barra de menús superior.

   ![Lista de errores](../ide/media/quickstart-aspnet-errorlist.png)

1. En la ventana del editor, coloque el cursor en cualquiera de las líneas que contenga el error y, a continuación, elija la bombilla Acciones rápidas situada en el margen izquierdo. En el menú desplegable, elija **using System;** para agregar esta directiva a la parte superior del archivo y resolver los errores.

## <a name="run-the-application"></a>Ejecutar la aplicación

1. Presione **Ctrl**+**F5** para ejecutar la aplicación y abrirla en un explorador web.

1. En la parte superior del sitio web, elija **Información** para ver el mensaje del directorio que ha agregado en el método `OnGet()` para la página **Información**.

1. Cierre el explorador web.

> [!NOTE]
> Si recibe un mensaje de error que indica **No se puede conectar al servidor web "IIS Express"**, cierre Visual Studio y, luego, ábralo con la opción **Ejecutar como administrador** que aparece si hace clic con el botón derecho o en el menú contextual. A continuación, vuelva a ejecutar la aplicación.

¡Enhorabuena por completar este tutorial de inicio rápido! Esperamos que haya aprendido un poco sobre el IDE de Visual Studio. Si quiere profundizar más en sus capacidades, continúe con el tutorial que encontrará en la sección **Tutoriales** de la tabla de contenido.

## <a name="next-steps"></a>Pasos siguientes
¡Enhorabuena por completar este tutorial de inicio rápido! Esperamos que haya aprendido un poco sobre C#, ASP.NET Core y el IDE de Visual Studio. Para obtener más información, continúe con el tutorial siguiente.

> [!div class="nextstepaction"]
> [Introducción a C# y ASP.NET Core en Visual Studio](tutorial-csharp-aspnet-core.md)
