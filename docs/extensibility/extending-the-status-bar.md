---
title: Extender la barra de estado | Microsoft Docs
description: Obtenga información sobre cómo extender la barra de estado de Visual Studio en la parte inferior del IDE, que muestra información.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- status bars, about status bars
- status bars, overview
ms.assetid: f955115c-4c5f-45ec-b41b-365868c5ec0c
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 7776c7fa35cd7ac06dec60ced3604cb67c96da4a
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99903200"
---
# <a name="extend-the-status-bar"></a>Extender la barra de estado
Puede usar la barra de estado de Visual Studio en la parte inferior del IDE para mostrar información.

 Al extender la barra de estado, puede mostrar información e interfaz de usuario en cuatro regiones: la región de comentarios, la barra de progreso, la región de animación y la región del diseñador. La región de comentarios le permite mostrar texto y resaltar el texto mostrado. La barra de progreso muestra el progreso incremental de las operaciones de ejecución breve, como guardar un archivo. La región de animación muestra una animación con bucle continuo para operaciones de ejecución prolongada u operación de longitud indeterminada, como la compilación de varios proyectos en una solución. Y la región del diseñador muestra el número de línea y columna de la ubicación del cursor.

 Puede obtener la barra de estado mediante la <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbar> interfaz (desde el <xref:Microsoft.VisualStudio.Shell.Interop.SVsStatusbar> servicio). Además, todos los objetos que se colocan en un marco de ventana pueden registrarse como un objeto de cliente de la barra de estado implementando la <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser> interfaz. Cada vez que se activa una ventana, Visual Studio consulta el objeto que se encuentra en esa ventana para la `IVsStatusbarUser` interfaz. Si se encuentra, llama al <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser.SetInfo%2A> método en la interfaz devuelta y el objeto puede actualizar la barra de estado desde dentro de ese método. Las ventanas de documento, por ejemplo, pueden utilizar el <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser.SetInfo%2A> método para actualizar la información en la región del diseñador cuando se activan.

 En los procedimientos siguientes se supone que entiende cómo crear un proyecto VSIX y cómo agregar un comando de menú personalizado. Para obtener información, consulte [crear una extensión con un comando de menú](../extensibility/creating-an-extension-with-a-menu-command.md).

## <a name="modify-the-status-bar"></a>Modificar la barra de estado
 En este procedimiento se muestra cómo establecer y obtener texto, mostrar texto estático y resaltar el texto mostrado en la región de comentarios de la barra de estado.

### <a name="read-and-write-to-the-status-bar"></a>Leer y escribir en la barra de estado

1. Cree un proyecto VSIX denominado **TestStatusBarExtension** y agregue un comando de menú denominado **TestStatusBarCommand**.

2. En *TestStatusBarCommand.CS*, reemplace el código del método de controlador de comandos ( `MenuItemCallback` ) por lo siguiente:

    ```csharp
    private void MenuItemCallback(object sender, EventArgs e)
    {
        IVsStatusbar statusBar = (IVsStatusbar)ServiceProvider.GetService(typeof(SVsStatusbar));

        // Make sure the status bar is not frozen
        int frozen;

        statusBar.IsFrozen(out frozen);

        if (frozen != 0)
        {
            statusBar.FreezeOutput(0);
        }

        // Set the status bar text and make its display static.
        statusBar.SetText("We just wrote to the status bar.");

        // Freeze the status bar.
        statusBar.FreezeOutput(1);

        // Get the status bar text.
        string text;
        statusBar.GetText(out text);
        System.Windows.Forms.MessageBox.Show(text);

        // Clear the status bar text.
        statusBar.FreezeOutput(0);
        statusBar.Clear();
    }
    ```

3. Compile el código e inicie la depuración.

4. Abra el menú **herramientas** en la instancia experimental de Visual Studio. Haga clic en el botón **invocar TestStatusBarCommand** .

     Debería ver que el texto de la barra de estado ahora lee que **acabamos de escribir en la barra de estado.** y el cuadro de mensaje que aparece tiene el mismo texto.

### <a name="update-the-progress-bar"></a>Actualizar la barra de progreso

1. En este procedimiento se muestra cómo inicializar y actualizar la barra de progreso.

2. Abra el archivo *TestStatusBarCommand.CS* y reemplace el `MenuItemCallback` método por el código siguiente:

    ```csharp
    private void MenuItemCallback(object sender, EventArgs e)
    {
        IVsStatusbar statusBar = (IVsStatusbar)ServiceProvider.GetService(typeof(SVsStatusbar));
        uint cookie = 0;
        string label = "Writing to the progress bar";

        // Initialize the progress bar.
        statusBar.Progress(ref cookie, 1, "", 0, 0);

        for (uint i = 0, total = 20; i <= total; i++)
        {
            // Display progress every second.
            statusBar.Progress(ref cookie, 1, label, i, total);
            System.Threading.Thread.Sleep(1000);
        }

        // Clear the progress bar.
        statusBar.Progress(ref cookie, 0, "", 0, 0);
    }
    ```

3. Compile el código e inicie la depuración.

4. Abra el menú **herramientas** en la instancia experimental de Visual Studio. Haga clic en el botón **invocar TestStatusBarCommand** .

     Debería ver que el texto de la barra de estado ahora lee **la escritura en la barra de progreso.** También debería ver que la barra de progreso se actualiza cada segundo durante 20 segundos. Después, se desactivan la barra de estado y la barra de progreso.

### <a name="display-an-animation"></a>Mostrar una animación

1. La barra de estado muestra una animación en bucle que indica una operación de ejecución prolongada (por ejemplo, compilar varios proyectos en una solución). Si no ve esta animación, asegúrese de que tiene la configuración de opciones de **herramientas** correcta  >   :

     Vaya a la pestaña Opciones de **herramientas**  >    >  **General** y desactive **ajustar automáticamente la experiencia visual según el rendimiento del cliente**. A continuación, active la subopción **Habilitar experiencia visual de cliente enriquecida**. Ahora debería poder ver la animación al compilar el proyecto en la instancia experimental de Visual Studio.

     En este procedimiento se muestra la animación de Visual Studio estándar que representa la creación de un proyecto o una solución.

2. Abra el archivo *TestStatusBarCommand.CS* y reemplace el `MenuItemCallback` método por el código siguiente:

    ```csharp
    private void MenuItemCallback(object sender, EventArgs e)
    {
        IVsStatusbar statusBar =(IVsStatusbar)ServiceProvider.GetService(typeof(SVsStatusbar));

        // Use the standard Visual Studio icon for building.
        object icon = (short)Microsoft.VisualStudio.Shell.Interop.Constants.SBAI_Build;

        // Display the icon in the Animation region.
        statusBar.Animation(1, ref icon);

        // The message box pauses execution for you to look at the animation.
        System.Windows.Forms.MessageBox.Show("showing?");

        // Stop the animation.
        statusBar.Animation(0, ref icon);
    }
    ```

3. Compile el código e inicie la depuración.

4. Abra el menú **herramientas** en la instancia experimental de Visual Studio y haga clic en **invocar TestStatusBarCommand**.

     Cuando vea el cuadro de mensaje, también debería ver la animación en la barra de estado en el extremo derecho. Al descartar el cuadro de mensaje, la animación desaparece.
