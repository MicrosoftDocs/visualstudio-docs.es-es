---
title: 'Tutorial: escribir un visualizador en Visual Basic | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- visualizers, writing
- walkthroughs [Visual Studio], visualizers
ms.assetid: c93bf5a1-3e5e-422f-894e-bd72c9bc1b57
caps.latest.revision: 25
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 954bd976317f5b5ad577b1236c9d7421c2d50315
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "65688206"
---
# <a name="walkthrough-writing-a-visualizer-in-visual-basic"></a>Tutorial: Escritura un visualizador en Visual Basic
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

En este tutorial se muestra cómo escribir un visualizador sencillo utilizando [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]. El visualizador que creará en este tutorial muestra el contenido de una cadena mediante un cuadro de mensaje de formularios Windows Forms. Este sencillo visualizador de cadenas es un ejemplo básico que muestra cómo se pueden crear visualizadores para otros tipos de datos más aplicables a sus proyectos.  
  
> [!NOTE]
> Los cuadros de diálogo y los comandos de menú que se ven pueden diferir de los descritos en la Ayuda, dependiendo de los valores de configuración o de edición activos. Para cambiar la configuración, vaya al menú **Herramientas** y elija **Importar y exportar**. Para obtener más información, consulte [Personalizar la configuración de desarrollo de Visual Studio](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
 El código del visualizador debe colocarse en un archivo DLL que leerá el depurador. El primer paso es crear un proyecto de biblioteca de clases para el archivo DLL.  
  
## <a name="create-and-prepare-a-class-library-project"></a>Crear y preparar un proyecto de biblioteca de clases  
  
#### <a name="to-create-a-class-library-project"></a>Para crear un proyecto de biblioteca de clases  
  
1. En el menú **Archivo**, elija **Nuevo** y haga clic en **Nuevo proyecto**.  
  
2. En el cuadro de diálogo **nuevo proyecto** , en **tipo de proyecto**s, haga clic en **Visual Basic**.  
  
3. En el cuadro **plantillas** , haga clic en **biblioteca de clases**.  
  
4. En el cuadro **Nombre**, escriba un nombre adecuado para la biblioteca de clases como, por ejemplo, **MyFirstVisualizer**.  
  
5. Haga clic en **OK**.  
  
   Cuando haya creado la biblioteca de clases, debe agregar una referencia a Microsoft.VisualStudio.DebuggerVisualizers.DLL, para que pueda utilizar las clases que allí se definen. No obstante, en primer lugar debe asignar un nombre descriptivo al proyecto.  
  
#### <a name="to-rename-class1vb-and-add-microsoftvisualstudiodebuggervisualizers"></a>Para cambiar el nombre de Class1.vb y agregar Microsoft.VisualStudio.DebuggerVisualizers  
  
1. En el **Explorador de soluciones**, haga clic con el botón derecho en **Class1.vb** y, en el menú contextual, haga clic en **Cambiar nombre**.  
  
2. Cambie el nombre Class1.vb por un nombre significativo, como DebuggerSide.vb.  
  
    > [!NOTE]
    > [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] cambia automáticamente la declaración de clase en DebuggerSide.vb para que coincida con el nuevo nombre del archivo.  
  
3. En el **Explorador de soluciones**, haga clic con el botón derecho en **Mi primer visualizador** y, a continuación, haga clic en **Agregar referencia** en el menú contextual.  
  
4. En el cuadro de diálogo **Agregar referencia**, en la ficha **.NET**, haga clic en Microsoft.VisualStudio.DebuggerVisualizers.DLL.  
  
5. Haga clic en **Aceptar**.  
  
6. En DebuggerSide.vb, agregue la instrucción siguiente a las instrucciones `Imports`:  
  
    ```  
    Imports Microsoft.VisualStudio.DebuggerVisualizers  
    ```  
  
## <a name="add-the-debugger-side-code"></a>Agregar el código depurado  
 Ahora, ya está listo para crear el código del depurador. Éste es el código que se ejecuta dentro del depurador para mostrar la información que desea visualizar. En primer lugar hay que cambiar la declaración del objeto `DebuggerSide` para que herede de la clase base `DialogDebuggerVisualizer`.  
  
#### <a name="to-inherit-from-dialogdebuggervisualizer"></a>Para heredar de DialogDebuggerVisualizer  
  
1. En DebuggerSide.vb, vaya a la línea siguiente del código:  
  
   ```  
   Public Class DebuggerSide  
   ```  
  
2. Edite el código de forma que presente el siguiente aspecto:  
  
   ```  
   Public Class DebuggerSide  
   Inherits DialogDebuggerVisualizer  
   ```  
  
   `DialogDebuggerVisualizer` tiene un método abstracto, `Show`, que debe reemplazar.  
  
#### <a name="to-override-the-dialogdebuggervisualizershow-method"></a>Para reemplazar el método DialogDebuggerVisualizer.Show  
  
- En `public class DebuggerSide`, agregue el método siguiente:  
  
  ```  
  Protected Overrides Sub Show(ByVal windowService As Microsoft.VisualStudio.DebuggerVisualizers.IDialogVisualizerService, ByVal objectProvider As Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider)  
  
      End Sub  
  ```  
  
  El método `Show` contiene el código que verdaderamente crea el cuadro de diálogo del visualizador, u otra interfaz de usuario, y muestra la información que se ha pasado del depurador al visualizador. Es necesario agregar el código que crea el cuadro de diálogo y muestra la información. En este tutorial, se realizará este paso mediante un cuadro de mensaje de formularios Windows Forms. En primer lugar debe agregar una referencia y una instrucción `Imports` para <xref:System.Windows.Forms>.  
  
#### <a name="to-add-systemwindowsforms"></a>Para agregar System.Windows.Forms  
  
1. En el **Explorador de soluciones**, haga clic con el botón derecho en **Referencias** y, a continuación, haga clic en **Agregar referencia** en el menú contextual.  
  
2. En el cuadro de diálogo **Agregar referencia**, en la ficha **.NET**, haga clic en **System.Windows.Forms**.  
  
3. Haga clic en **Aceptar**.  
  
4. En DebuggerSide.cs, agregue la instrucción siguiente a las instrucciones `Imports`:  
  
    ```  
    Imports System.Windows.Forms  
    ```  
  
## <a name="create-your-visualizers-user-interface"></a>Crear la interfaz de usuario del visualizador  
 Ahora, agregará código para crear y mostrar la interfaz de usuario para el visualizador. Debido que éste es su primer visualizador, mantendrá la interfaz de usuario sencilla y utilizará un cuadro de mensaje.  
  
#### <a name="to-show-the-visualizer-output-in-a-dialog-box"></a>Para mostrar el resultado del visualizador en un cuadro de diálogo  
  
1. En el método `Show`, agregue la siguiente línea de código:  
  
    ```  
    MessageBox.Show(objectProvider.GetObject().ToString())  
    ```  
  
     En este código de ejemplo no se incluye el control de errores. Debe incluir el control de errores en un visualizador real o en cualquier otro tipo de aplicación.  
  
2. En el menú **Compilar**, haga clic en **Compilar MyFirstVisualizer**. El proyecto debería compilarse correctamente. Corrija cualquier error de compilación antes de continuar.  
  
## <a name="add-the-necessary-attribute"></a>Agregar el atributo necesario  
 Ése es el fin del código del depurador. Sin embargo, hay un paso más que realizar: el atributo que indica al lado depurado qué colección de clases incluye el visualizador.  
  
#### <a name="to-add-the-debugee-side-code"></a>Para agregar el código que está siendo depurado  
  
1. Agregue el código de atributo siguiente a DebuggerSide.vb, después de las instrucciones `Imports`, pero antes de `namespace MyFirstVisualizer`:  
  
    ```  
    <Assembly: System.Diagnostics.DebuggerVisualizer(GetType(MyFirstVisualizer.DebuggerSide), GetType(VisualizerObjectSource), Target:=GetType(System.String), Description:="My First Visualizer")>  
    ```  
  
2. En el menú **Compilar**, haga clic en **Compilar MyFirstVisualizer**. El proyecto debería compilarse correctamente. Corrija cualquier error de compilación antes de continuar.  
  
## <a name="create-a-test-harness"></a>Crear un instrumento de prueba  
 En este momento, el primer visualizador está terminado. Si ha seguido los pasos correctamente, debería poder compilar el visualizador e instalarlo en [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Sin embargo, antes de instalar un visualizador en [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], debería probarlo para asegurarse de que se ejecuta correctamente. A continuación creará un instrumento de prueba para ejecutar el visualizador sin instalarlo en [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
#### <a name="to-add-a-test-method-to-show-the-visualizer"></a>Para agregar un método de prueba para mostrar el visualizador  
  
1. Agregue el método siguiente a la clase `public DebuggerSide`:  
  
   ```  
   Shared Public Sub TestShowVisualizer(ByVal objectToVisualize As Object)  
       Dim visualizerHost As New VisualizerDevelopmentHost(objectToVisualize, GetType(DebuggerSide))  
   visualizerHost.ShowVisualizer()  
   End Sub  
   ```  
  
2. En el menú **Compilar**, haga clic en **Compilar MyFirstVisualizer**. El proyecto debería compilarse correctamente. Corrija cualquier error de compilación antes de continuar.  
  
   Luego, debe crear un proyecto ejecutable para llamar al archivo DLL del visualizador. Para que resulte más sencillo, utilice un proyecto de aplicación de consola.  
  
#### <a name="to-add-a-console-application-project-to-the-solution"></a>Para agregar un proyecto de aplicación de consola a la solución  
  
1. En el menú **Archivo**, haga clic en **Agregar** y, a continuación, en **Nuevo proyecto**.  
  
2. En el cuadro de diálogo **Agregar nuevo proyecto** , en el cuadro **plantillas** , haga clic en **aplicación de consola**.  
  
3. En el cuadro **Nombre**, escriba un nombre significativo para la aplicación de consola, como **MyTestConsole**.  
  
4. Haga clic en **OK**.  
  
   Ahora, debe agregar las referencias necesarias para que MyTestConsole pueda llamar a MyFirstVisualizer.  
  
#### <a name="to-add-necessary-references-to-mytestconsole"></a>Para agregar las referencias necesarias a MyTestConsole  
  
1. En el **Explorador de soluciones**, haga clic con el botón derecho en **MyTestConsole** y, luego, en **Agregar referencia**, en el menú contextual.  
  
2. En el cuadro de diálogo **Agregar referencia**, en la pestaña **.NET**, haga clic en Microsoft.VisualStudio.DebuggerVisualizers.  
  
3. Haga clic en **Aceptar**.  
  
4. Haga clic con el botón derecho en **MyTestConsole** y, a continuación, vuelva a hacer clic en **Agregar referencia**.  
  
5. En el cuadro de diálogo **Agregar referencia**, haga clic en la pestaña **Proyectos** y, a continuación, seleccione MyFirstVisualizer.  
  
6. Haga clic en **Aceptar**.  
  
## <a name="finish-your-test-harness-and-test-your-visualizer"></a>Finalizar el instrumento de prueba y probar el visualizador  
 A continuación, agregará el código para finalizar el instrumento de prueba.  
  
#### <a name="to-add-code-to-mytestconsole"></a>Para agregar el código a MyTestConsole  
  
1. En el **Explorador de soluciones**, haga clic con el botón derecho en **Program.vb** y, en el menú contextual, haga clic en **Cambiar nombre**.  
  
2. Edite el nombre de Module1.vb por uno adecuado, como por ejemplo **TestConsole.vb**.  
  
    Tenga en cuenta que [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] cambia automáticamente la declaración de clase de TestConsole.vb para que coincida con el nuevo nombre de archivo.  
  
3. En TestConsole. vb, agregue la instrucción `Imports` siguiente:  
  
   ```  
   Imports MyFirstVisualizer  
   ```  
  
4. En el método `Main`, agregue el código siguiente:  
  
   ```  
   Dim myString As String = "Hello, World"  
   DebuggerSide.TestShowVisualizer(myString)  
   ```  
  
   Ahora está preparado para probar el primer visualizador.  
  
#### <a name="to-test-the-visualizer"></a>Para probar el visualizador  
  
1. En el **Explorador de soluciones**, haga clic con el botón derecho en **MyTestConsole** y, en el menú contextual, en **Establecer como proyecto de inicio**.  
  
2. En el menú **Depurar**, haga clic en **Iniciar**.  
  
    Se inicia la aplicación de consola. Aparecerá el visualizador y mostrará la cadena "Hello, World".  
  
   Enhorabuena. Acaba de compilar y probar el primer visualizador.  
  
   Si desea utilizar el visualizador en [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], en lugar de simplemente llamarlo desde el instrumento de prueba, tendrá que instalarlo. Para obtener más información, vea [Cómo: instalar un visualizador](../debugger/how-to-install-a-visualizer.md).  
  
## <a name="see-also"></a>Consulte también  
 [Arquitectura del visualizador](../debugger/visualizer-architecture.md)   
 [Cómo: instalar un visualizador](../debugger/how-to-install-a-visualizer.md)   
 [Create Custom Visualizers](../debugger/create-custom-visualizers-of-data.md) (Crear visualizadores personalizados)
