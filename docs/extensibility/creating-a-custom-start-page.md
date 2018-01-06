---
title: "Crear un personalizado la página de inicio | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d67e0c53-9f5a-45fb-a929-b9d2125c3c82
caps.latest.revision: "18"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: f1ce8112adffabcee835d7adf598e73d327ca3b6
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="creating-a-custom-start-page"></a>Crear una página principal personalizada
Puede crear una página de inicio personalizada siguiendo los pasos descritos en este documento.  
  
## <a name="creating-a-blank-start-page"></a>Crear una página de inicio en blanco  
 En primer lugar, realice una página de inicio en blanco mediante la creación de un archivo .xaml que tiene una estructura de etiquetas que va a reconocer Visual Studio. A continuación, agregar marcado y código subyacente para generar la apariencia y funcionalidad que desee.  
  
#### <a name="to-create-a-blank-start-page"></a>Para crear una página de inicio en blanco  
  
1.  Crear un nuevo proyecto del tipo **aplicación WPF** (**Visual C# / escritorio de Windows**.  
  
2.  Agregue una referencia a `Microsoft.VisualStudio.Shell.14.0`.  
  
3.  Abra el archivo XAML en el editor XML y cambie el nivel superior \<Ventana > elemento a una \<UserControl > elemento sin quitar cualquiera de las declaraciones de espacio de nombres.  
  
4.  Quitar el `x:Class` la declaración del elemento de nivel superior. Esto hace que el contenido XAML sea compatible con la ventana de herramientas de Visual Studio que hospeda la página de inicio.  
  
5.  Agregue las siguientes declaraciones de espacio de nombres en el nivel superior \<UserControl > elemento.  
  
    ```  
    xmlns:vs="clr-namespace:Microsoft.VisualStudio.PlatformUI;assembly=Microsoft.VisualStudio.Shell.14.0"  
    xmlns:vsfx="clr-namespace:Microsoft.VisualStudio.Shell;assembly=Microsoft.VisualStudio.Shell.14.0"  
    ```  
  
     Estos espacios de nombres permiten tener acceso a comandos de Visual Studio, los controles y configuración de la interfaz de usuario. Para obtener más información, consulte [agregar comandos de Microsoft Visual Studio a una página de inicio](../extensibility/adding-visual-studio-commands-to-a-start-page.md).  
  
     En el ejemplo siguiente se muestra el marcado en el archivo .xaml para una página de inicio en blanco. Cualquier contenido personalizado debería ir en interna <xref:System.Windows.Controls.Grid> elemento.  
  
    ```vb  
    <UserControl  
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"  
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"  
        xmlns:d="http://schemas.microsoft.com/expression/blend/2008"  
        xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"  
        xmlns:MyNamespace="clr-namespace:ManualStartPage;assembly=ManualStartPage"  
        xmlns:vs="clr-namespace:Microsoft.VisualStudio.PlatformUI;assembly=Microsoft.VisualStudio.Shell.14.0"  
                xmlns:vsfx="clr-namespace:Microsoft.VisualStudio.Shell;assembly=Microsoft.VisualStudio.Shell.14.0"  
        xmlns:local="clr-namespace:StartPageHost"  
        mc:Ignorable="d"  
         Height="350" Width="525">  
        <Grid>  
        <!--Add content here.-->  
        </Grid>  
    </UserControl>  
    ```  
  
6.  Agregar controles a vacío \<UserControl > elemento que se va a rellenar la página de inicio personalizada. Para obtener información sobre cómo agregar funcionalidad específica a Visual Studio, vea [agregar comandos de Microsoft Visual Studio a una página de inicio](../extensibility/adding-visual-studio-commands-to-a-start-page.md).  
  
## <a name="testing-and-applying-the-custom-start-page"></a>Probar y aplicar la página de inicio personalizada  
 No establezca la instancia principal de Visual Studio para ejecutar la página de inicio personalizada hasta que compruebe que no se bloquea Visual Studio. En su lugar, probarlo en la instancia experimental.  
  
#### <a name="to-test-a-manually-created-custom-start-page"></a>Para probar una página de inicio personalizada creada manualmente  
  
1.  Copie el archivo XAML y los archivos de texto o marcado auxiliares archivos, a la **%USERPROFILE%\My documentos\Visual Studio 2015\StartPages\\**  carpeta.  
  
2.  Si la página de inicio hace referencia a los tipos en ensamblados que no están instalados Visual Studio o los controles, copie los ensamblados y, a continuación, pegarlos en *carpeta de instalación de Visual Studio***\Common7\IDE\ PrivateAssemblies\\**.  
  
3.  En un símbolo del sistema de Visual Studio, escriba **devenv /rootsuffix Exp** para abrir una instancia experimental de Visual Studio.  
  
4.  En la instancia experimental, vaya a la **herramientas / opciones / entorno / inicio** página y seleccione el archivo XAML de la **Personalizar página principal** lista desplegable.  
  
5.  En el menú **Vista** , haga clic en **Página de inicio**.  
  
     Debe mostrarse la página de inicio personalizada. Si desea cambiar los archivos, debe cerrar la instancia experimental, realice los cambios, copie y pegue los archivos modificados y, a continuación, vuelva a abrir la instancia experimental para ver los cambios.  
  
#### <a name="to-apply-the-custom-start-page-in-the-primary-instance-of-visual-studio"></a>Para aplicar la opción de instalación página de inicio en la instancia principal de Visual Studio  
  
-   Una vez que haya probado su página de inicio y resultaba estable, use la **Personalizar página principal** opción en el **opciones** cuadro de diálogo para seleccionar como página de inicio en la instancia principal de Visual Studio  
  
## <a name="see-also"></a>Vea también  
 [Tutorial: Agregar XAML personalizado a la página de inicio](../extensibility/walkthrough-adding-custom-xaml-to-the-start-page.md)   
 [Agregar Control de usuario a la página de inicio](../extensibility/adding-user-control-to-the-start-page.md)   
 [Agregar comandos de Visual Studio a una página de inicio](../extensibility/adding-visual-studio-commands-to-a-start-page.md)   
 [Tutorial: Guardar configuración de usuario en una página de inicio](../extensibility/walkthrough-saving-user-settings-on-a-start-page.md)   
 [Implementación de páginas de inicio personalizadas](../extensibility/deploying-custom-start-pages.md)