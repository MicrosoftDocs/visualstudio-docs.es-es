---
title: Extender la barra de estado | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- status bars, about status bars
- status bars, overview
ms.assetid: f955115c-4c5f-45ec-b41b-365868c5ec0c
caps.latest.revision: "23"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: e170edf941455dd21727628c2e07a836db919d0e
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="extending-the-status-bar"></a>Extender la barra de estado
Puede usar la barra de estado de Visual Studio en la parte inferior del IDE para mostrar información.  
  
 Cuando se amplía la barra de estado, puede mostrar información y la interfaz de usuario en cuatro regiones: la región de comentarios, la barra de progreso, la región de animación y la región del diseñador. La región de comentarios permite mostrar texto y resalte el texto mostrado. La barra de progreso muestra el progreso incremental para las operaciones de corta duración como guardar un archivo. La región de animación muestra una animación con bucle continuamente para operaciones de ejecución prolongada o funcionamiento de longitud indeterminado, como compilar varios proyectos en una solución. Y la región del diseñador muestra el número de línea y columna de la ubicación del cursor.  
  
 Puede obtener la barra de estado mediante la <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbar> interfaz (desde el <xref:Microsoft.VisualStudio.Shell.Interop.SVsStatusbar> servicio). Además, puede registrar cualquier objeto que se encuentra en un marco de ventana como un objeto de cliente de la barra de estado mediante la implementación de la <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser> interfaz. Cada vez que una ventana se activa, Visual Studio consulta el objeto que se sitúa en esa ventana para el `IVsStatusbarUser` interfaz. Si se encuentra, llama a la <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser.SetInfo%2A> método en la interfaz devuelta y el objeto puede actualizar la barra de estado de ese método. Documento como las ventanas, por ejemplo, puede utilizar el <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser.SetInfo%2A> método para actualizar información en la región del diseñador cuando están activas.  
  
 Los procedimientos siguientes suponen que sabe cómo crear un proyecto VSIX y agregar un comando de menú personalizado. Para obtener información, consulte [crear una extensión con un comando de menú](../extensibility/creating-an-extension-with-a-menu-command.md).  
  
## <a name="modifying-the-status-bar"></a>Modificación de la barra de estado  
 Este procedimiento muestra cómo establecer y obtener el texto, mostrar texto estático y resalte el texto mostrado en la región de comentarios de la barra de estado.  
  
#### <a name="reading-and-writing-to-the-status-bar"></a>Leer y escribir en la barra de estado  
  
1.  Crear un proyecto VSIX denominado **TestStatusBarExtension** y agregue un comando de menú llamado **TestStatusBarCommand**.  
  
2.  En TestStatusBarCommand.cs, reemplace el código de método de controlador de comandos (MenuItemCallback) por lo siguiente:  
  
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
  
3.  Compilar el código e iniciar la depuración.  
  
4.  Abra la **herramientas** menú en la instancia experimental de Visual Studio. Haga clic en el **TestStatusBarCommand invocar** botón.  
  
     Debería ver que el texto en el estado de la barra ahora lecturas **"Se acaba de escribir en la barra de estado."** y el cuadro de mensaje que aparece tiene el mismo texto.  
  
#### <a name="updating-the-progress-bar"></a>Actualización de la barra de progreso  
  
1.  En este procedimiento le mostraremos cómo inicializar y actualizar la barra de progreso.  
  
2.  Abra el archivo TestStatusBarCommand.cs y reemplace el método MenuItemCallback con el código siguiente:  
  
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
  
3.  Compilar el código e iniciar la depuración.  
  
4.  Abra la **herramientas** menú en la instancia experimental de Visual Studio. Haga clic en **TestStatusBarCommand invocar** botón.  
  
     Debería ver que el texto en el estado de la barra ahora lecturas **"Escribir en la barra de progreso".** También debe ver la barra de progreso se actualiza cada segundo durante 20 segundos. Después de que se borran la barra de estado y la barra de progreso.  
  
#### <a name="displaying-an-animation"></a>Mostrar una animación  
  
1.  La barra de estado muestra una animación de bucle indica una operación de larga duración (por ejemplo, compilar varios proyectos en una solución). Si no ve esta animación, asegúrese de que tiene el formato correcto **herramientas / opciones** configuración:  
  
     Vaya a la **herramientas/opciones / General** pestaña y desactive la opción **ajustar automáticamente la experiencia visual según rendimiento del cliente**. A continuación, active la opción subcarpetas **habilitar experiencia visual de cliente enriquecido**. Ahora debería ver la animación cuando se compila el proyecto en la instancia experimental de Visual Studio.  
  
     En este procedimiento se muestra la animación de Visual Studio estándar que representa la creación de un proyecto o solución.  
  
2.  Abra el archivo TestStatusBarCommand.cs y reemplace el método MenuItemCallback con el código siguiente:  
  
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
  
3.  Compilar el código e iniciar la depuración.  
  
4.  Abra la **herramientas** menú en la instancia experimental de Visual Studio y haga clic en **TestStatusBarCommand invocar**.  
  
     Cuando aparezca el cuadro de mensaje, también verá la animación en la barra de estado en el extremo derecho. Al descartar el cuadro de mensaje, desaparece la animación.