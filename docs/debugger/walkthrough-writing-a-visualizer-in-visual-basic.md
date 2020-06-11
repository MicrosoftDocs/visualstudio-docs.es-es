---
title: Escritura de un visualizador en Visual Basic | Microsoft Docs
ms.custom: seodec18
ms.date: 05/27/2020
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- visualizers, writing
- walkthroughs [Visual Studio], visualizers
ms.assetid: c93bf5a1-3e5e-422f-894e-bd72c9bc1b57
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 25720f31c721cae44ed5425631a86b3a41bf475e
ms.sourcegitcommit: d20ce855461c240ac5eee0fcfe373f166b4a04a9
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/29/2020
ms.locfileid: "84180550"
---
# <a name="walkthrough-writing-a-visualizer-in-visual-basic"></a>Tutorial: Escritura un visualizador en Visual Basic

En este tutorial se muestra cómo escribir un visualizador sencillo utilizando [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]. El visualizador que creará en este tutorial muestra el contenido de una cadena mediante un cuadro de mensaje de formularios Windows Forms. Este sencillo visualizador de cadenas es un ejemplo básico que muestra cómo se pueden crear visualizadores para otros tipos de datos más aplicables a sus proyectos.

> [!NOTE]
> Los cuadros de diálogo y los comandos de menú que se ven pueden diferir de los descritos en la Ayuda, dependiendo de los valores de configuración o de edición activos. Para cambiar la configuración, vaya al menú **Herramientas** y elija **Importar y exportar**. Para obtener más información, vea [Restablecer la configuración](../ide/environment-settings.md#reset-settings).

El código del visualizador debe colocarse en un archivo DLL que leerá el depurador. El primer paso es crear un proyecto de biblioteca de clases para el archivo DLL.

## <a name="create-and-prepare-a-class-library-project"></a>Crear y preparar un proyecto de biblioteca de clases

### <a name="to-create-a-class-library-project"></a>Para crear un proyecto de biblioteca de clases

1. Cree un nuevo proyecto de biblioteca de clases.

    ::: moniker range=">=vs-2019"
    Presione **Esc** para cerrar la ventana de inicio. Presione **Ctrl + Q** para abrir el cuadro de búsqueda, escriba **visual basic**, elija **Plantillas** y luego, **Crear una nueva biblioteca de clases (.NET Framework)** . En el cuadro de diálogo que se abre, elija **Crear**.
    ::: moniker-end
    ::: moniker range="vs-2017"
    En la barra de menús superior, elija **Archivo** > **Nuevo** > **Proyecto**. En el panel izquierdo del cuadro de diálogo **Nuevo proyecto**, en **Visual Basic**, elija **.NET Standard** y, luego, en el panel central, **Biblioteca de clases (.NET Standard)** .
    ::: moniker-end

2. Escriba un nombre adecuado para la biblioteca de clases, como `MyFirstVisualizer`, y haga clic en **Crear** o **Aceptar**.

   Cuando haya creado la biblioteca de clases, debe agregar una referencia a Microsoft.VisualStudio.DebuggerVisualizers.DLL, para que pueda utilizar las clases que allí se definen. No obstante, en primer lugar debe asignar un nombre descriptivo al proyecto.

### <a name="to-rename-class1vb-and-add-microsoftvisualstudiodebuggervisualizers"></a>Para cambiar el nombre de Class1.vb y agregar Microsoft.VisualStudio.DebuggerVisualizers

1. En el **Explorador de soluciones**, haga clic con el botón derecho en **Class1.vb** y, en el menú contextual, haga clic en **Cambiar nombre**.

2. Cambie el nombre Class1.vb por un nombre significativo, como DebuggerSide.vb.

   > [!NOTE]
   > [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] cambia automáticamente la declaración de clase en DebuggerSide.vb para que coincida con el nuevo nombre del archivo.

3. En el **Explorador de soluciones**, haga clic con el botón derecho en **Mi primer visualizador** y, a continuación, haga clic en **Agregar referencia** en el menú contextual.

4. En el cuadro de diálogo **Agregar referencia**, en la pestaña **Examinar**, seleccione **Examinar** y busque Microsoft.VisualStudio.DebuggerVisualizers.DLL.

    Puede encontrar el archivo DLL en el subdirectorio *\<Visual Studio Install Directory>\Common7\IDE\PublicAssemblies* del directorio de instalación de Visual Studio.

5. Haga clic en **Aceptar**.

6. En DebuggerSide.vb, agregue la instrucción siguiente a las instrucciones `Imports`:

   ```vb
   Imports Microsoft.VisualStudio.DebuggerVisualizers
   ```

## <a name="add-the-debugger-side-code"></a>Agregar el código depurado
 Ahora, ya está listo para crear el código del depurador. Éste es el código que se ejecuta dentro del depurador para mostrar la información que desea visualizar. En primer lugar hay que cambiar la declaración del objeto `DebuggerSide` para que herede de la clase base `DialogDebuggerVisualizer`.

### <a name="to-inherit-from-dialogdebuggervisualizer"></a>Para heredar de DialogDebuggerVisualizer

1. En DebuggerSide.vb, vaya a la línea siguiente del código:

   ```vb
   Public Class DebuggerSide
   ```

2. Edite el código de forma que presente el siguiente aspecto:

   ```vb
   Public Class DebuggerSide
   Inherits DialogDebuggerVisualizer
   ```

   `DialogDebuggerVisualizer` tiene un método abstracto, `Show`, que debe reemplazar.

### <a name="to-override-the-dialogdebuggervisualizershow-method"></a>Para reemplazar el método DialogDebuggerVisualizer.Show

- En `public class DebuggerSide`, agregue el método siguiente:

  ```vb
  Protected Overrides Sub Show(ByVal windowService As Microsoft.VisualStudio.DebuggerVisualizers.IDialogVisualizerService, ByVal objectProvider As Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider)

      End Sub
  ```

  El método `Show` contiene el código que verdaderamente crea el cuadro de diálogo del visualizador, u otra interfaz de usuario, y muestra la información que se ha pasado del depurador al visualizador. Es necesario agregar el código que crea el cuadro de diálogo y muestra la información. En este tutorial, se realizará este paso mediante un cuadro de mensaje de formularios Windows Forms. En primer lugar debe agregar una referencia y una instrucción `Imports` para <xref:System.Windows.Forms>.

### <a name="to-add-systemwindowsforms"></a>Para agregar System.Windows.Forms

1. En el **Explorador de soluciones**, haga clic con el botón derecho en **Referencias** y, a continuación, haga clic en **Agregar referencia** en el menú contextual.

2. En el cuadro de diálogo **Agregar referencia**, en la pestaña **Examinar**, seleccione **Examinar** y busque System.Windows.Forms.DLL.

    Puede encontrar el archivo DLL en *C:\Windows\Microsoft.NET\Framework\v4.0.30319*.

3. Haga clic en **Aceptar**.

4. En DebuggerSide.cs, agregue la instrucción siguiente a las instrucciones `Imports`:

    ```vb
    Imports System.Windows.Forms
    ```

## <a name="create-your-visualizers-user-interface"></a>Crear la interfaz de usuario del visualizador
 Ahora, agregará código para crear y mostrar la interfaz de usuario para el visualizador. Debido que éste es su primer visualizador, mantendrá la interfaz de usuario sencilla y utilizará un cuadro de mensaje.

### <a name="to-show-the-visualizer-output-in-a-dialog-box"></a>Para mostrar el resultado del visualizador en un cuadro de diálogo

1. En el método `Show`, agregue la siguiente línea de código:

    ```vb
    MessageBox.Show(objectProvider.GetObject().ToString())
    ```

     En este código de ejemplo no se incluye el control de errores. Debe incluir el control de errores en un visualizador real o en cualquier otro tipo de aplicación.

2. En el menú **Compilar**, haga clic en **Compilar MyFirstVisualizer**. El proyecto debería compilarse correctamente. Corrija cualquier error de compilación antes de continuar.

## <a name="add-the-necessary-attribute"></a>Agregar el atributo necesario
 Ése es el fin del código del depurador. Sin embargo, hay un paso más que realizar: el atributo que indica al lado depurado qué colección de clases incluye el visualizador.

### <a name="to-add-the-type-to-visualize-for-the-debuggee-side-code"></a>Para agregar el tipo que se va a visualizar en el código del lado depurado

En el código del depurador, especifique el tipo que se va a visualizar (el origen del objeto) en el lado depurado con el atributo <xref:System.Diagnostics.DebuggerVisualizerAttribute>. La propiedad `Target` establece el tipo que se va a visualizar.

1. Agregue el código de atributo siguiente a DebuggerSide.vb, después de las instrucciones `Imports`, pero antes de `namespace MyFirstVisualizer`:

    ```vb
    <Assembly: System.Diagnostics.DebuggerVisualizer(GetType(MyFirstVisualizer.DebuggerSide), GetType(VisualizerObjectSource), Target:=GetType(System.String), Description:="My First Visualizer")>
    ```

2. En el menú **Compilar**, haga clic en **Compilar MyFirstVisualizer**. El proyecto debería compilarse correctamente. Corrija cualquier error de compilación antes de continuar.

## <a name="create-a-test-harness"></a>Crear un instrumento de prueba
 En este momento, el primer visualizador está terminado. Si ha seguido los pasos correctamente, debería poder compilar el visualizador e instalarlo en [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Sin embargo, antes de instalar un visualizador en [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], debería probarlo para asegurarse de que se ejecuta correctamente. A continuación creará un instrumento de prueba para ejecutar el visualizador sin instalarlo en [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].

### <a name="to-add-a-test-method-to-show-the-visualizer"></a>Para agregar un método de prueba para mostrar el visualizador

1. Agregue el método siguiente a la clase `public DebuggerSide`:

   ```vb
   Shared Public Sub TestShowVisualizer(ByVal objectToVisualize As Object)
       Dim visualizerHost As New VisualizerDevelopmentHost(objectToVisualize, GetType(DebuggerSide))
   visualizerHost.ShowVisualizer()
   End Sub
   ```

2. En el menú **Compilar**, haga clic en **Compilar MyFirstVisualizer**. El proyecto debería compilarse correctamente. Corrija cualquier error de compilación antes de continuar.

   Luego, debe crear un proyecto ejecutable para llamar al archivo DLL del visualizador. Para que resulte más sencillo, utilice un proyecto de aplicación de consola.

### <a name="to-add-a-console-application-project-to-the-solution"></a>Para agregar un proyecto de aplicación de consola a la solución

1. En el Explorador de soluciones, haga clic con el botón derecho en la solución; luego, elija **Agregar** y haga clic en **Nuevo proyecto**.

    ::: moniker range=">=vs-2019"
    En el cuadro de búsqueda, escriba **visual basic**, elija **Plantillas** y, luego, **Create a new Console App (.NET Framework)** [Crear una nueva aplicación de consola (.NET Framework)]. En el cuadro de diálogo que se abre, elija **Crear**.
    ::: moniker-end
    ::: moniker range="vs-2017"
    En la barra de menús superior, elija **Archivo** > **Nuevo** > **Proyecto**. En el panel izquierdo del cuadro de diálogo **Nuevo proyecto**, en **Visual Basic**, elija **Escritorio de Windows** y luego, en el panel central, **Aplicación de consola (.NET Framework)** .
    ::: moniker-end

2. Escriba un nombre adecuado para la biblioteca de clases, como `MyTestConsole`, y haga clic en **Crear** o **Aceptar**.

   Ahora, debe agregar las referencias necesarias para que MyTestConsole pueda llamar a MyFirstVisualizer.

### <a name="to-add-necessary-references-to-mytestconsole"></a>Para agregar las referencias necesarias a MyTestConsole

1. En el **Explorador de soluciones**, haga clic con el botón derecho en **MyTestConsole** y, luego, en **Agregar referencia**, en el menú contextual.

2. En el cuadro de diálogo **Agregar referencia**, en la pestaña **Examinar**, haga clic en Microsoft.VisualStudio.DebuggerVisualizers.

3. Haga clic en **Aceptar**.

4. Haga clic con el botón derecho en **MyTestConsole** y, a continuación, vuelva a hacer clic en **Agregar referencia**.

5. En el cuadro de diálogo **Agregar referencia**, haga clic en la pestaña **Proyectos** y, a continuación, seleccione MyFirstVisualizer.

6. Haga clic en **Aceptar**.

## <a name="finish-your-test-harness-and-test-your-visualizer"></a>Finalizar el instrumento de prueba y probar el visualizador
 A continuación, agregará el código para finalizar el instrumento de prueba.

### <a name="to-add-code-to-mytestconsole"></a>Para agregar el código a MyTestConsole

1. En el **Explorador de soluciones**, haga clic con el botón derecho en **Program.vb** y, en el menú contextual, haga clic en **Cambiar nombre**.

2. Edite el nombre de Module1.vb por uno adecuado, como por ejemplo **TestConsole.vb**.

    Tenga en cuenta que [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] cambia automáticamente la declaración de clase de TestConsole.vb para que coincida con el nuevo nombre de archivo.

3. En TestConsole. vb, agregue la instrucción `Imports` siguiente:

   ```vb
   Imports MyFirstVisualizer
   ```

4. En el método `Main`, agregue el código siguiente:

   ```vb
   Dim myString As String = "Hello, World"
   DebuggerSide.TestShowVisualizer(myString)
   ```

   Ahora está preparado para probar el primer visualizador.

### <a name="to-test-the-visualizer"></a>Para probar el visualizador

1. En el **Explorador de soluciones**, haga clic con el botón derecho en **MyTestConsole** y, en el menú contextual, en **Establecer como proyecto de inicio**.

2. En el menú **Depurar**, haga clic en **Iniciar**.

    Se inicia la aplicación de consola. Aparecerá el visualizador y mostrará la cadena "Hello, World".

   Enhorabuena. Acaba de compilar y probar el primer visualizador.

   Si desea utilizar el visualizador en [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], en lugar de simplemente llamarlo desde el instrumento de prueba, tendrá que instalarlo. Para obtener más información, vea [Cómo: instalar un visualizador](../debugger/how-to-install-a-visualizer.md).

## <a name="see-also"></a>Vea también

- [Arquitectura de un visualizador](../debugger/visualizer-architecture.md)
- [Cómo: instalar un visualizador](../debugger/how-to-install-a-visualizer.md)
- [Create Custom Visualizers](../debugger/create-custom-visualizers-of-data.md) (Crear visualizadores personalizados)