---
title: Creación de una página de opciones | Microsoft Docs
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
- Tools Options pages [Visual Studio SDK], creating
ms.assetid: 9f4e210c-4b47-4daa-91fa-1c301c4587f9
caps.latest.revision: 63
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 9c65a91135c9346e0dfcabbe7422501ed4f02704
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/16/2018
ms.locfileid: "51751367"
---
# <a name="creating-an-options-page"></a>Creación de una página de opciones
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Este tutorial crea una página Herramientas/Opciones sencilla que usa una cuadrícula de propiedades para examinar y establecer propiedades.  
  
 Para guardar estas propiedades a y restaurarlas desde un archivo de configuración, siga estos pasos y, a continuación, consulte [crear una categoría de configuración](../extensibility/creating-a-settings-category.md).  
  
 MPF proporciona dos clases para ayudarle a crear páginas de opciones de herramientas, el <xref:Microsoft.VisualStudio.Shell.Package> clase y el <xref:Microsoft.VisualStudio.Shell.DialogPage> clase. Crear un VSPackage para proporcionar un contenedor para estas páginas mediante la creación de subclases de la clase de paquete. Crear cada página de opciones de herramientas mediante la derivación de la clase de DialogPage.  
  
## <a name="prerequisites"></a>Requisitos previos  
 A partir de Visual Studio 2015, no instale el SDK de Visual Studio desde el centro de descarga. Se incluye como una característica opcional en el programa de instalación de Visual Studio. También puede instalar el SDK de VS más adelante. Para obtener más información, consulte [instalar el SDK de Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-tools-options-grid-page"></a>Creación de una página de cuadrícula de opciones de herramientas  
 En esta sección, creará una cuadrícula de propiedades Opciones de herramientas simple. Utilice esta cuadrícula para mostrar y cambiar el valor de una propiedad.  
  
#### <a name="to-create-the-vsix-project-and-add-a-vspackage"></a>Para crear el proyecto VSIX y agregar un paquete VSPackage  
  
1.  Todas las extensiones de Visual Studio se inicia con un proyecto de implementación de VSIX que contendrá los recursos de extensión. Crear un [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] proyecto VSIX denominado `MyToolsOptionsExtension`. Puede encontrar la plantilla de proyecto VSIX en el **nuevo proyecto** en el cuadro de diálogo **Visual C# / extensibilidad**.  
  
2.  Agregar un paquete VSPackage mediante la adición de una plantilla de elemento de paquete de Visual Studio denominada `MyToolsOptionsPackage`. En el **el Explorador de soluciones**, haga clic en el nodo del proyecto y seleccione **Agregar / nuevo elemento**. En el **cuadro de diálogo Agregar nuevo elemento**, vaya a **elementos de Visual C# / extensibilidad** y seleccione **paquete de Visual Studio**. En el **nombre** campo en la parte inferior del cuadro de diálogo, cambie el nombre de archivo a `MyToolsOptionsPackage.cs`. Para obtener más información sobre cómo crear un VSPackage, consulte [crear una extensión con un VSPackage](../extensibility/creating-an-extension-with-a-vspackage.md).  
  
#### <a name="to-create-the-tools-options-property-grid"></a>Para crear la cuadrícula de propiedades Opciones de herramientas  
  
1.  Abra el archivo MyToolsOptionsPackage en el editor de código.  
  
2.  Agregue la siguiente instrucción using.  
  
    ```csharp  
    using System.ComponentModel;  
    ```  
  
3.  Declarar una clase OptionPageGrid y derívela desde <xref:Microsoft.VisualStudio.Shell.DialogPage>.  
  
    ```csharp  
    public class OptionPageGrid : DialogPage  
    {  }  
    ```  
  
4.  Aplicar un <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> a la clase de VSPackage para asignar a la clase de una categoría de opciones y el nombre de la página de opciones para el OptionPageGrid. El resultado debería tener este aspecto:  
  
    ```csharp  
    [PackageRegistration(UseManagedResourcesOnly = true)]  
    [InstalledProductRegistration("#110", "#112", "1.0", IconResourceID = 400)]  
    [ProvideMenuResource("Menus.ctmenu", 1)]  
    [Guid(GuidList.guidMyToolsOptionsPkgString)]  
    [ProvideOptionPage(typeof(OptionPageGrid),  
        "My Category", "My Grid Page", 0, 0, true)]  
    public sealed class MyToolsOptionsPackage : Package  
    ```  
  
5.  Agregar un `OptionInteger` propiedad a la `OptionPageGrid` clase.  
  
    -   Aplicar un <xref:System.ComponentModel.CategoryAttribute?displayProperty=fullName> para asignar a la propiedad de una categoría de la cuadrícula de propiedad.  
  
    -   Aplicar un <xref:System.ComponentModel.DisplayNameAttribute?displayProperty=fullName> para asignar a la propiedad de un nombre.  
  
    -   Aplicar un <xref:System.ComponentModel.DescriptionAttribute?displayProperty=fullName> para asignar a la propiedad de una descripción.  
  
    ```csharp  
    public class OptionPageGrid : DialogPage  
    {  
        private int optionInt = 256;  
  
        [Category("My Category")]  
        [DisplayName("My Integer Option")]  
        [Description("My integer option")]  
        public int OptionInteger  
        {  
            get { return optionInt; }  
            set { optionInt = value; }  
        }  
    }  
    ```  
  
    > [!NOTE]
    >  La implementación predeterminada de <xref:Microsoft.VisualStudio.Shell.DialogPage> admite propiedades que tienen los convertidores de tipos adecuadas o que son estructuras o matrices que se pueden expandir en las propiedades que tienen los convertidores de tipos adecuados. Para obtener una lista de los convertidores de tipos, vea el <xref:System.ComponentModel> espacio de nombres.  
  
6.  Compile la solución y comience la depuración.  
  
7.  En la instancia experimental de Visual Studio, en el **herramientas** menú haga clic en **opciones**.  
  
     En el panel izquierdo aparecerá **My Category**. (Categorías de las opciones se enumeran en orden alfabético, por lo que debe aparecer sobre mitad abajo en la lista.) Abra **My Category** y, a continuación, haga clic en **mi página de cuadrícula**. La cuadrícula de opciones aparece en el panel derecho. La categoría de propiedad es **Mis opciones**, y es el nombre de propiedad **mi opción entero**. La descripción de la propiedad **mi opción entero**, aparece en la parte inferior del panel. Cambie el valor de su valor inicial de 256 a otra cosa. Haga clic en **Aceptar**y, a continuación, vuelva a abrir **mi página de cuadrícula**. Puede ver que el nuevo valor se conserva.  
  
     La página de opciones también está disponible a través de inicio rápido de Visual Studio. En la ventana de inicio rápido en la esquina superior derecha del IDE, escriba **My Category** y verá **My Category –> Mi página de cuadrícula** aparece en la lista desplegable.  
  
## <a name="creating-a-tools-options-custom-page"></a>Creación de herramientas opciones personalizada página  
 En esta sección, creará una página de opciones de herramientas con una interfaz de usuario personalizada. Utilice esta página para mostrar y cambiar el valor de una propiedad.  
  
1.  Abra el archivo MyToolsOptionsPackage en el editor de código.  
  
2.  Agregue la siguiente instrucción using.  
  
    ```csharp  
    using System.Windows.Forms;  
    ```  
  
3.  Agregar un `OptionPageCustom` clase justo antes del `OptionPageGrid` clase. Derive la clase nueva de `DialogPage`.  
  
    ```csharp  
    public class OptionPageCustom : DialogPage  
    {  
        private string optionValue = "alpha";  
  
        public string OptionString  
        {  
            get { return optionValue; }  
            set { optionValue = value; }  
        }  
    }  
    ```  
  
4.  Agregue un atributo GUID. Agregue una propiedad OptionString:  
  
    ```csharp  
    [Guid("00000000-0000-0000-0000-000000000000")]  
    public class OptionPageCustom : DialogPage  
    {  
        private string optionValue = "alpha";  
  
        public string OptionString  
        {  
            get { return optionValue; }  
            set { optionValue = value; }  
        }  
    }  
    ```  
  
5.  Aplicar un segundo <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> a la clase de VSPackage. Este atributo asigna la clase de una categoría de opciones y el nombre de la página de opciones.  
  
    ```csharp  
    [PackageRegistration(UseManagedResourcesOnly = true)]  
    [InstalledProductRegistration("#110", "#112", "1.0", IconResourceID = 400)]  
    [ProvideMenuResource("Menus.ctmenu", 1)]  
    [Guid(GuidList.guidMyToolsOptionsPkgString)]  
    [ProvideOptionPage(typeof(OptionPageGrid),  
        "My Category", "My Grid Page", 0, 0, true)]  
    [ProvideOptionPage(typeof(OptionPageCustom),  
        "My Category", "My Custom Page", 0, 0, true)]  
    public sealed class MyToolsOptionsPackage : Package  
    ```  
  
6.  Agregue un nuevo **Control de usuario** denominado MyUserControl al proyecto.  
  
7.  Agregar un **TextBox** control para el control de usuario.  
  
     En el **propiedades** ventana, en la barra de herramientas, haga clic en el **eventos** botón y, a continuación, haga doble clic en el **deje** eventos. En el código de MyUserControl.cs aparece el nuevo controlador de eventos.  
  
8.  Agregar una pública `OptionsPage` campo, un `Initialize` método a la clase de control y actualizar el controlador de eventos para establecer la opción de valor para el contenido del cuadro de texto:  
  
    ```csharp  
    public partial class MyUserControl : UserControl  
    {  
        public MyUserControl()  
        {  
            InitializeComponent();  
        }  
  
        internal OptionPageCustom optionsPage;  
  
        public void Initialize()  
        {  
            textBox1.Text = optionsPage.OptionString;  
        }  
  
        private void textBox1_Leave(object sender, EventArgs e)  
        {  
            optionsPage.OptionString = textBox1.Text;  
        }  
    }  
    ```  
  
     El `optionsPage` campo contiene una referencia al elemento primario `OptionPageCustom` instancia. El `Initialize` método muestra `OptionString` en el **TextBox**. El controlador de eventos escribe el valor actual de la **TextBox** a la `OptionString` cuando el enfoque deja el **TextBox**.  
  
9. En el archivo de código del paquete, agregue una invalidación para el `OptionPageCustom.Window` propiedad a la clase OptionPageCustom para crear, inicializar y devolver una instancia de `MyUserControl`. La clase debe ser ahora similar al siguiente:  
  
    ```csharp  
    [Guid("00000000-0000-0000-0000-000000000000")]  
    public class OptionPageCustom : DialogPage  
    {  
        private string optionValue = "alpha";  
  
        public string OptionString  
        {  
            get { return optionValue; }  
            set { optionValue = value; }  
        }  
  
        protected override IWin32Window Window  
        {  
            get  
            {  
                MyUserControl page = new MyUserControl();  
                page.optionsPage = this;  
                page.Initialize();  
                return page;  
            }  
        }  
    }  
    ```  
  
10. Compile y ejecute el proyecto.  
  
11. En la instancia experimental, haga clic en **herramientas / opciones**.  
  
12. Buscar **mi categoría** y, a continuación, **personalizados página**.  
  
13. Cambie el valor de **OptionString**. Haga clic en **Aceptar**y, a continuación, vuelva a abrir **mi página personalizada**. Puede ver que se ha guardado el nuevo valor.  
  
## <a name="accessing-options"></a>Acceder a las opciones  
 En esta sección, obtendrá el valor de una opción de VSPackage que hospeda la página de opciones de herramientas asociada. La misma técnica puede utilizarse para obtener el valor de cualquier propiedad pública.  
  
1.  En el archivo de código de paquete, agregue una propiedad pública denominada **OptionInteger** a la **MyToolsOptionsPackage** clase.  
  
    ```  
    public int OptionInteger  
    {  
        get  
        {  
            OptionPageGrid page = (OptionPageGrid)GetDialogPage(typeof(OptionPageGrid));  
            return page.OptionInteger;  
        }  
    }  
  
    ```  
  
     Este código llama a <xref:Microsoft.VisualStudio.Shell.Package.GetDialogPage%2A> para crear o recuperar un `OptionPageGrid` instancia. `OptionPageGrid` las llamadas <xref:Microsoft.VisualStudio.Shell.DialogPage.LoadSettingsFromStorage%2A> para cargar sus opciones, que son propiedades públicas.  
  
2.  Ahora agregue una plantilla de elemento de comando personalizado denominada **MyToolsOptionsCommand** para mostrar el valor. En el **Agregar nuevo elemento** cuadro de diálogo, vaya a **Visual C# / extensibilidad** y seleccione **comando personalizado**. En el **nombre** campo en la parte inferior de la ventana, cambie el nombre de archivo de comandos para **MyToolsOptionsCommand.cs**.  
  
3.  En el archivo MyToolsOptionsCommand, reemplace el cuerpo del comando `ShowMessageBox` método con lo siguiente:  
  
    ```csharp  
    private void ShowMessageBox(object sender, EventArgs e)  
    {  
        MyToolsOptionsPackage myToolsOptionsPackage = this.package as MyToolsOptionsPackage;  
        System.Windows.Forms.MessageBox.Show(string.Format(CultureInfo.CurrentCulture, "OptionInteger: {0}", myToolsOptionsPackage.OptionInteger));  
    }  
  
    ```  
  
4.  Compile la solución y comience la depuración.  
  
5.  En la instancia experimental, en el **herramientas** menú, haga clic en **MyToolsOptionsCommand invocar**.  
  
     Un cuadro de mensaje muestra el valor actual de `OptionInteger`.  
  
## <a name="see-also"></a>Vea también  
 [Opciones y páginas de opciones](../extensibility/internals/options-and-options-pages.md)

