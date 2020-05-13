---
title: Creación de una página de opciones ( Options Page) Microsoft Docs
ms.date: 3/16/2019
ms.topic: conceptual
helpviewer_keywords:
- Tools Options pages [Visual Studio SDK], creating
ms.assetid: 9f4e210c-4b47-4daa-91fa-1c301c4587f9
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1607af2a6f68bd5593f9a185188b25b364926fe4
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739517"
---
# <a name="create-an-options-page"></a>Crear una página de opciones

Este tutorial crea una página sencilla Herramientas/Opciones que usa una cuadrícula de propiedades para examinar y establecer propiedades.

 Para guardar estas propiedades y restaurarlas desde un archivo de configuración, siga estos pasos y, a continuación, consulte [Crear una categoría](../extensibility/creating-a-settings-category.md)de configuración .

 El MPF proporciona dos clases para ayudarle <xref:Microsoft.VisualStudio.Shell.Package> a <xref:Microsoft.VisualStudio.Shell.DialogPage> crear páginas de opciones de herramientas, la clase y la clase. Crear un VSPackage para proporcionar un contenedor para `Package` estas páginas mediante la subclase de la clase. Puede crear cada página de opciones `DialogPage` de herramientas derivando de la clase.

## <a name="prerequisites"></a>Prerrequisitos

 A partir de Visual Studio 2015, no se instala el SDK de Visual Studio desde el centro de descarga. Se incluye como una característica opcional en la configuración de Visual Studio. También puede instalar el SDK de VS más adelante. Para obtener más información, vea [Instalar el SDK](../extensibility/installing-the-visual-studio-sdk.md)de Visual Studio .

## <a name="create-a-tools-options-grid-page"></a>Crear una página de cuadrícula Opciones de herramientas

 En esta sección, creará una cuadrícula de propiedades Opciones de herramientas simple. Utilice esta cuadrícula para mostrar y cambiar el valor de una propiedad.

### <a name="to-create-the-vsix-project-and-add-a-vspackage"></a>Para crear el proyecto VSIX y agregar un VSPackage

1. Cada extensión de Visual Studio comienza con un proyecto de implementación de VSIX, que contendrá los activos de extensión. Cree [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] un proyecto `MyToolsOptionsExtension`VSIX denominado . Puede encontrar la plantilla de proyecto VSIX en el cuadro de diálogo **Nuevo proyecto** buscando "vsix".

2. Agregue un VSPackage agregando una plantilla `MyToolsOptionsPackage`de elemento de paquete de Visual Studio denominada . En el **Explorador**de soluciones , haga clic con el botón secundario en el nodo del proyecto y seleccione **Agregar** > **nuevo elemento**. En el cuadro de **diálogo Agregar nuevo elemento**, vaya a**Extensibilidad** de elementos > de **Visual C.** y seleccione Paquete de **Visual Studio**. En el campo **Nombre** en la parte inferior `MyToolsOptionsPackage.cs`del cuadro de diálogo, cambie el nombre del archivo a . Para obtener más información acerca de cómo crear un VSPackage, vea [crear una extensión con un VSPackage](../extensibility/creating-an-extension-with-a-vspackage.md).

### <a name="to-create-the-tools-options-property-grid"></a>Para crear la cuadrícula de propiedades Opciones de herramientas

1. Abra el archivo *MyToolsOptionsPackage* en el editor de código.

2. Agregue la siguiente instrucción using.

   ```csharp
   using System.ComponentModel;
   ```

3. Declare `OptionPageGrid` una clase y <xref:Microsoft.VisualStudio.Shell.DialogPage>derivarla de .

   ```csharp
   public class OptionPageGrid : DialogPage
   {  }
   ```

4. Aplique <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> a `VSPackage` a la clase para asignar a la clase una categoría de opciones y el nombre de página de opciones para el OptionPageGrid. El resultado debería tener este aspecto:

    ```csharp
    [PackageRegistration(UseManagedResourcesOnly = true)]
    [InstalledProductRegistration("#110", "#112", "1.0", IconResourceID = 400)]
    [ProvideMenuResource("Menus.ctmenu", 1)]
    [Guid(GuidList.guidMyToolsOptionsPkgString)]
    [ProvideOptionPage(typeof(OptionPageGrid),
        "My Category", "My Grid Page", 0, 0, true)]
    public sealed class MyToolsOptionsPackage : Package
    ```

5. Agregue `OptionInteger` una propiedad `OptionPageGrid` a la clase.

    - Aplique <xref:System.ComponentModel.CategoryAttribute?displayProperty=fullName> a para asignar a la propiedad una categoría de cuadrícula de propiedades.

    - Aplique <xref:System.ComponentModel.DisplayNameAttribute?displayProperty=fullName> a para asignar a la propiedad un nombre.

    - Aplique <xref:System.ComponentModel.DescriptionAttribute?displayProperty=fullName> a para asignar a la propiedad una descripción.

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
    > La implementación <xref:Microsoft.VisualStudio.Shell.DialogPage> predeterminada de admite propiedades que tienen convertidores adecuados o que son estructuras o matrices que se pueden expandir en propiedades que tienen convertidores adecuados. Para obtener una lista de <xref:System.ComponentModel> convertidores, consulte el espacio de nombres.

6. Compile la solución y comience la depuración.

7. En la instancia experimental de Visual Studio, en el menú **Herramientas,** haga clic en **Opciones**.

     En el panel izquierdo, debería ver **Mi categoría**. (Las categorías de opciones se enumeran en orden alfabético, por lo que debería aparecer aproximadamente a la mitad de la lista.) Abra **Mi categoría** y, a continuación, haga clic en Mi página de **cuadrícula**. La cuadrícula de opciones aparece en el panel derecho. La categoría de propiedad es **Mis opciones**y el nombre de la propiedad es Mi **opción entero**. La descripción de la propiedad, **Mi opción de entero**, aparece en la parte inferior del panel. Cambie el valor de su valor inicial de 256 a otra cosa. Haga clic en **Aceptar**y, a continuación, vuelva a abrir **Mi página**de cuadrícula . Puede ver que el nuevo valor persiste.

     La página de opciones también está disponible a través del cuadro de búsqueda de Visual Studio. En el cuadro de búsqueda situado cerca de la parte superior del IDE, escriba **Mi categoría** y verá Mi **categoría -> Mi página** de cuadrícula en la lista de resultados.

## <a name="create-a-tools-options-custom-page"></a>Crear una página personalizada Opciones de herramientas

 En esta sección, creará una página Opciones de herramientas con una interfaz de usuario personalizada. Utilice esta página para mostrar y cambiar el valor de una propiedad.

1. Abra el archivo *MyToolsOptionsPackage* en el editor de código.

2. Agregue la siguiente instrucción using.

    ```csharp
    using System.Windows.Forms;
    ```

3. Agregue `OptionPageCustom` una clase, `OptionPageGrid` justo antes de la clase. Derive la nueva `DialogPage`clase de .

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

4. Agregue un atributo GUID. Agregue una propiedad OptionString:

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

5. Aplicar un <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> segundo a la clase VSPackage. Este atributo asigna a la clase una categoría de opciones y un nombre de página de opciones.

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

6. Agregue un nuevo control de **usuario** denominado MyUserControl al proyecto.

7. Agregue un control **TextBox** al control de usuario.

     En la ventana **Propiedades,** en la barra de herramientas, haga clic en el botón **Eventos** y, a continuación, haga doble clic en el evento **Leave.** El nuevo controlador de eventos aparece en el *código de MyUserControl.cs.*

8. Agregue un `OptionsPage` campo `Initialize` público, un método a la clase de control y actualice el controlador de eventos para establecer el valor de opción en el contenido del cuadro de texto:

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

     El `optionsPage` campo contiene una referencia `OptionPageCustom` a la instancia primaria. El `Initialize` método `OptionString` se muestra en **textbox**. El controlador de eventos escribe el valor `OptionString` actual de la **TextBox** en el momento en que el foco deja el **textbox**.

9. En el archivo de código de `OptionPageCustom.Window` paquete, `OptionPageCustom` agregue una invalidación de `MyUserControl`la propiedad a la clase para crear, inicializar y devolver una instancia de . La clase ahora debería tener este aspecto:

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

11. En la instancia **Tools** > experimental, haga clic en**Opciones de herramientas**.

12. Busque **Mi categoría** y, a continuación, Mi página **personalizada**.

13. Cambie el valor de **OptionString**. Haga clic en **Aceptar**y, a continuación, vuelva a abrir **Mi página personalizada**. Puede ver que el nuevo valor ha persistido.

## <a name="access-options"></a>Opciones de acceso

 En esta sección, obtendrá el valor de una opción del VSPackage que hospeda la página opciones de herramientas asociada. La misma técnica se puede utilizar para obtener el valor de cualquier propiedad pública.

1. En el archivo de código de paquete, agregue una propiedad pública denominada **OptionInteger** a la clase **MyToolsOptionsPackage.**

    ```csharp
    public int OptionInteger
    {
        get
        {
            OptionPageGrid page = (OptionPageGrid)GetDialogPage(typeof(OptionPageGrid));
            return page.OptionInteger;
        }
    }

    ```

     Este código <xref:Microsoft.VisualStudio.Shell.Package.GetDialogPage%2A> llama para `OptionPageGrid` crear o recuperar una instancia. `OptionPageGrid`llamadas <xref:Microsoft.VisualStudio.Shell.DialogPage.LoadSettingsFromStorage%2A> para cargar sus opciones, que son propiedades públicas.

2. Ahora agregue una plantilla de elemento de comando personalizada denominada **MyToolsOptionsCommand** para mostrar el valor. En el cuadro de diálogo **Agregar nuevo elemento** , vaya a**Extensibilidad** de **Visual C-** > y seleccione **Comando personalizado**. En el campo **Nombre** en la parte inferior de la ventana, cambie el nombre del archivo de comandos a *MyToolsOptionsCommand.cs*.

3. En el archivo *MyToolsOptionsCommand,* reemplace el `ShowMessageBox` cuerpo del método del comando por el siguiente:

    ```csharp
    private void ShowMessageBox(object sender, EventArgs e)
    {
        MyToolsOptionsPackage myToolsOptionsPackage = this.package as MyToolsOptionsPackage;
        System.Windows.Forms.MessageBox.Show(string.Format(CultureInfo.CurrentCulture, "OptionInteger: {0}", myToolsOptionsPackage.OptionInteger));
    }

    ```

4. Compile la solución y comience la depuración.

5. En la instancia experimental, en el menú **Herramientas** , haga clic en **Invocar MyToolsOptionsCommand**.

     Un cuadro de mensaje `OptionInteger`muestra el valor actual de .

## <a name="see-also"></a>Vea también

- [Páginas de opciones y opciones](../extensibility/internals/options-and-options-pages.md)
