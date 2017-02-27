---
title: "Ampliaci&#243;n de la barra de estado | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "barras de estado, barras de estado"
  - "barras de estado, información general"
ms.assetid: f955115c-4c5f-45ec-b41b-365868c5ec0c
caps.latest.revision: 23
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 23
---
# Ampliaci&#243;n de la barra de estado
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Puede utilizar la barra de estado de Visual Studio en la parte inferior del IDE para mostrar información.  
  
 Al extender la barra de estado, puede mostrar información y la interfaz de usuario en cuatro áreas: el área de comentarios, la barra de progreso, la región de la animación y la región del diseñador. El área de comentarios permite mostrar texto y resalte el texto mostrado. La barra de progreso muestra el progreso incremental para las operaciones de ejecución corta como guardar un archivo. La región de la animación muestra una animación con bucle continuamente para operaciones de ejecución prolongada o funcionamiento de longitud indeterminada, como compilar varios proyectos en una solución. Y la región del diseñador muestra el número de línea y columna de la ubicación del cursor.  
  
 Puede obtener la barra de estado mediante la <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbar> interfaz \(desde el <xref:Microsoft.VisualStudio.Shell.Interop.SVsStatusbar> service\). Además, puede registrar cualquier objeto que se encuentra en un marco de ventana como un objeto de cliente de la barra de estado mediante la implementación de la <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser> interfaz. Cada vez que una ventana se activa, Visual Studio consulta el objeto situado en esa ventana para el `IVsStatusbarUser` interfaz. Si se encuentra, invoca el <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser.SetInfo%2A> método en la interfaz devuelta y el objeto puede actualizar la barra de estado de ese método. Documento de windows, por ejemplo, puede utilizar el <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser.SetInfo%2A> método para actualizar la información en la región del diseñador cuando se activan.  
  
 Los siguientes procedimientos se suponen que sabe cómo crear un proyecto de VSIX y agregar un comando de menú personalizado. Para obtener más información, vea [Crear una extensión con un comando de menú](../extensibility/creating-an-extension-with-a-menu-command.md).  
  
## Modificación de la barra de estado  
 Este procedimiento muestra cómo establecer y obtener texto, mostrar texto estático y resalte el texto mostrado en el área de comentarios de la barra de estado.  
  
#### Leer y escribir en la barra de estado  
  
1.  Cree un proyecto VSIX denominado **TestStatusBarExtension** y agregue un comando de menú llamado **TestStatusBarCommand**.  
  
2.  En TestStatusBarCommand.cs, reemplace el código de método de controlador de comandos \(MenuItemCallback\) por lo siguiente:  
  
    ```c#  
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
  
3.  Compile el código e iniciar la depuración.  
  
4.  Abra la **herramientas** menú en la instancia experimental de Visual Studio. Haga clic en el **TestStatusBarCommand invocar** botón.  
  
     Debería ver que el texto de la barra ahora lecturas de estado **"Que acabamos de escribir en la barra de estado"** y el cuadro de mensaje que aparece tiene el mismo texto.  
  
#### Actualización de la barra de progreso  
  
1.  En este procedimiento, se mostrará cómo inicializar y actualizar la barra de progreso.  
  
2.  Abra el archivo TestStatusBarCommand.cs y reemplace el método MenuItemCallback con el código siguiente:  
  
    ```c#  
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
  
3.  Compile el código e iniciar la depuración.  
  
4.  Abra la **herramientas** menú en la instancia experimental de Visual Studio. Haga clic en **TestStatusBarCommand invocar** botón.  
  
     Debería ver que el texto de la barra ahora lecturas de estado **"Escribir en la barra de progreso"** También verá la barra de progreso se actualiza cada segundo durante 20 segundos. Después de que se borran la barra de estado y la barra de progreso.  
  
#### Mostrar una animación  
  
1.  La barra de estado muestra una animación de bucle indica una operación de larga duración \(por ejemplo, al compilar varios proyectos en una solución\). Si no ve esta animación, asegúrese de que tiene el formato correcto **Herramientas \/ opciones** configuración:  
  
     Vaya a la **Herramientas\/Opciones \/ General** ficha y desactive **Ajustar automáticamente la experiencia visual según el rendimiento del cliente**. A continuación, active la opción subdirectorio **Habilitar experiencia visual de cliente enriquecido**. Ahora podrá ver la animación cuando se compila el proyecto en la instancia experimental de Visual Studio.  
  
     En este procedimiento se muestra la animación de Visual Studio estándar que representa la creación de un proyecto o solución.  
  
2.  Abra el archivo TestStatusBarCommand.cs y reemplace el método MenuItemCallback con el código siguiente:  
  
    ```c#  
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
  
3.  Compile el código e iniciar la depuración.  
  
4.  Abra la **herramientas** menú en la instancia experimental de Visual Studio y haga clic en **invocar TestStatusBarCommand**.  
  
     Cuando aparezca el cuadro de mensaje, también verá la animación en la barra de estado en el extremo derecho. Al descartar el cuadro de mensaje, desaparece la animación.