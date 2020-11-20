---
title: Crear una página de opciones | Microsoft Docs
description: Obtenga información sobre cómo crear una página de herramientas/opciones simple que use una cuadrícula de propiedades para examinar y establecer propiedades.
ms.custom: SEO-VS-2020
ms.date: 3/16/2019
ms.topic: how-to
helpviewer_keywords:
- Tools Options pages [Visual Studio SDK], creating
ms.assetid: 9f4e210c-4b47-4daa-91fa-1c301c4587f9
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 41102dfbbf1e49dadb1360ab0182810a47651dca
ms.sourcegitcommit: 5027eb5c95e1d2da6d08d208fd6883819ef52d05
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/20/2020
ms.locfileid: "94973715"
---
# <a name="create-an-options-page"></a>Crear una página de opciones

En este tutorial se crea una página de herramientas/opciones simple que utiliza una cuadrícula de propiedades para examinar y establecer propiedades.

 Para guardar estas propiedades y restaurarlas desde un archivo de configuración, siga estos pasos y, a continuación, vea [crear una categoría de configuración](../extensibility/creating-a-settings-category.md).

 MPF proporciona dos clases para ayudarle a crear páginas de opciones de herramientas, la <xref:Microsoft.VisualStudio.Shell.Package> clase y la <xref:Microsoft.VisualStudio.Shell.DialogPage> clase. Cree un VSPackage para proporcionar un contenedor para estas páginas mediante la creación de subclases de la `Package` clase. Cree cada página de opciones de herramientas mediante la derivación de la `DialogPage` clase.

## <a name="prerequisites"></a>Requisitos previos

 A partir de Visual Studio 2015, no se instala el SDK de Visual Studio desde el centro de descarga. Se incluye como una característica opcional en el programa de instalación de Visual Studio. También puede instalar el SDK de VS después. Para obtener más información, vea [instalar el SDK de Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-a-tools-options-grid-page"></a>Crear una página de cuadrícula de opciones de herramientas

 En esta sección, creará una cuadrícula de propiedades de opciones de herramientas simples. Esta cuadrícula se usa para mostrar y cambiar el valor de una propiedad.

### <a name="to-create-the-vsix-project-and-add-a-vspackage"></a>Para crear el Proyecto VSIX y agregar un VSPackage

1. Cada extensión de Visual Studio comienza con un proyecto de implementación de VSIX, que contendrá los recursos de la extensión. Cree un [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Proyecto VSIX denominado `MyToolsOptionsExtension` . Para buscar la plantilla de Proyecto VSIX en el cuadro de diálogo **nuevo proyecto** , busque "VSIX".

2. Agregue un VSPackage agregando una plantilla de elementos de paquete de Visual Studio denominada `MyToolsOptionsPackage` . En el **Explorador de soluciones**, haga clic con el botón secundario en el nodo del proyecto y seleccione **Agregar**  >  **nuevo elemento**. En el **cuadro de diálogo Agregar nuevo elemento**, vaya a la extensibilidad de **elementos de Visual C#**  >  **Extensibility** y seleccione **paquete de Visual Studio**. En el campo **nombre** de la parte inferior del cuadro de diálogo, cambie el nombre del archivo a `MyToolsOptionsPackage.cs` . Para obtener más información sobre cómo crear un VSPackage, vea [crear una extensión con un VSPackage](../extensibility/creating-an-extension-with-a-vspackage.md).

### <a name="to-create-the-tools-options-property-grid"></a>Para crear la cuadrícula de propiedades opciones de herramientas

1. Abra el archivo *MyToolsOptionsPackage* en el editor de código.

2. Agregue la siguiente instrucción using.

   ```csharp
   using System.ComponentModel;
   ```

3. Declare una `OptionPageGrid` clase y derivela de <xref:Microsoft.VisualStudio.Shell.DialogPage> .

   ```csharp
   public class OptionPageGrid : DialogPage
   {  }
   ```

4. Aplique <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> a la `VSPackage` clase para asignar a la clase una categoría de opciones y un nombre de página de opciones para OptionPageGrid. El resultado debería ser similar al siguiente:

    ```csharp
    [PackageRegistration(UseManagedResourcesOnly = true)]
    [InstalledProductRegistration("#110", "#112", "1.0", IconResourceID = 400)]
    [ProvideMenuResource("Menus.ctmenu", 1)]
    [Guid(GuidList.guidMyToolsOptionsPkgString)]
    [ProvideOptionPage(typeof(OptionPageGrid),
        "My Category", "My Grid Page", 0, 0, true)]
    public sealed class MyToolsOptionsPackage : Package
    ```

5. Agregue una `OptionInteger` propiedad a la `OptionPageGrid` clase.

    - Aplique un <xref:System.ComponentModel.CategoryAttribute?displayProperty=fullName> para asignar a la propiedad una categoría de cuadrícula de propiedades.

    - Aplique un <xref:System.ComponentModel.DisplayNameAttribute?displayProperty=fullName> para asignar un nombre a la propiedad.

    - Aplique un <xref:System.ComponentModel.DescriptionAttribute?displayProperty=fullName> para asignar a la propiedad una descripción.

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
    > La implementación predeterminada de <xref:Microsoft.VisualStudio.Shell.DialogPage> admite propiedades que tienen convertidores adecuados o que son estructuras o matrices que se pueden expandir en propiedades que tienen convertidores adecuados. Para obtener una lista de convertidores, vea el <xref:System.ComponentModel> espacio de nombres.

6. Compile la solución y comience la depuración.

7. En la instancia experimental de Visual Studio, en el menú **herramientas** , haga clic en **Opciones**.

     En el panel izquierdo, debería ver **mi categoría**. (Las categorías de opciones se muestran en orden alfabético, por lo que debe aparecer cerca de la mitad de la lista). Abra **mi categoría** y, a continuación, haga clic en **mi página de cuadrícula**. La cuadrícula de opciones aparece en el panel derecho. La categoría de la propiedad es **My Options** y el nombre de la propiedad es **My Integer Option**. La descripción de la propiedad, **mi opción de entero**, aparece en la parte inferior del panel. Cambie el valor de su valor inicial de 256 a otra cosa. Haga clic en **Aceptar** y, a continuación, vuelva a abrir **la página de cuadrícula**. Puede ver que el nuevo valor persiste.

     La página Opciones también está disponible a través del cuadro de búsqueda de Visual Studio. En el cuadro de búsqueda situado cerca de la parte superior del IDE, escriba **mi categoría** y verá la **categoría-> la página** de la cuadrícula que aparece en los resultados.

## <a name="create-a-tools-options-custom-page"></a>Crear una página personalizada de opciones de herramientas

 En esta sección, creará una página de opciones de herramientas con una interfaz de usuario personalizada. Utilice esta página para mostrar y cambiar el valor de una propiedad.

1. Abra el archivo *MyToolsOptionsPackage* en el editor de código.

2. Agregue la siguiente instrucción using.

    ```csharp
    using System.Windows.Forms;
    ```

3. Agregue una `OptionPageCustom` clase, justo antes de la `OptionPageGrid` clase. Derive la nueva clase de `DialogPage` .

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

5. Aplique un segundo <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> a la clase VSPackage. Este atributo asigna a la clase una categoría de opciones y un nombre de página de opciones.

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

6. Agregue un nuevo **control de usuario** denominado MyUserControl al proyecto.

7. Agregue un control de **cuadro de texto** al control de usuario.

     En la ventana **propiedades** , en la barra de herramientas, haga clic en el botón **eventos** y, a continuación, haga doble clic en el evento **leave** . El nuevo controlador de eventos aparece en el código *MyUserControl.CS* .

8. Agregue un `OptionsPage` campo público, un `Initialize` método a la clase de control y actualice el controlador de eventos para establecer el valor de la opción en el contenido del cuadro de texto:

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

     El `optionsPage` campo contiene una referencia a la `OptionPageCustom` instancia primaria. El `Initialize` método se muestra `OptionString` en el **cuadro de texto**. El controlador de eventos escribe el valor actual del **cuadro de texto** en `OptionString` cuando el foco sale del **cuadro de texto**.

9. En el archivo de código del paquete, agregue una invalidación para la `OptionPageCustom.Window` propiedad a la `OptionPageCustom` clase para crear, inicializar y devolver una instancia de `MyUserControl` . La clase debería tener ahora el siguiente aspecto:

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

11. En la instancia experimental, haga clic en **herramientas**  >  **Opciones**.

12. Busque **mi categoría** y, a continuación, **mi página personalizada**.

13. Cambie el valor de **OptionString**. Haga clic en **Aceptar** y, a continuación, vuelva a abrir **mi página personalizada**. Puede ver que el nuevo valor ha persistido.

## <a name="access-options"></a>Opciones de acceso

 En esta sección, obtendrá el valor de una opción del VSPackage que hospeda la página Opciones de herramientas asociadas. Se puede usar la misma técnica para obtener el valor de cualquier propiedad pública.

1. En el archivo de código del paquete, agregue una propiedad pública denominada **OptionInteger** a la clase **MyToolsOptionsPackage** .

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

     Este código llama <xref:Microsoft.VisualStudio.Shell.Package.GetDialogPage%2A> a para crear o recuperar una `OptionPageGrid` instancia. `OptionPageGrid` llama <xref:Microsoft.VisualStudio.Shell.DialogPage.LoadSettingsFromStorage%2A> a para cargar sus opciones, que son propiedades públicas.

2. Ahora, agregue una plantilla de elemento de comando personalizada denominada **MyToolsOptionsCommand** para mostrar el valor. En el cuadro de diálogo **Agregar nuevo elemento** , vaya a extensibilidad de **Visual C#**  >  **Extensibility** y seleccione **comando personalizado**. En el campo **nombre** situado en la parte inferior de la ventana, cambie el nombre del archivo de comandos a *MyToolsOptionsCommand.CS*.

3. En el archivo *MyToolsOptionsCommand* , reemplace el cuerpo del método del comando `ShowMessageBox` por lo siguiente:

    ```csharp
    private void ShowMessageBox(object sender, EventArgs e)
    {
        MyToolsOptionsPackage myToolsOptionsPackage = this.package as MyToolsOptionsPackage;
        System.Windows.Forms.MessageBox.Show(string.Format(CultureInfo.CurrentCulture, "OptionInteger: {0}", myToolsOptionsPackage.OptionInteger));
    }

    ```

4. Compile la solución y comience la depuración.

5. En la instancia experimental, en el menú **herramientas** , haga clic en **invocar MyToolsOptionsCommand**.

     Un cuadro de mensaje muestra el valor actual de `OptionInteger` .

## <a name="see-also"></a>Vea también

- [Opciones y páginas de opciones](../extensibility/internals/options-and-options-pages.md)
