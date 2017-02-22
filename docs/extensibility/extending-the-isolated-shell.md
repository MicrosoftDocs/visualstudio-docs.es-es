---
title: "Extender el Shell aislado | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Shell de Visual Studio, modo aislado"
ms.assetid: 9a641d8f-211e-4486-a1b1-4a89fafe7ee8
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# Extender el Shell aislado
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Puede extender el shell aislado de Visual Studio mediante la adición de un paquete VSPackage, un componente de Managed Extensibility Framework \(MEF\) o un proyecto VSIX genérico para la aplicación de shell aislado.  
  
> [!NOTE]
>  Los siguientes pasos implican que ha creado una aplicación de shell aislado básico mediante la plantilla de proyecto de Visual Studio Shell aislado. Para obtener más información acerca de esta plantilla de proyecto, vea [Tutorial: Crear una aplicación básica de Shell aislado](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md).  
  
## Ubicaciones de la plantilla de proyecto de paquete de Visual Studio  
 La plantilla de proyecto de paquete de Visual Studio puede encontrarse en tres ubicaciones diferentes en el cuadro de diálogo **Nuevo proyecto**:  
  
1.  Bajo **Visual Basic**, **extensibilidad**. El lenguaje predeterminado del proyecto es Visual Basic.  
  
2.  Bajo **Visual C\#**, **extensibilidad**. El lenguaje predeterminado del proyecto es C\#.  
  
3.  Bajo **otros tipos de proyecto**, **extensibilidad**. El lenguaje predeterminado del proyecto es C\+\+.  
  
## Agregar un paquete VSPackage  
 Puede agregar un paquete VSPackage a la aplicación de shell aislado. Los siguientes pasos muestran cómo crear uno que agrega comandos de menú.  
  
#### Para agregar un nuevo paquete de VSPackage  
  
1.  Agregue un proyecto de Visual Studio Package denominado `MenuCommandsPackage`.  
  
2.  En el **información básica de VSPackage** página del asistente, establezca **nombre de la empresa** a `Fabrikam` y **nombre de VSPackage** a `FabrikamMenuCommands`. Elija el botón **Siguiente**.  
  
3.  En la siguiente página, seleccione **comando de menú** y, a continuación, elija **siguiente**.  
  
4.  En la página siguiente, establezca **nombre de comando** a `Fabrikam Command` y **identificador de comando** a `cmdidFabrikamCommand`, y, a continuación, elija **siguiente**.  
  
5.  En el **Seleccionar opciones de proyecto de prueba** página, desactive las opciones de prueba y, a continuación, elija la **Finalizar** botón.  
  
6.  En el proyecto ShellExtensionsVSIX, abra el archivo source.extension.vsixmanifest.  
  
     El **activos** sección debe contener una entrada para el proyecto VSShellStub.AboutBoxPackage.  
  
7.  Elija el botón **Nuevo**.  
  
8.  En el **Agregar nuevo activo** ventana, en la **tipo** lista, seleccione **Microsoft.VisualStudio.VsPackage**.  
  
9. En el **origen** lista, asegúrese de que **un proyecto en la solución actual** está seleccionada. En el **proyecto** cuadro de lista, seleccione **MenuCommandsPackage**.  
  
10. Guarde y cierre el archivo.  
  
11. Recompile la solución e iniciar la depuración del shell aislado.  
  
12. En la barra de menús, elija **herramientas** menú, **comando Fabrikam**.  
  
     Debe aparecer un cuadro de mensaje.  
  
13. Detenga la depuración de la aplicación.  
  
## Agregar un componente MEF  
 Los pasos siguientes muestran cómo agregar un componente MEF en la aplicación de shell aislado.  
  
#### Para agregar un componente MEF  
  
1.  En el **Agregar nuevo proyecto** cuadro de diálogo **Visual C\#**, **extensibilidad**, utilice el **margen del Editor** plantilla para agregar un proyecto. Denomínelo `ShellEditorMargin`.  
  
2.  En el proyecto ShellExtensionsVSIX, abra el archivo Source.extension.vsixmanifest en la vista Diseño, no en la vista de código.  
  
3.  En la `Asset` sección, elija **Agregar contenido**.  
  
4.  En el **Agregar nuevo activo** ventana, en la **tipo** lista, seleccione **Microsoft.VisualStudio.MefComponent**.  
  
5.  En el **origen** lista, asegúrese de que **un proyecto en la solución actual** está seleccionada. En el **proyecto** cuadro de lista, seleccione **ShellEditorMargin**.  
  
6.  Guarde y cierre el archivo.  
  
7.  Recompile la solución e iniciar la depuración del shell aislado.  
  
8.  Abra un archivo de texto.  
  
     Un margen de color verde que contiene las palabras "Hello world\!" debe mostrarse en la parte inferior de la ventana de archivo de texto.  
  
9. Detenga la depuración de la aplicación.  
  
## Agregar un proyecto VSIX genérico  
  
#### Para agregar un proyecto VSIX genérico  
  
1.  En el **Agregar nuevo proyecto** cuadro de diálogo **Visual C\#**, **extensibilidad**, utilice el **VSIXProject** plantilla para agregar un proyecto. Denomínelo `EmptyVSIX`.  
  
2.  En el proyecto ShellExtensionsVSIX, abra el archivo Source.extensions.vsixmanifest en la vista Diseño, no en la vista de código.  
  
3.  En la `Assets` sección, elija **nuevo**.  
  
4.  En el **Agregar nuevo activo** ventana, en la **tipo** seleccione el tipo de contenido que desea agregar.  
  
5.  En **origen**, asegúrese de que el **un proyecto de la solución actual** está seleccionada. En el cuadro de lista, seleccione el nombre del proyecto VSIX.  
  
6.  Guarde y cierre el archivo.  
  
7.  Si este proyecto incluye código compilado, debe editar el proyecto para que el ensamblado se incluye en la salida.  
  
    1.  Descargar el proyecto VSIX y abra el archivo de proyecto.  
  
    2.  En la primera `<PropertyGroup>` Bloquear, cambie el valor de `<CopyBuildOutputToOutputDirectory>` a `true`.  
  
    3.  Guardar y recargar el proyecto.  
  
8.  Compile y ejecute la solución.  
  
## Vea también  
 [Tutorial: Crear una aplicación básica de Shell aislado](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md)