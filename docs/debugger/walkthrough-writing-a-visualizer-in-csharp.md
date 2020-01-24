---
title: Escribir un visualizador C# en | Microsoft Docs
ms.custom: seodec18
ms.date: 04/12/2019
ms.topic: conceptual
dev_langs:
- CSharp
helpviewer_keywords:
- visualizers, writing
- walkthroughs [Visual Studio], visualizers
ms.assetid: 53467461-8e0f-45ee-9bc4-374bbaeaf00f
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: a46967d5f46c4f495a07d80e5f73cfc9f9d60c1a
ms.sourcegitcommit: 7b07e7b5e06e2e13f622445c568b78a284e1a40d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2020
ms.locfileid: "76542638"
---
# <a name="walkthrough-writing-a-visualizer-in-c"></a>Tutorial: Escribir un visualizador en C\#
En este tutorial se muestra cómo escribir un visualizador sencillo con C#. El visualizador que creará en este tutorial muestra el contenido de una cadena mediante un cuadro de mensaje de formularios Windows Forms. Este sencillo visualizador de cadenas no es especialmente útil, pero muestra los pasos básicos que se deben seguir para crear visualizadores más útiles para otros tipos de datos.

> [!NOTE]
> Los cuadros de diálogo y los comandos de menú que se ven pueden diferir de los descritos en la Ayuda, dependiendo de los valores de configuración o de edición activos. Para cambiar la configuración, vaya al menú **Herramientas**, y elija **Importar y exportar configuraciones**. Para obtener más información, vea [Restablecer la configuración](../ide/environment-settings.md#reset-settings).

El código del visualizador debe colocarse en un archivo DLL, el cual será leído por el depurador. Por lo tanto, el primer paso es crear un proyecto de biblioteca de clases para el archivo DLL.

## <a name="create-a-visualizer-manually"></a>Crear un visualizador manualmente

Siga las tareas siguientes para crear un visualizador.

### <a name="to-create-a-class-library-project"></a>Para crear un proyecto de biblioteca de clases

1. Cree un nuevo proyecto de biblioteca de clases.

    ::: moniker range=">=vs-2019"
    Presione **Esc** para cerrar la ventana de inicio. Presione **Ctrl + Q** para abrir el cuadro de búsqueda, escriba **biblioteca de clases**, elija **plantillas**y, a continuación, elija **crear una nueva biblioteca de clases (.NET Framework)** . En el cuadro de diálogo que se abre, elija **Crear**.
    ::: moniker-end
    ::: moniker range="vs-2017"
    En la barra de menús superior, elija **Archivo** > **Nuevo** > **Proyecto**. En el panel izquierdo del cuadro de diálogo **nuevo proyecto** , en **Visual C#** , elija **.NET Framework**y, a continuación, en el panel central, elija **biblioteca de clases (.NET Framework)** .
    ::: moniker-end

2. Escriba un nombre adecuado para la biblioteca de clases, como `MyFirstVisualizer`y, a continuación, haga clic en **crear** o en **Aceptar**.

   Después de crear la biblioteca de clases, debe agregar una referencia a Microsoft.VisualStudio.DebuggerVisualizers.DLL, para poder utilizar las clases que allí se definen. No obstante, antes de agregar la referencia, debe cambiar los nombres de algunas clases para que sean significativos.

### <a name="to-rename-class1cs-and-add-microsoftvisualstudiodebuggervisualizers"></a>Para cambiar el nombre de Class1.cs y agregar Microsoft.VisualStudio.DebuggerVisualizers

1. En el **Explorador de soluciones**, haga clic con el botón derecho en Class1.cs y elija **Cambiar nombre** en el menú contextual.

2. Cambie el nombre Class1.cs por un nombre significativo, como DebuggerSide.cs.

   > [!NOTE]
   > [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] cambia automáticamente la declaración de clase en DebuggerSide.cs para que coincida con el nuevo nombre del archivo.

3. En el **Explorador de soluciones**, haga clic con el botón derecho en **Referencias** y después elija **Agregar referencia** en el menú contextual.

4. En el cuadro de diálogo **Agregar referencia** , en la pestaña **examinar** , seleccione **examinar** y busque Microsoft. VisualStudio. DebuggerVisualizers. dll.

    Puede encontrar el archivo DLL en *\<directorio de instalación de Visual studio >* subdirectorio \Common7\IDE\PublicAssemblies del directorio de instalación de Visual Studio.

5. Haga clic en **Aceptar**.

6. En DebuggerSide.cs, agregue lo siguiente a las directivas de `using`:

   ```csharp
   using Microsoft.VisualStudio.DebuggerVisualizers;
   ```

   Ahora, ya está listo para crear el código del depurador. Éste es el código que se ejecuta dentro del depurador para mostrar la información que desea visualizar. En primer lugar hay que cambiar la declaración del objeto `DebuggerSide` para que herede de la clase base `DialogDebuggerVisualizer`.

### <a name="to-inherit-from-dialogdebuggervisualizer"></a>Para heredar de DialogDebuggerVisualizer

1. En DebuggerSide.cs, vaya a la línea siguiente del código:

   ```csharp
   public class DebuggerSide
   ```

2. Cambie el código por:

   ```csharp
   public class DebuggerSide : DialogDebuggerVisualizer
   ```

   `DialogDebuggerVisualizer` tiene un método abstracto (`Show`) que debe reemplazar.

#### <a name="to-override-the-dialogdebuggervisualizershow-method"></a>Para reemplazar el método DialogDebuggerVisualizer.Show

- En `public class DebuggerSide`, agregue el siguiente **método:**

  ```csharp
  protected override void Show(IDialogVisualizerService windowService, IVisualizerObjectProvider objectProvider)
  {
  }
  ```

  El método `Show` contiene el código que verdaderamente crea el cuadro de diálogo del visualizador, u otra interfaz de usuario, y muestra la información que se ha pasado del depurador al visualizador. Es necesario agregar el código que crea el cuadro de diálogo y muestra la información. En este tutorial, se realizará este paso mediante un cuadro de mensaje de formularios Windows Forms. En primer lugar, debe agregar una referencia y una directiva de `using` para System. Windows. Forms.

### <a name="to-add-systemwindowsforms"></a>Para agregar System.Windows.Forms

1. En el **Explorador de soluciones**, haga clic con el botón derecho en **Referencias** y después elija **Agregar referencia** en el menú contextual.

2. En el cuadro de diálogo **Agregar referencia** , en la pestaña **examinar** , seleccione **examinar**y busque System. Windows. Forms. dll.

    Puede encontrar el archivo DLL en *C:\Windows\Microsoft.NET\Framework\v4.0.30319*.

3. Haga clic en **Aceptar**.

4. En DebuggerSide.cs, agregue lo siguiente a las directivas de `using`:

   ```csharp
   using System.Windows.Forms;
   ```

   Ahora, agregará código para crear y mostrar la interfaz de usuario para el visualizador. Debido que éste es su primer visualizador, mantendremos la interfaz de usuario sencilla y utilizaremos un cuadro de mensaje.

### <a name="to-show-the-visualizer-output-in-a-dialog-box"></a>Para mostrar el resultado del visualizador en un cuadro de diálogo

1. En el método `Show`, agregue la siguiente línea de código:

   ```csharp
   MessageBox.Show(objectProvider.GetObject().ToString());
   ```

    En este código de ejemplo no se incluye el control de errores. Debe incluir el control de errores en un visualizador real o en cualquier otro tipo de aplicación.

2. En el menú **Compilar**, elija **Compilar MyFirstVisualizer**. El proyecto debería compilarse correctamente. Corrija cualquier error de compilación antes de continuar.

   Ése es el fin del código del depurador. Sin embargo, hay un paso más que realizar; el atributo que indica al lado depurado qué colección de clases incluye el visualizador.

### <a name="to-add-the-debuggee-side-code"></a>Para agregar el código que está siendo depurado

1. Agregue el código de atributo siguiente a DebuggerSide.cs, después de las directivas de `using` pero antes de `namespace MyFirstVisualizer`:

   ```csharp
   [assembly:System.Diagnostics.DebuggerVisualizer(
   typeof(MyFirstVisualizer.DebuggerSide),
   typeof(VisualizerObjectSource),
   Target = typeof(System.String),
   Description = "My First Visualizer")]
   ```

2. En el menú **Compilar**, elija **Compilar MyFirstVisualizer**. El proyecto debería compilarse correctamente. Corrija cualquier error de compilación antes de continuar.

   En este momento, el primer visualizador está terminado. Si ha seguido los pasos correctamente, debería poder compilar el visualizador e instalarlo en [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Sin embargo, antes de instalar un visualizador en [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], debería probarlo para asegurarse de que se ejecuta correctamente. A continuación creará un instrumento de prueba para ejecutar el visualizador sin instalarlo en [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].

### <a name="to-add-a-test-method-to-show-the-visualizer"></a>Para agregar un método de prueba para mostrar el visualizador

1. Agregue el método siguiente a la clase `public DebuggerSide`:

   ```csharp
   public static void TestShowVisualizer(object objectToVisualize)
   {
      VisualizerDevelopmentHost visualizerHost = new VisualizerDevelopmentHost(objectToVisualize, typeof(DebuggerSide));
      visualizerHost.ShowVisualizer();
   }
   ```

2. En el menú **Compilar**, elija **Compilar MyFirstVisualizer**. El proyecto debería compilarse correctamente. Corrija cualquier error de compilación antes de continuar.

   Luego, debe crear un proyecto ejecutable para llamar al archivo DLL del visualizador. Por simplicidad, utilizaremos un proyecto de aplicación de consola.

### <a name="to-add-a-console-application-project-to-the-solution"></a>Para agregar un proyecto de aplicación de consola a la solución

1. En Explorador de soluciones, haga clic con el botón secundario en la solución, elija **Agregar**y, a continuación, haga clic en **nuevo proyecto**.

    ::: moniker range=">=vs-2019"
    En el cuadro de búsqueda, escriba **aplicación de consola**, seleccione **plantillas**y, a continuación, elija **crear una nueva aplicación de consola (.NET Framework)** . En el cuadro de diálogo que se abre, elija **Crear**.
    ::: moniker-end
    ::: moniker range="vs-2017"
    En la barra de menús superior, elija **Archivo** > **Nuevo** > **Proyecto**. En el panel izquierdo del cuadro de diálogo **Nuevo proyecto**, en **Visual C#** , elija **Escritorio de Windows** y luego, en el panel central, **Aplicación de consola (.NET Framework)** .
    ::: moniker-end

2. Escriba un nombre adecuado para la biblioteca de clases, como `MyTestConsole`y, a continuación, haga clic en **crear** o en **Aceptar**.

   Ahora, debe agregar las referencias necesarias para que MyTestConsole pueda llamar a MyFirstVisualizer.

### <a name="to-add-necessary-references-to-mytestconsole"></a>Para agregar las referencias necesarias a MyTestConsole

1. En el **Explorador de soluciones**, haga clic con el botón derecho en **MyTestConsole** y elija **Agregar referencia** en el menú contextual.

2. En el cuadro de diálogo **Agregar referencia** , en la pestaña **examinar** , elija Microsoft. VISUALSTUDIO. DebuggerVisualizers. dll.

3. Haga clic en **Aceptar**.

4. Haga clic con el botón derecho en **MyTestConsole** y elija nuevamente **Agregar referencia**.

5. En el cuadro de diálogo **Agregar referencia**, haga clic en la ficha **Proyectos** y después haga clic en MyFirstVisualizer.

6. Haga clic en **Aceptar**.

   A continuación, agregará el código para finalizar el instrumento de prueba.

### <a name="to-add-code-to-mytestconsole"></a>Para agregar el código a MyTestConsole

1. En el **Explorador de soluciones**, haga clic con el botón derecho en Program.cs y elija **Cambiar nombre** en el menú contextual.

2. Cambie el nombre Program.cs por un nombre más significativo, como TestConsole.cs.

    > [!NOTE]
    > [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] cambia automáticamente la declaración de clase de TestConsole.cs para que coincida con el nuevo nombre del archivo.

3. En TestConsole.cs, agregue el código siguiente a las directivas de `using`:

   ```csharp
   using MyFirstVisualizer;
   ```

4. En el método `Main`, agregue el código siguiente:

   ```csharp
   String myString = "Hello, World";
   DebuggerSide.TestShowVisualizer(myString);
   ```

   Ahora, está listo para probar el primer visualizador.

### <a name="to-test-the-visualizer"></a>Para probar el visualizador

1. En el **Explorador de soluciones**, haga clic con el botón derecho en **MyTestConsole** y, en el menú contextual, elija **Establecer como proyecto de inicio**.

2. En el menú **Depurar**, elija **Iniciar**.

    Se iniciará la aplicación de consola y aparecerá el visualizador, que mostrará la cadena "Hello, World".

   Enhorabuena. Acaba de compilar y probar el primer visualizador.

   Si desea utilizar el visualizador en [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], en lugar de simplemente llamarlo desde el instrumento de prueba, tendrá que instalarlo. Para obtener más información, vea [Cómo: instalar un visualizador](../debugger/how-to-install-a-visualizer.md).

## <a name="create-a-visualizer-using-the-visualizer-item-template"></a>Crear un visualizador mediante la plantilla de elemento del visualizador

Hasta ahora, en este tutorial se ha mostrado cómo crear manualmente un visualizador. Esto se realizó como un ejercicio de aprendizaje. Ahora que sabe cómo funciona un visualizador sencillo, existe una manera más fácil de crear uno: mediante la plantilla de elementos del visualizador.

En primer lugar, debe crear un nuevo proyecto de biblioteca de clases.

### <a name="to-create-a-new-class-library"></a>Para crear una nueva biblioteca de clases

1. En el menú **Archivo**, elija **Nuevo > Proyecto**.

2. En el cuadro de diálogo **nuevo proyecto** , **en C#visual** , seleccione **.NET Framework**.

3. En el panel central, elija **biblioteca de clases**.

4. En el cuadro **Nombre**, escriba un nombre adecuado para la biblioteca de clases como, por ejemplo, MySecondVisualizer.

5. Haga clic en **Aceptar**.

   A continuación, puede agregarle un elemento del visualizador:

### <a name="to-add-a-visualizer-item"></a>Para agregar un elemento del visualizador

1. En el **Explorador de soluciones**, haga clic con el botón derecho en MySecondVisualizer.

2. En el menú contextual, elija **Agregar** y después haga clic en **Nuevo elemento**.

3. En el cuadro de diálogo **Agregar nuevo elemento** , **en C# elementos visuales**, seleccione **visualizador del depurador**.

4. En el cuadro **Nombre**, escriba un nombre adecuado, como SecondVisualizer.cs.

5. Haga clic en **Agregar**.

   Eso es todo lo que tiene que hacer. Examine el archivo SecondVisualizer.cs y observe el código que la plantilla ha agregado por usted. Continúe y experimente con el código. Ahora que conoce los fundamentos, ya puede crear visualizadores más complejos y útiles.

## <a name="see-also"></a>Vea también

- [Arquitectura de un visualizador](../debugger/visualizer-architecture.md)
- [Cómo: Instalar un visualizador](../debugger/how-to-install-a-visualizer.md)
- [Create Custom Visualizers](../debugger/create-custom-visualizers-of-data.md) (Crear visualizadores personalizados)
