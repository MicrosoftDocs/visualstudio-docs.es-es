---
title: "Creaci&#243;n de una p&#225;gina de opciones | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "páginas de opciones de herramientas [SDK de Visual Studio], crear"
ms.assetid: 9f4e210c-4b47-4daa-91fa-1c301c4587f9
caps.latest.revision: 62
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 62
---
# Creaci&#243;n de una p&#225;gina de opciones
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Este tutorial crea una página Herramientas\/Opciones sencilla que utiliza una cuadrícula de propiedades para examinar y establecer propiedades.  
  
 Para guardar estas propiedades a y restáurelos a partir de un archivo de configuración, siga estos pasos y, a continuación, consulte [Creación de una categoría de configuración](../extensibility/creating-a-settings-category.md).  
  
 La MPF proporciona dos clases para ayudarle a crear páginas de opciones de herramientas, el <xref:Microsoft.VisualStudio.Shell.Package> \(clase\) y la <xref:Microsoft.VisualStudio.Shell.DialogPage> clase. Crear un VSPackage para proporcionar un contenedor de estas páginas mediante subclases de la clase de paquete. Crear cada página de opciones de herramientas derivando de la clase de DialogPage.  
  
## Requisitos previos  
 A partir de Visual Studio 2015, no instale el SDK de Visual Studio desde el centro de descarga. Se incluye como una característica opcional de la instalación de Visual Studio. También puede instalar el SDK de VS más adelante. Para obtener más información, consulta [Instalar el SDK de Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).  
  
## Crear una página de cuadrícula de opciones de herramientas  
 En esta sección, creará una cuadrícula de propiedades de opciones de herramientas simple. Esta cuadrícula se utiliza para mostrar y cambiar el valor de una propiedad.  
  
#### Para crear el proyecto VSIX y agregar un VSPackage  
  
1.  Todas las extensiones de Visual Studio se inicia con un proyecto de implementación de VSIX que contiene los activos de la extensión. Crear un [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] proyecto VSIX denominado `MyToolsOptionsExtension`. Puede encontrar la plantilla de proyecto VSIX en la **nuevo proyecto** en el cuadro de diálogo **Visual C\# \/ extensibilidad**.  
  
2.  Agregar un paquete VSPackage agregando una plantilla de elemento de paquete de Visual Studio denominada `MyToolsOptionsPackage`. En el **el Explorador de soluciones**, haga clic en el nodo del proyecto y seleccione **Agregar \/ nuevo elemento**. En el **cuadro de diálogo Agregar nuevo elemento**, vaya a **elementos de Visual C\# \/ extensibilidad** y seleccione **paquete de Visual Studio**. En el **nombre** campo en la parte inferior del cuadro de diálogo, cambie el nombre de archivo a `MyToolsOptionsPackage.cs`. Para obtener más información sobre cómo crear un paquete VSPackage, consulte [Crear una extensión con un VSPackage](../extensibility/creating-an-extension-with-a-vspackage.md).  
  
#### Para crear la cuadrícula de propiedades de opciones de herramientas  
  
1.  Abra el archivo MyToolsOptionsPackage en el editor de código.  
  
2.  Agregue la siguiente instrucción using.  
  
    ```c#  
    using System.ComponentModel;  
    ```  
  
3.  Declare una clase OptionPageGrid y lo derivará de <xref:Microsoft.VisualStudio.Shell.DialogPage>.  
  
    ```c#  
    public class OptionPageGrid : DialogPage  
    {  }  
    ```  
  
4.  Aplicar un <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> a la clase de VSPackage que se asigna a la clase de una categoría de opciones y el nombre de la página de opciones para el OptionPageGrid. El resultado debería tener este aspecto:  
  
    ```c#  
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
  
    -   Aplicar un <xref:System.ComponentModel.DisplayNameAttribute?displayProperty=fullName> para asignar a la propiedad un nombre.  
  
    -   Aplicar un <xref:System.ComponentModel.DescriptionAttribute?displayProperty=fullName> para asignar a la propiedad una descripción.  
  
    ```c#  
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
    >  La implementación predeterminada de <xref:Microsoft.VisualStudio.Shell.DialogPage> admite propiedades convertidores adecuados o que son estructuras o matrices que se pueden expandir en las propiedades que tienen convertidores adecuados. Para obtener una lista de convertidores, consulte la <xref:System.ComponentModel> espacio de nombres.  
  
6.  Compile la solución y comience la depuración.  
  
7.  En la instancia experimental de Visual Studio, en el **herramientas** menú haga clic en **opciones**.  
  
     En el panel izquierdo debería ver **My Category**. \(Categorías de opciones se muestran en orden alfabético, por lo que debe aparecer sobre a mitad hacia abajo en la lista.\) Abra **My Category** y, a continuación, haga clic en **Mi página de cuadrícula**. La cuadrícula de opciones aparece en el panel derecho. Es la categoría de propiedad **Mis opciones de**, y el nombre de propiedad es **Mi opción entero**. La descripción de la propiedad **Mi opción entero**, aparece en la parte inferior del panel. Cambie el valor de su valor inicial de 256 a otra cosa. Haga clic en **Aceptar**, y, a continuación, vuelva a abrir **Mi página de cuadrícula**. Puede ver que el nuevo valor se conserva.  
  
     La página de opciones también está disponible a través de inicio rápido de Visual Studio. En la ventana de inicio rápido, en la esquina superior derecha del IDE, escriba **My Category** y verá **My Category –\> Mi página de cuadrícula** aparece en la lista desplegable.  
  
## Creación de un archivo de opciones de herramientas página  
 En esta sección, creará una página de opciones de herramientas con una interfaz de usuario personalizada. Utilice esta página para mostrar y cambiar el valor de una propiedad.  
  
1.  Abra el archivo MyToolsOptionsPackage en el editor de código.  
  
2.  Agregue la siguiente instrucción using.  
  
    ```vb  
    using System.Windows.Forms;  
    ```  
  
3.  Agregar un `OptionPageCustom` clase, justo antes del `OptionPageGrid` clase. Derive la nueva clase de `DialogPage`.  
  
    ```c#  
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
  
    ```c#  
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
  
5.  Aplicar un segundo <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> a la clase de VSPackage. Este atributo asigna la clase una categoría de opciones y el nombre de la página de opciones.  
  
    ```c#  
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
  
7.  Agregar un **TextBox** control al control de usuario.  
  
     En el **propiedades** ventana, en la barra de herramientas, haga clic en el **eventos** botón y, a continuación, haga doble clic en el **deje** eventos. Aparece el nuevo controlador de eventos en el código MyUserControl.cs.  
  
8.  Agregar un público `OptionsPage` campo, un `Initialize` método a la clase de control y actualizar el controlador de eventos para establecer la opción de valor para el contenido del cuadro de texto:  
  
    ```c#  
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
  
9. En el archivo de código del paquete, agregue una invalidación para el `OptionPageCustom.Window` propiedad a la clase OptionPageCustom para crear, inicializar y devolver una instancia de `MyUserControl`. La clase debe tener el siguiente aspecto:  
  
    ```c#  
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
  
11. En la instancia experimental, haga clic en **Herramientas \/ opciones**.  
  
12. Buscar **Mi categoría** y, a continuación, **personalizados página**.  
  
13. Cambie el valor de **OptionString**. Haga clic en **Aceptar**, y, a continuación, vuelva a abrir **Mi página personalizada**. Puede ver que se ha conservado el nuevo valor.  
  
## Acceso a opciones  
 En esta sección, obtendrá el valor de una opción de VSPackage que hospeda la página de opciones de herramientas asociada. La misma técnica puede utilizarse para obtener el valor de las propiedades públicas.  
  
1.  En el archivo de código del paquete, agregue una propiedad pública denominada **OptionInteger** a la **MyToolsOptionsPackage** clase.  
  
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
  
     Este código llama a <xref:Microsoft.VisualStudio.Shell.Package.GetDialogPage%2A> para crear o recuperar un `OptionPageGrid` instancia.`OptionPageGrid` llamadas <xref:Microsoft.VisualStudio.Shell.DialogPage.LoadSettingsFromStorage%2A> cargar sus opciones, que son propiedades públicas.  
  
2.  Ahora agregue una plantilla de elemento de comando personalizado denominada **MyToolsOptionsCommand** para mostrar el valor. En el **Agregar nuevo elemento** cuadro de diálogo, vaya a **Visual C\# \/ extensibilidad** y seleccione **comando personalizado**. En el **nombre** campo en la parte inferior de la ventana, el nombre del archivo de comandos **MyToolsOptionsCommand.cs**.  
  
3.  En el archivo MyToolsOptionsCommand, reemplace el cuerpo del comando `ShowMessageBox` método con lo siguiente:  
  
    ```c#  
    private void ShowMessageBox(object sender, EventArgs e)  
    {  
        MyToolsOptionsPackage myToolsOptionsPackage = this.package as MyToolsOptionsPackage;  
        System.Windows.Forms.MessageBox.Show(string.Format(CultureInfo.CurrentCulture, "OptionInteger: {0}", myToolsOptionsPackage.OptionInteger));  
    }  
  
    ```  
  
4.  Compile la solución y comience la depuración.  
  
5.  En la instancia experimental, en la **herramientas** menú, haga clic en **invocar MyToolsOptionsCommand**.  
  
     Un cuadro de mensaje muestra el valor actual de `OptionInteger`.  
  
## Vea también  
 [Opciones y páginas de opciones](../extensibility/internals/options-and-options-pages.md)