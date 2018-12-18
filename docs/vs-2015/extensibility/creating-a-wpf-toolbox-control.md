---
title: Crear un Control de cuadro de herramientas WPF | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- toolbox control
- toolbox
- wpf
ms.assetid: 9cc34db9-b0d1-4951-a02f-7537fbbb51ad
caps.latest.revision: 17
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 2ad3edfa84ee64425a7a9fbc6b0dfc5098396907
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/16/2018
ms.locfileid: "51786033"
---
# <a name="creating-a-wpf-toolbox-control"></a>Creación de un control de cuadro de herramientas de WPF
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La plantilla de Control de cuadro de herramientas WPF (Windows Presentation Framework) le permite crear controles de WPF que se agregan automáticamente a la **cuadro de herramientas** cuando se instala la extensión. En este tema se muestra cómo usar la plantilla para crear un **cuadro de herramientas** control que se puede distribuir a otros usuarios.  
  
 A partir de Visual Studio 2015, no instale el SDK de Visual Studio desde el centro de descarga. Se incluye como una característica opcional en el programa de instalación de Visual Studio. También puede instalar el SDK de VS más adelante. Para obtener más información, consulte [instalar el SDK de Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-wpf-toolbox-control"></a>Creación de un control de cuadro de herramientas de WPF  
  
#### <a name="create-an-extension-with-a-wpf-toolbox-control"></a>Crear una extensión con un Control de cuadro de herramientas WPF  
  
1.  Cree un proyecto VSIX denominado `MyToolboxControl`. Puede encontrar la plantilla de proyecto VSIX en el **nuevo proyecto** en el cuadro de diálogo **Visual C# / extensibilidad**.  
  
2.  Cuando se abra el proyecto, agregue un **Control Toolbox de WPF** plantilla de elemento denominado `MyToolboxControl`. En el **el Explorador de soluciones**, haga clic en el nodo del proyecto y seleccione **Agregar / nuevo elemento**. En el **Agregar nuevo elemento** cuadro de diálogo, vaya a **Visual C# / extensibilidad** y seleccione **Control Toolbox de WPF**. En el **nombre** campo en la parte inferior de la ventana, cambie el nombre de archivo de comandos para `MyToolboxControl.cs`.  
  
     La solución contiene ahora un control de usuario, un `ProvideToolboxControlAttribute` <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute> que agrega el control a la **cuadro de herramientas**y un **Microsoft.VisualStudio.ToolboxControl** entrada del activo en el manifiesto VSIX para  implementación.  
  
#### <a name="to-create-the-control-ui"></a>Para crear la interfaz de usuario del control  
  
1.  Abra MyToolboxControl.xaml en el diseñador.  
  
     El diseñador muestra un control <xref:System.Windows.Controls.Grid> que contiene un control <xref:System.Windows.Controls.Button>.  
  
2.  Organice el diseño de cuadrícula. Cuando se selecciona el <xref:System.Windows.Controls.Grid> controlar, aparecen barras de control en azul en los bordes superiores e izquierdos de la cuadrícula. Puede agregar filas y columnas a la cuadrícula, haga clic en las barras.  
  
3.  Agregar controles secundarios a la cuadrícula. Puede colocar un control secundario arrastrándolo desde la **cuadro de herramientas** a una sección de la cuadrícula, o estableciendo su `Grid.Row` y `Grid.Column` atributos en el XAML. El ejemplo siguiente agrega dos etiquetas en la fila superior de la cuadrícula y un botón en la segunda fila.  
  
    ```xaml  
    <Grid>  
        <Label Grid.Row="0" Grid.Column="0" Name="label1" />  
        <Label Grid.Row="0" Grid.Column="1" Name="label2" />  
        <Button Name="button1" Click="button1_Click" Grid.Row="1" Grid.ColumnSpan="2" />  
    </Grid>  
    ```  
  
## <a name="renaming-the-control"></a>Cambiar el nombre del control  
 De forma predeterminada, el control aparecerá en el **cuadro de herramientas** como **MyToolboxControl** en un grupo denominado **MyToolboxControl.MyToolboxControl**. Puede cambiar estos nombres en el archivo MyToolboxControl.xaml.cs.  
  
1.  Abra MyToolboxControl.xaml.cs en la vista código.  
  
2.  Busque la clase MyToolboxControl y cámbielo por TestControl. (La forma más rápida de hacerlo es cambiar el nombre de la clase, a continuación, seleccione **cambiar el nombre** en el menú contextual y complete los pasos. (Para obtener más información sobre la **cambiar el nombre de** de comandos, consulte [cambiar el nombre de refactorización (C#)](../csharp-ide/rename-refactoring-csharp.md).)  
  
3.  Vaya a la `ProvideToolboxControl` atributo y cambie el valor del primer parámetro a **prueba**. Este es el nombre del grupo que contiene el control en el **cuadro de herramientas**.  
  
     El código resultante debe tener este aspecto:  
  
    ```csharp  
    [ProvideToolboxControl("Test", true)]  
    public partial class TestControl : UserControl  
    {  
        public TestControl()  
        {  
            InitializeComponent();  
        }  
    }  
    ```  
  
## <a name="building-testing-and-deployment"></a>Compilación, prueba e implementación  
 Cuando se depura el proyecto, debe buscar el control instalado en el **cuadro de herramientas** de la instancia experimental de Visual Studio.  
  
#### <a name="to-build-and-test-the-control"></a>Para compilar y probar el control  
  
1.  Recompilar el proyecto e iniciar la depuración.  
  
2.  En la nueva instancia de Visual Studio, cree un proyecto de aplicación WPF. Asegúrese de que el Diseñador XAML está abierto.  
  
3.  Busque el control en el **Cuadro de herramientas** y arrástrelo a la superficie de diseño.  
  
4.  Empiece a depurar la aplicación de WPF.  
  
5.  Compruebe que aparece el control.  
  
#### <a name="to-deploy-the-control"></a>Para implementar el control  
  
1.  Después de compilar el proyecto probado, puede encontrar el archivo .vsix en la carpeta \bin\debug\ del proyecto.  
  
2.  Puede instalarlo en un equipo local, haga doble clic en el archivo .vsix y siguiendo el procedimiento de instalación. Para desinstalar el control, vaya a **herramientas / extensiones y actualizaciones** y busque la extensión de control, a continuación, haga clic en **desinstalar**.  
  
3.  Cargue el archivo .vsix en una red o en un sitio web.  
  
     Si va a cargar el archivo a la [Galería de Visual Studio](http://go.microsoft.com/fwlink/?LinkID=123847) sitio Web, otros usuarios pueden usar **herramientas / extensiones y actualizaciones** en Visual Studio para buscar en línea para el control e instalarlo.

