---
title: "Ampliaci&#243;n de la ventana de salida | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Ventana de resultados, acerca de la ventana de salida"
ms.assetid: b02fa88c-f92a-4ff6-ba5f-2eb4d48a643a
caps.latest.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 13
---
# Ampliaci&#243;n de la ventana de salida
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

El **salida** ventana es un conjunto de paneles de texto de lectura y escritura. Visual Studio tiene estos paneles integrados: **Generar**, en los proyectos que se comunican mensajes sobre las compilaciones, y **General**, en el que [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] comunica mensajes sobre el IDE. Proyectos de obtención una referencia a la **Generar** automáticamente a través del panel el <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildableProjectCfg> métodos de interfaz y Visual Studio ofrece acceso directo a la **General** panel a través de la <xref:Microsoft.VisualStudio.Shell.Interop.SVsGeneralOutputWindowPane> servicio. Además de los paneles integrados, puede crear y administrar sus propios paneles personalizados.  
  
 Puede controlar la **salida** ventana directamente desde el <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindow> y <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindowPane> interfaces. El <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindow> interfaz, que ofrece el <xref:Microsoft.VisualStudio.Shell.Interop.SVsOutputWindow> del servicio, define métodos para crear, recuperar y destruir **salida** paneles de la ventana. El <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindow> interfaz define métodos para mostrar paneles, ocultar paneles y manipular el texto. Una manera alternativa de controlar la **salida** ventana es a través de la <xref:EnvDTE.OutputWindow> y <xref:EnvDTE.OutputWindowPane> objetos en el modelo de objetos de automatización de Visual Studio. Estos objetos encapsulan casi toda la funcionalidad de la <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindow> y <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindowPane> interfaces. Además, la <xref:EnvDTE.OutputWindow> y <xref:EnvDTE.OutputWindowPane> objetos agregan algunas funciones de nivel superior para que resulten más fáciles de enumerar el **salida** paneles de la ventana y recuperar el texto de los paneles.  
  
## Crear una extensión que utiliza el panel de resultados  
 Puede realizar una extensión que ejerce distintos aspectos del panel de resultados.  
  
1.  Cree un proyecto VSIX denominado `TestOutput` con un comando de menú denominado **TestOutput**. Para obtener más información, consulta [Crear una extensión con un comando de menú](../extensibility/creating-an-extension-with-a-menu-command.md).  
  
2.  Agregue las siguientes referencias:  
  
    1.  EnvDTE  
  
    2.  EnvDTE80  
  
3.  En TestOutput.cs, agregue la siguiente instrucción using:  
  
    ```f#  
    using EnvDTE; using EnvDTE80;  
    ```  
  
4.  En TestOutput.cs, elimine el método ShowMessageBox. Agregue el siguiente código auxiliar del método:  
  
    ```c#  
    private void OutputCommandHandler(object sender, EventArgs e) { }  
    ```  
  
5.  En el constructor TestOutput, cambie el controlador de comandos para OutputCommandHandler. Aquí está lo que agrega los comandos:  
  
    ```c#  
    OleMenuCommandService commandService = this.ServiceProvider.GetService(typeof(IMenuCommandService)) as OleMenuCommandService; if (commandService != null) { CommandID menuCommandID = new CommandID(MenuGroup, CommandId); EventHandler eventHandler = OutputCommandHandler; MenuCommand menuItem = new MenuCommand(eventHandler, menuCommandID); commandService.AddCommand(menuItem); }  
    ```  
  
6.  Las secciones siguientes tienen métodos diferentes que muestran distintas formas de trabajar con el panel de resultados. Puede llamar a estos métodos al cuerpo del método OutputCommandHandler\(\). Por ejemplo, el código siguiente agrega el método CreatePane\(\) en la sección siguiente.  
  
    ```c#  
    private void OutputCommandHandler(object sender, EventArgs e) { CreatePane(new Guid(), "Created Pane", true, false); }  
    ```  
  
## Creación de una ventana de salida con IVsOutputWindow  
 Este ejemplo muestra cómo crear un nuevo **salida** panel mediante el uso de la <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindow> interfaz.  
  
```c#  
void CreatePane(Guid paneGuid, string title, bool visible, bool clearWithSolution) { IVsOutputWindow output = (IVsOutputWindow)GetService(typeof(SVsOutputWindow)); IVsOutputWindowPane pane; // Create a new pane. output.CreatePane( ref paneGuid, title, Convert.ToInt32(visible), Convert.ToInt32(clearWithSolution)); // Retrieve the new pane. output.GetPane(ref paneGuid, out pane); pane.OutputString("This is the Created Pane \n"); }  
```  
  
 Si agrega este método para la extensión dada en la sección anterior, al hacer clic en el **invocar TestOutput** comando debería ver el **salida** ventana con un encabezado que dice **Mostrar resultados desde: CreatedPane** y las palabras **este es el panel crear** en el propio panel.  
  
## Creación de una ventana de salida con OutputWindow  
 Este ejemplo muestra cómo crear un **salida** panel utilizando la <xref:EnvDTE.OutputWindow> objeto.  
  
```c#  
void CreatePane(string title) { DTE2 dte = (DTE2)GetService(typeof(DTE)); OutputWindowPanes panes = dte.ToolWindows.OutputWindow.OutputWindowPanes; try { // If the pane exists already, write to it. panes.Item(title); } catch (ArgumentException) { // Create a new pane and write to it. return panes.Add(title); } }  
```  
  
 Aunque el <xref:EnvDTE.OutputWindowPanes> colección le permite recuperar un **salida** panel de ventana por su título, los títulos de panel no se garantiza que es único. Si tiene dudas acerca de la unicidad de un título, utilice la <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindow.GetPane%2A> método para recuperar el panel correcto por su GUID.  
  
 Si agrega este método para la extensión dada en la sección anterior, al hacer clic en el **TestOutput invocar** debería ver la ventana de salida con un encabezado que indica que el comando **Mostrar resultados desde: DTEPane** y las palabras **agregado DTE panel** en el propio panel.  
  
## Eliminación de una ventana de salida  
 Este ejemplo muestra cómo eliminar una **salida** panel de ventana.  
  
```c#  
void DeletePane(Guid paneGuid) { IVsOutputWindow output = (IVsOutputWindow)ServiceProvider.GetService(typeof(SVsOutputWindow)); IVsOutputWindowPane pane; output.GetPane(ref paneGuid, out pane); if (pane == null) { CreatePane(paneGuid, "New Pane\n", true, true); } else { output.DeletePane(ref paneGuid); } }  
```  
  
 Si agrega este método para la extensión dada en la sección anterior, al hacer clic en el **TestOutput invocar** debería ver la ventana de salida con un encabezado que indica que el comando **Mostrar resultados desde: nuevo panel** y las palabras **agregado panel creado** en el propio panel. Si hace clic en el **TestOutput invocar** comando nuevo, se elimina el panel.  
  
## Obtener el panel General de la ventana de salida  
 Este ejemplo muestra cómo obtener integrado **General** panel de la **salida** ventana.  
  
```c#  
void GetGeneralPane() { return (IVsOutputWindowPane)GetService( typeof(SVsGeneralOutputWindowPane)); }  
```  
  
 Si agrega este método para la extensión dada en la sección anterior, al hacer clic en el **TestOutput invocar** comando, verá que el **salida** ventana muestra las palabras **panel encuentra General** en el panel.  
  
## Obtener el panel de compilación de la ventana de salida  
 Este ejemplo muestra cómo encontrar el panel de compilación y escribir en él. Puesto que el panel de compilación no está activado de forma predeterminada, se activa también.  
  
```c#  
void OutputTaskItemStringExExample(string buildMessage) { EnvDTE80.DTE2 dte = (EnvDTE80.DTE2)ServiceProvider.GetService(typeof(EnvDTE.DTE)); EnvDTE.OutputWindowPanes panes = dte.ToolWindows.OutputWindow.OutputWindowPanes; foreach (EnvDTE.OutputWindowPane pane in panes) { if (pane.Name.Contains("Build")) { pane.OutputString(buildMessage + "\n"); pane.Activate(); return; } } }  
```