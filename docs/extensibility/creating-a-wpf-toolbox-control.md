---
title: "Crear un Control de cuadro de herramientas WPF | Microsoft Docs"
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
  - "control de cuadro de herramientas"
  - "toolbox"
  - "wpf"
ms.assetid: 9cc34db9-b0d1-4951-a02f-7537fbbb51ad
caps.latest.revision: 16
caps.handback.revision: 16
ms.author: "gregvanl"
manager: "ghogen"
---
# Crear un Control de cuadro de herramientas WPF
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

La plantilla de Control de cuadro de herramientas WPF \(Windows Presentation Framework\) le permite crear controles WPF que se agregan automáticamente a la **herramientas** cuando se instala la extensión. En este tema se muestra cómo usar la plantilla para crear un **herramientas** control que se puede distribuir a otros usuarios.  
  
 A partir de Visual Studio 2015, no instale el SDK de Visual Studio desde el centro de descarga. Se incluye como una característica opcional de la instalación de Visual Studio. También puede instalar el SDK de VS más adelante. Para obtener más información, consulta [Instalar el SDK de Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).  
  
## Crear un Control de cuadro de herramientas WPF  
  
#### Crear una extensión con un Control de cuadro de herramientas WPF  
  
1.  Cree un proyecto VSIX denominado `MyToolboxControl`. Puede encontrar la plantilla de proyecto VSIX en la **nuevo proyecto** en el cuadro de diálogo **Visual C\# \/ extensibilidad**.  
  
2.  Cuando se abre el proyecto, agregue un **Control de cuadro de herramientas de WPF** plantilla de elemento denominada `MyToolboxControl`. En el **el Explorador de soluciones**, haga clic en el nodo del proyecto y seleccione **Agregar \/ nuevo elemento**. En el **Agregar nuevo elemento** cuadro de diálogo, vaya a **Visual C\# \/ extensibilidad** y seleccione **Control de cuadro de herramientas de WPF**. En el **nombre** campo en la parte inferior de la ventana, cambie el nombre de archivo de comandos para `MyToolboxControl.cs`.  
  
     La solución contiene ahora un control de usuario, un `ProvideToolboxControlAttribute`<xref:Microsoft.VisualStudio.Shell.RegistrationAttribute> que agrega el control a la **herramientas**, y un **Microsoft.VisualStudio.ToolboxControl** entrada de recurso en el manifiesto de VSIX para la implementación.  
  
#### Para crear la interfaz de usuario del control  
  
1.  Abra MyToolboxControl.xaml en el diseñador.  
  
     El diseñador muestra un control <xref:System.Windows.Controls.Grid> que contiene un control <xref:System.Windows.Controls.Button>.  
  
2.  Organizar el diseño de cuadrícula. Cuando se selecciona el <xref:System.Windows.Controls.Grid> controlar, aparecen barras de control en azul en los bordes superiores e izquierdos de la cuadrícula. Puede agregar filas y columnas a la cuadrícula haciendo clic en las barras.  
  
3.  Agregar controles secundarios a la cuadrícula. Puede colocar un control secundario arrastrándolo desde el **herramientas** a una sección de la cuadrícula, o estableciendo su `Grid.Row` y `Grid.Column` atributos en XAML. El ejemplo siguiente agrega dos etiquetas en la fila superior de la cuadrícula y un botón en la segunda fila.  
  
    ```xaml  
    <Grid>  
        <Label Grid.Row="0" Grid.Column="0" Name="label1" />  
        <Label Grid.Row="0" Grid.Column="1" Name="label2" />  
        <Button Name="button1" Click="button1_Click" Grid.Row="1" Grid.ColumnSpan="2" />  
    </Grid>  
    ```  
  
## Cambiar el nombre del control  
 De forma predeterminada, el control aparecerá en el **herramientas** como **MyToolboxControl** en un grupo denominado **MyToolboxControl.MyToolboxControl**. Puede cambiar estos nombres en el archivo MyToolboxControl.xaml.cs.  
  
1.  Abra MyToolboxControl.xaml.cs en la vista código.  
  
2.  Busque la clase MyToolboxControl y cambie su nombre a TestControl. \(La forma más rápida de hacerlo es cambiar el nombre de la clase, a continuación, seleccione **cambiar el nombre de** en el menú contextual y complete los pasos. \(Para obtener más información acerca de la **cambiar el nombre de** de comandos, consulte [Cambiar el nombre de refactorización \(C\#\)](../csharp-ide/rename-refactoring-csharp.md).\)  
  
3.  Vaya a la `ProvideToolboxControl` de atributo y cambie el valor del primer parámetro para **prueba**. Este es el nombre del grupo que contiene el control en el **herramientas**.  
  
     El código resultante debe tener este aspecto:  
  
    ```c#  
    [ProvideToolboxControl("Test", true)]  
    public partial class TestControl : UserControl  
    {  
        public TestControl()  
        {  
            InitializeComponent();  
        }  
    }  
    ```  
  
## Compilación, prueba e implementación  
 Cuando se depura el proyecto, encontrará el control instalado en el **herramientas** de la instancia experimental de Visual Studio.  
  
#### Para compilar y probar el control  
  
1.  Vuelva a generar el proyecto e iniciar la depuración.  
  
2.  En la nueva instancia de Visual Studio, cree un proyecto de aplicación WPF. Asegúrese de que el Diseñador de XAML está abierto.  
  
3.  Busque el control en el **Cuadro de herramientas** y arrástrelo a la superficie de diseño.  
  
4.  Inicie la depuración de la aplicación de WPF.  
  
5.  Compruebe que aparece el control.  
  
#### Para implementar el control  
  
1.  Después de compilar el proyecto probado, puede encontrar el archivo .vsix en la carpeta \\bin\\debug\\ del proyecto.  
  
2.  Puede instalarlo en un equipo local, haga doble clic en el archivo .vsix y siguiendo el procedimiento de instalación. Para desinstalar el control, vaya a **Herramientas \/ extensiones y actualizaciones** y busque la extensión de control, a continuación, haga clic en **desinstalar**.  
  
3.  Cargue el archivo .vsix en una red o en un sitio web.  
  
     Si va a cargar el archivo a la [Galería de Visual Studio](http://go.microsoft.com/fwlink/?LinkID=123847) sitio Web, pueden usar otros usuarios **Herramientas \/ extensiones y actualizaciones** en Visual Studio para buscar el control en línea e instalarlo.