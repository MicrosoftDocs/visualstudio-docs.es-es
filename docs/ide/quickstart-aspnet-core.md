---
title: "Uso de Visual Studio para crear una aplicación web ASP.NET Core en C# | Microsoft Docs"
ms.custom: 
ms.date: 10/10/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-acquisition
ms.tgt_pltfrm: 
ms.topic: quickstart
author: gewarren
ms.author: gewarren
manager: ghogen
dev_langs: CSharp
ms.openlocfilehash: 6879d29b1e8c36ce9456fc44cf738a57603a6d50
ms.sourcegitcommit: eb954434c34b4df6fd2264266381b23ce9e6204a
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/22/2017
---
# <a name="quickstart-use-visual-studio-to-create-your-first-aspnet-core-web-app"></a>Inicio rápido: uso de Visual Studio para crear su primera aplicación web ASP.NET Core

En esta introducción al entorno de desarrollo integrado (IDE) de Visual Studio, con una duración de entre 5 y 10 minutos, creará una sencilla aplicación web C# ASP.NET Core. Si todavía no tiene instalado Visual Studio, puede descargarlo de forma gratuita en [esta página](http://www.visualstudio.com).

## <a name="create-a-project"></a>Crear un proyecto

En primer lugar, creará un proyecto de aplicación web ASP.NET Core. En el tipo de proyecto se incluyen los archivos de plantilla, que constituyen una aplicación web funcional por sí mismos, sin necesidad de agregar nada más.

1. Abra Visual Studio 2017.

1. En la barra de menús, elija **Archivo**, **Nuevo**, **Proyecto...**.

1. En el panel de la izquierda del cuadro de diálogo **Nuevo proyecto**, expanda **Visual C#** y seleccione **.NET Core**. En el panel central, elija **Aplicación web ASP.NET Core** y después elija **Aceptar**.

     Si no ve la plantilla de proyecto **.NET Core**, cancele haciendo clic fuera del cuadro de diálogo **Nuevo proyecto** y, en la barra de menús superior, elija **Herramientas**, **Obtener herramientas y características...**. Se iniciará el Instalador de Visual Studio. Elija la carga de trabajo **Desarrollo de ASP.NET y web** y después elija **Modificar**.

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

1. Verá dos líneas de subrayado ondulado debajo de **Environment** y **String**, ya que estos tipos no están dentro del ámbito. Abra la barra de herramientas **Lista de errores** para ver los mismos errores en la lista. Si no ve la barra de herramientas **Lista de errores**, elija **Ver**, **Lista de errores** en la barra de menús superior.

   ![Lista de errores](../ide/media/quickstart-aspnet-errorlist.png)

1. En la ventana del editor, coloque el cursor en cualquiera de las líneas que contenga el error y, a continuación, elija la bombilla Acciones rápidas situada en el margen izquierdo. En el menú desplegable, elija **using System;** para agregar esta directiva a la parte superior del archivo y resolver los errores.

## <a name="run-the-application"></a>Ejecutar la aplicación

1. Presione **CTRL+F5** para ejecutar la aplicación y abrirla en un explorador web.

1. En la parte superior del sitio web, elija **Información** para ver el mensaje del directorio que ha agregado en el método `OnGet()` para la página **Información**.

1. Cierre el explorador web.

¡Enhorabuena por completar este tutorial de inicio rápido! Esperamos que haya aprendido un poco sobre el IDE de Visual Studio. Si quiere profundizar más en sus capacidades, continúe con el tutorial que encontrará en la sección **Tutoriales** de la tabla de contenido.

## <a name="see-also"></a>Vea también

[Introducción a C# y Visual Basic con Visual Studio](getting-started-with-visual-csharp-and-visual-basic.md)  
[Introducción a las páginas de Razor en ASP.NET Core](/aspnet/core/tutorials/razor-pages/razor-pages-start)