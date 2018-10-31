---
title: 'Tutorial: Compilar una aplicación'
ms.date: 09/25/2017
ms.prod: visual-studio-dev15
ms.technology: vs-ide-compile
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 23d22e5fc3169cc731428e8c5fafff607847c156
ms.sourcegitcommit: 1abb9cf4c3ccb90e3481ea8079272c98aad12875
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/26/2018
ms.locfileid: "50143195"
---
# <a name="walkthrough-build-an-application"></a>Tutorial: Compilar una aplicación

Cuando complete este tutorial, estará más familiarizado con varias opciones que se pueden configurar al compilar aplicaciones con Visual Studio. Creará una configuración de compilación personalizada, ocultará determinados mensajes de advertencia y aumentará la información de los resultados de la compilación para una aplicación de ejemplo.

## <a name="install-the-sample-application"></a>Instalar la aplicación de ejemplo

Descargue el ejemplo [Introducción a la compilación de aplicaciones de WPF](https://code.msdn.microsoft.com/Introduction-to-Building-b8d16419). Elija C# o Visual Basic. Una vez descargado el archivo *.zip*, extráigalo y abra el archivo *ExpenseItIntro.sln* con Visual Studio.

## <a name="create-a-custom-build-configuration"></a>Crear una configuración de compilación personalizada

Cuando se crea una solución, se definen automáticamente configuraciones de compilación de depuración y de versión y sus destinos de plataforma predeterminados para la solución. Es posible personalizar estas configuraciones o crear sus propias configuraciones. Las configuraciones de compilación especifican el tipo de compilación. Las plataformas de compilación especifican el sistema operativo de destino de una aplicación para esa configuración. Para obtener más información, consulte [Descripción de las configuraciones de compilación](../ide/understanding-build-configurations.md), [Descripción de las plataformas de compilación](../ide/understanding-build-platforms.md) y [Cómo: Establecer configuraciones Debug y Release](../debugger/how-to-set-debug-and-release-configurations.md).

Puede cambiar o crear configuraciones y opciones de plataforma mediante el cuadro de diálogo **Administrador de configuración**. En este procedimiento, creará una configuración de compilación para probar.

### <a name="create-a-build-configuration"></a>Crear una configuración de compilación

1. Abra el cuadro de diálogo **Administrador de configuración**.

   ![Menú Compilar, comando Administrador de configuración](../ide/media/buildwalk_configurationmanagerdialogbox.png)

1. En la lista **Configuración de soluciones activas**, elija **\<Nueva...\>**.

1. En el cuadro de diálogo **Nueva configuración de la solución**, asigne a la nueva configuración el nombre `Test`, copie valores de la configuración de **depuración** existente y luego elija el botón **Aceptar**.

   ![Cuadro de diálogo Nueva configuración de la solución](../ide/media/buildwalk_newsolutionconfigdlgbox.png)

1. En la lista **Plataforma de soluciones activas**, elija **\<Nueva...\>**.

1. En el cuadro de diálogo **Nueva plataforma de soluciones**, elija **x64** y no copie valores de la plataforma x86.

   ![Cuadro de diálogo Nueva plataforma de solución](../ide/media/buildwalk_newsolutionplatform.png)

1. Elija el botón **Aceptar** .

   La configuración de soluciones activa ha cambiado a **Prueba** y la plataforma de soluciones activas se ha establecido en x64.

   ![Administrador de configuración con una configuración de prueba](../ide/media/buildwalk_configmanagertestconfig.png)

1. Elija **Cerrar**.

Puede comprobar o cambiar rápidamente la configuración de soluciones activas mediante la lista **Configuraciones de soluciones** de la barra de herramientas **Estándar**.

![Opción Configuración de soluciones de la barra de herramientas estándar](../ide/media/buildwalk_standardtoolbarsolutioncongfig.png)

## <a name="build-the-application"></a>Compilar la aplicación

Después, compilará la solución con la configuración de compilación personalizada.

### <a name="build-the-solution"></a>Compilar la solución

-   En la barra de menús, elija **Compilar** > **Compilar solución**.

    La ventana **Salida** muestra los resultados de la compilación. La compilación se ha realizado correctamente.

## <a name="hide-compiler-warnings"></a>Ocultar advertencias del compilador

A continuación presentamos determinado código que causa que el compilador genere una advertencia.

1. En el proyecto de C#, abra el archivo *ExpenseReportPage.xaml.cs*. En el método **ExpenseReportPage**, agregue el código siguiente: `int i;`.

    O

    En el proyecto de Visual Basic, abra el archivo *ExpenseReportPage.xaml.vb*. En el constructor personalizado **Public Sub New...**, agregue el código siguiente: `Dim i`.

1. Compile la solución.

La ventana **Salida** muestra los resultados de la compilación. La compilación se ha realizado correctamente, pero se han generado advertencias:

![Ventana de salida de Visual Basic](../ide/media/buildwalk_vbbuildoutputwnd.png)

![Ventana de salida de Visual C&#35;](../ide/media/buildwalk_csharpbuildoutputwnd.png)

Es posible ocultar temporalmente determinados mensajes de advertencia durante una compilación en lugar de que se acumulen en los resultados de la compilación.

### <a name="hide-a-specific-c-warning"></a>Ocultar una advertencia específica de C#

1. En el **Explorador de soluciones**, elija el nodo de proyecto de nivel superior.

1. En la barra de menús, elija **Ver** > **Páginas de propiedades**.

     Se abrirá el **Diseñador de proyectos**.

1. Elija la página **Compilación** y, después, en el cuadro **Suprimir advertencias**, especifique el número de advertencia **0168**.

     ![Página Compilación, Diseñador de proyectos](../ide/media/buildwalk_csharpsuppresswarnings.png)

     Para obtener más información, consulte [Compilar (Página, Diseñador de proyectos) (C#)](../ide/reference/build-page-project-designer-csharp.md).

1. Compile la solución.

     La ventana **Salida** solo muestra información de resumen de la compilación.

     ![Ventana de salida, advertencias de compilación de Visual C&#35;](../ide/media/buildwalk_visualcsharpbuildwarnings.png)

### <a name="suppress-all-visual-basic-build-warnings"></a>Suprimir todas las advertencias de compilación de Visual Basic

1. En el **Explorador de soluciones**, elija el nodo de proyecto de nivel superior.

2. En la barra de menús, elija **Ver** > **Páginas de propiedades**.

     Se abrirá el **Diseñador de proyectos**.

3. En la página **Compilación**, active la casilla **Deshabilitar todas las advertencias**.

     ![Página Compilar, Diseñador de proyectos](../ide/media/buildwalk_vbsuppresswarnings.png)

     Para obtener más información, vea [Configurar advertencias en Visual Basic](../ide/configuring-warnings-in-visual-basic.md).

4. Compile la solución.

   La ventana **Salida** solo muestra información de resumen de la compilación.

   ![Ventana de salida, advertencias de compilación de Visual Basic](../ide/media/buildwalk_visualbasicbuildwarnings.png)

   Para obtener más información, consulte [Cómo: Suprimir advertencias del compilador](../ide/how-to-suppress-compiler-warnings.md).

## <a name="display-additional-build-details-in-the-output-window"></a>Mostrar detalles de compilación adicionales en la ventana de salida

Se puede cambiar la cantidad de información sobre el proceso de compilación que aparece en la ventana **Salida**. El nivel de detalle de la compilación se establece normalmente en **Mínimo**, lo que significa que la ventana **Salida** solo muestra un resumen del proceso de compilación, junto con las advertencias y los errores de alta prioridad. Puede mostrar más información sobre la compilación mediante el [cuadro de diálogo Opciones, Proyectos y soluciones, Compilar y ejecutar](../ide/reference/options-dialog-box-projects-and-solutions-build-and-run.md).

> [!IMPORTANT]
> Si se muestra más información, la compilación tardará más tiempo en completarse.

### <a name="change-the-amount-of-information-in-the-output-window"></a>Cambiar la cantidad de información que se muestra en la ventana Salida

1. Abra el cuadro de diálogo **Opciones**.

     ![Comando Opciones del menú Herramientas](../ide/media/exploreide-toolsoptionsmenu.png)

1. Elija la categoría **Proyectos y soluciones** y luego elija la página **Compilar y ejecutar**.

1. En la lista **Detalles de la salida de la compilación del proyecto de MSBuild**, elija **Normal** y después elija el botón **Aceptar**.

1. En la barra de menús, elija **Compilar** > **Limpiar solución**.

1. Compile la solución y después revise la información de la ventana **Salida**.

     La información de compilación incluye la hora a la que se inició la compilación (situada al principio) y el orden en el que se procesaron los archivos. Esta información también incluye la sintaxis real del compilador que Visual Studio ejecuta durante la compilación.

     Por ejemplo, en la compilación de C#, la opción [/nowarn](/dotnet/visual-basic/reference/command-line-compiler/nowarn) muestra el código de advertencia, **1762**, que ha especificado anteriormente en este tema, junto con otras tres advertencias.

     En la compilación de Visual Basic, [/nowarn](/dotnet/visual-basic/reference/command-line-compiler/nowarn) no contiene advertencias concretas para excluir, por lo que no aparece ninguna advertencia.

    > [!TIP]
    > Puede buscar en el contenido de la ventana **Salida** si pulsa las teclas **CTRL**+**F** para mostrar el cuadro de diálogo **Buscar**.

Para obtener más información, consulte [Cómo: Ver, guardar y configurar archivos de registro de compilación](../ide/how-to-view-save-and-configure-build-log-files.md).

## <a name="create-a-release-build"></a>Crear una compilación de versión

Se puede compilar una versión de la aplicación de ejemplo optimizada para su entrega. Para la compilación de versión, especificará que el ejecutable se copie a un recurso compartido de red antes de que se inicie la compilación.

Para obtener más información, consulte [Cómo: Cambiar el directorio de resultados de compilación](../ide/how-to-change-the-build-output-directory.md) y [Compilar y limpiar proyectos y soluciones en Visual Studio](../ide/building-and-cleaning-projects-and-solutions-in-visual-studio.md).

### <a name="specify-a-release-build-for-visual-basic"></a>Especificar una compilación de versión para Visual Basic

1. Abra el **Diseñador de proyectos**.

     ![Menú Ver, comando Páginas de propiedades](../ide/media/buildwalk_viewpropertypages.png)

1. Elija la página **Compilación**.

1. En la lista **Configuración**, elija **Versión**.

1. En la lista **Plataforma**, elija **x86**.

1. En el cuadro **Ruta de acceso de los resultados de la compilación**, especifique una ruta de acceso de red.

     Por ejemplo, puede especificar `\\myserver\builds`.

    > [!IMPORTANT]
    > Puede aparecer un cuadro de mensaje advirtiéndole que el recurso compartido de red que ha especificado puede no ser una ubicación de confianza. Si confía en la ubicación que ha especificado, pulse el botón **Aceptar** en el cuadro de mensaje.

1. Compile la aplicación.

     ![Comando Compilar solución del menú Compilar](../ide/media/exploreide-buildsolution.png)

### <a name="specify-a-release-build-for-c"></a>Especificar una compilación de versión para C# #

1. Abra el **Diseñador de proyectos**.

     ![Menú Ver, comando Páginas de propiedades](../ide/media/buildwalk_viewpropertypages.png)

1. Seleccione la página **Compilación**.

1. En la lista **Configuración**, elija **Versión**.

1. En la lista **Plataforma**, elija **x86**.

1. En el cuadro **Ruta de acceso de salida**, especifique una ruta de acceso de red.

     Por ejemplo, podría especificar `\\myserver\builds`.

    > [!IMPORTANT]
    > Puede aparecer un cuadro de mensaje advirtiéndole que el recurso compartido de red que ha especificado puede no ser una ubicación de confianza. Si confía en la ubicación que ha especificado, pulse el botón **Aceptar** en el cuadro de mensaje.

1. En la **barra de herramientas estándar**, establezca las configuraciones de soluciones en **Versión** y las plataformas de soluciones en **x86**.

1. Compile la aplicación.

     ![Comando Compilar solución del menú Compilar](../ide/media/exploreide-buildsolution.png)

   El archivo ejecutable se copia a la ruta de acceso de red especificada. La ruta de acceso sería `\\myserver\builds\\FileName.exe`.

¡Enhorabuena! Completó correctamente este tutorial.

## <a name="see-also"></a>Vea también

- [Tutorial: Compilar un proyecto (C++)](/cpp/ide/walkthrough-building-a-project-cpp)
- [Información general sobre la precompilación de proyectos de aplicación web ASP.NET](http://msdn.microsoft.com/b940abbd-178d-4570-b441-52914fa7b887)
- [Tutorial: Usar MSBuild](../msbuild/walkthrough-using-msbuild.md)