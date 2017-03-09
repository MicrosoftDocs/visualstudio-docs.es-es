---
title: "Desarrollo avanzado de controles del cuadro de herramientas | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Cuadro de herramientas [Visual Studio SDK], agregar elementos mediante MPF"
ms.assetid: d22479a8-6d95-400c-a115-f46d10c10d2f
caps.latest.revision: 19
caps.handback.revision: 19
manager: "douge"
---
# Desarrollo avanzado de controles del cuadro de herramientas
> [!NOTE]
>  La manera recomendada de agregar controles personalizados al cuadro de herramientas es utilizar plantillas del Control de cuadro de herramientas que vienen con Visual Studio 10 SDK.  Este tema se mantiene por compatibilidad con versiones anteriores, agregar controles existentes al cuadro de herramientas, y para desarrollo avanzadas del control de cuadro de herramientas.  
>   
>  Para obtener más información sobre cómo crear controles de cuadro de herramientas mediante plantillas, vea [Cómo: Crear un control Toolbox que use formularios Windows Forms](../misc/how-to-create-a-toolbox-control-that-uses-windows-forms.md) y [Crear un Control de cuadro de herramientas WPF](../extensibility/creating-a-wpf-toolbox-control.md).  
  
 Un VSPackage según el managed package puede ampliar la funcionalidad de cuadro de herramientas de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] agregando controles, objetos derivados de los objetos de <xref:System.Drawing.Design.ToolboxItem> .  Cada <xref:System.Drawing.Design.ToolboxItem> se implementa mediante un objeto derivado de <xref:System.ComponentModel.Component>.  
  
## Proveedor VSPackage de elementos del cuadro de herramientas  
 Un VSPackage según el managed package debe registrarse como un proveedor de control del cuadro de herramientas con los atributos de [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] y controlar eventos Cuadro de herramientas\-relacionados.  
  
#### Para configurar un Paquete como proveedor del elemento del cuadro de herramientas  
  
1.  Cree una instancia de <xref:Microsoft.VisualStudio.Shell.ProvideToolboxItemsAttribute> aplicado a la clase que implementa <xref:Microsoft.VisualStudio.Shell.Package>.  Por ejemplo:  
  
    ```vb#  
    Namespace Vsip.LoadToolboxMembers   
        <ProvideToolboxItems(14)> _   
        <DefaultRegistryRoot("Software\Microsoft\VisualStudio\8.0")> _   
        <InstalledProductRegistration(False, "#100", "#102", "1.0", IconResourceID := 400)> _   
        <ProvideLoadKey("Standard", "1.0", "Package Name", "Company", 1)> _   
        <ProvideMenuResource(1000, 1)> _   
        <Guid("YYYYYYYY-YYYY-YYYY-YYYY-YYYYYYYYYYYY")> _   
        Public Class LoadToolboxMembers   
            Inherits Package   
        End Class   
    End Namespace  
    ```  
  
    ```c#  
    namespace Vsip.LoadToolboxMembers {  
        [ProvideToolboxItems(14)]  
        [DefaultRegistryRoot("Software\\Microsoft\\VisualStudio\\8.0")]  
        [InstalledProductRegistration(false, "#100", "#102", "1.0", IconResourceID = 400)]  
        [ProvideLoadKey("Standard", "1.0", "Package Name", "Company", 1)]  
        [ProvideMenuResource(1000, 1)]  
        [Guid("YYYYYYYY-YYYY-YYYY-YYYY-YYYYYYYYYYYY")]  
        public class LoadToolboxMembers : Package {  
    ```  
  
    > [!NOTE]
    >  El constructor de <xref:Microsoft.VisualStudio.Shell.ProvideToolboxItemsAttribute> toma un número de versión entero como argumento.  El entorno de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] utiliza el número de versión para determinar si un Paquete que proporciona los objetos de <xref:System.Drawing.Design.ToolboxItem> debe volver a cargarse o si la información almacenada en caché se puede utilizar el cuadro de herramientas.  Para garantizar recargar de un Paquete al proporcionar a <xref:System.Drawing.Design.ToolboxItem> que está en desarrollo, aumente siempre el número de versión después de cualquier modificación.  
  
2.  Si los objetos de <xref:System.Drawing.Design.ToolboxItem> proporcionan formatos de Portapapeles no estándar del cuadro de herramientas, una instancia de <xref:Microsoft.VisualStudio.Shell.ProvideToolboxFormatAttribute> se debe aplicar a la clase que implementa el objeto de <xref:Microsoft.VisualStudio.Shell.Package> para cada formato de Portapapeles compatibles los objetos de <xref:System.Drawing.Design.ToolboxItem> que el paquete VSPackage proporciona.  
  
     Para obtener más información sobre formatos de Portapapeles admitidos en el cuadro de herramientas, vea [Extensión del Cuadro de herramientas](../misc/extending-the-toolbox.md).  
  
    > [!NOTE]
    >  Si un VSPackage indica que proporciona cualquier objeto de <xref:System.Drawing.Design.ToolboxItem> con formatos de Portapapeles no estándar, el entorno de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] supone que sólo los formatos indicados por las instancias de <xref:Microsoft.VisualStudio.Shell.ProvideToolboxFormatAttribute> aplicados a la clase de<xref:Microsoft.VisualStudio.Shell.Package> de un Paquete que la implementación admitida por el paquete VSPackage.  Si un VSPackage necesita admitir los formatos de Portapapeles predeterminados así como un formato no estándar, debe solicitar una instancia de <xref:Microsoft.VisualStudio.Shell.ProvideToolboxFormatAttribute> cada formato predeterminado junto con el formato no estándar.  
  
3.  Si el paquete VSPackage proporciona la configuración dinámica de <xref:System.Drawing.Design.ToolboxItem>, debe:  
  
    1.  Aplica una instancia de <xref:Microsoft.VisualStudio.Shell.ProvideToolboxItemConfigurationAttribute> construyó mediante <xref:System.Type> que el paquete para implementar la interfaz de <xref:Microsoft.VisualStudio.Shell.IConfigureToolboxItem> .  
  
    2.  En una de clase independiente de `public` de <xref:Microsoft.VisualStudio.Shell.Package>de VSPackage, el Paquete debe implementar la interfaz de <xref:Microsoft.VisualStudio.Shell.IConfigureToolboxItem> .  
  
         Una instancia de <xref:Microsoft.VisualStudio.Shell.ProvideAssemblyFilterAttribute> se debe aplicar a la clase que implementa <xref:Microsoft.VisualStudio.Shell.IConfigureToolboxItem>, utilizando una cadena que contiene los criterios de una selección \(filtro\) como argumento al constructor de instancia de <xref:Microsoft.VisualStudio.Shell.ProvideToolboxItemConfigurationAttribute> .  
  
 Para obtener información sobre cómo notificar el entorno de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] que un VSPackage proporciona controles de cuadro de herramientas, vea [Registrar características de compatibilidad del Cuadro de herramientas](../misc/registering-toolbox-support-features.md).  
  
 Para obtener un ejemplo que muestra cómo se puede implementar <xref:Microsoft.VisualStudio.Shell.IConfigureToolboxItem> admite, vea [Tutorial: Personalizar la configuración del elemento de cuadro de herramientas dinámicamente](../misc/walkthrough-customizing-toolbox-item-configuration-dynamically.md).  
  
1.  VSPackages que proporciona a <xref:System.Drawing.Design.ToolboxItem> debe controlar <xref:Microsoft.VisualStudio.Shell.Package.ToolboxInitialized> y eventos de <xref:Microsoft.VisualStudio.Shell.Package.ToolboxUpgraded> .  
  
    1.  Implemente los controladores para los eventos de <xref:Microsoft.VisualStudio.Shell.Package.ToolboxInitialized> y de <xref:Microsoft.VisualStudio.Shell.Package.ToolboxUpgraded> :  
  
        ```vb#  
        Private Sub OnToolboxUpgraded(ByVal sender As Object, ByVal e As EventArgs)   
            OnToolboxInitialized(send, e)   
        End Sub   
        Private Sub OnToolboxInitialized(ByVal sender As Object, ByVal e As EventArgs)   
            'Make sure all toolbox items are added.   
        End Sub  
        ```  
  
        ```c#  
        private void OnToolboxUpgraded(object sender, EventArgs e) {  
            OnToolboxInitialized(send,e);  
        }  
        private void OnToolboxInitialized(object sender, EventArgs e) {  
            //Make sure all toolbox items are added.  
        }  
        ```  
  
    2.  suscrito a los eventos de <xref:Microsoft.VisualStudio.Shell.Package.ToolboxInitialized> y de <xref:Microsoft.VisualStudio.Shell.Package.ToolboxUpgraded> .  
  
         Esto suele hacerse en el método de <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> de implementación de <xref:Microsoft.VisualStudio.Shell.Package> :  
  
        ```vb#  
        Protected Overloads Overrides Sub Initialize()   
            AddHandler ToolboxInitialized, AddressOf OnToolboxInitialized   
            AddHandler ToolboxUpgraded, AddressOf OnToolboxUpgraded   
        End Sub  
        ```  
  
        ```c#  
        protected override void Initialize() {  
            ToolboxInitialized += new EventHandler(OnToolboxInitialized);  
            ToolboxUpgraded += new EventHandler(OnToolboxUpgraded);  
        }  
        ```  
  
     Para obtener un ejemplo de cómo implementar controladores para <xref:Microsoft.VisualStudio.Shell.Package.ToolboxInitialized> y eventos de <xref:Microsoft.VisualStudio.Shell.Package.ToolboxUpgraded> , vea [Tutorial: Carga automática de elementos del cuadro de herramientas](../misc/walkthrough-autoloading-toolbox-items.md).  
  
## Creación de controles de cuadro de herramientas  
 La implementación subyacente de un control de cuadro de herramientas se debe ser derivada de <xref:System.ComponentModel.Component> y encapsular en el valor predeterminado o una implementación derivada del objeto de <xref:System.Drawing.Design.ToolboxItem> .  
  
 La manera más fácil de proporcionar <xref:System.ComponentModel.Component>\- deployment derivada de los controles de cuadro de herramientas se extiende un objeto derivado de <xref:System.Windows.Forms.Control>, en particular, la clase de <xref:System.Windows.Forms.UserControl> .  
  
#### Para crear los controles de cuadro de herramientas  
  
1.  Utilice el comando de **Agregar nuevo elemento** del Explorador De Soluciones de crear un objeto del que implemente <xref:System.Windows.Forms.UserControl>.  
  
    ```vb#  
    Public Partial Class ToolboxControl1   
        Inherits UserControl   
        Public Sub New()   
            InitializeComponent()   
        End Sub   
        Private Sub button1_Click(ByVal sender As Object, ByVal e As EventArgs)   
            MsgBox("Hello world from" & Me.ToString())   
        End Sub   
  
        Private Sub ToolboxItem1_Load(ByVal sender As Object, ByVal e As EventArgs)   
  
        End Sub   
    End Class  
    ```  
  
    ```c#  
    public partial class ToolboxControl1 : UserControl {  
            public ToolboxControl1() {  
                InitializeComponent();  
            }  
  
            private void button1_Click(object sender, EventArgs e) {  
                MessageBox.Show("Hello world from" + this.ToString());  
            }  
  
            private void ToolboxItem1_Load(object sender, EventArgs e) {  
  
            }  
        }  
    ```  
  
     Para obtener más información sobre los controles de formularios Windows Forms de creación y los controles de cuadro de herramientas, vea [Desarrollar controles personalizados de formularios Windows Forms con .NET Framework](../Topic/Developing%20Custom%20Windows%20Forms%20Controls%20with%20the%20.NET%20Framework.md) o [Tutorial: Carga automática de elementos del cuadro de herramientas](../misc/walkthrough-autoloading-toolbox-items.md).  
  
2.  \(Opcional\) una aplicación puede utilizar un objeto personalizado derivado del objeto de <xref:System.Drawing.Design.ToolboxItem> para proporcionar el control de cuadro de herramientas a **Cuadro de herramientas**.  
  
    > [!NOTE]
    >  Cualquier clase derivada del objeto de <xref:System.Drawing.Design.ToolboxItem> debe tener una instancia de <xref:System.SerializableAttribute> aplicadas.  
  
     Una implementación personalizada derivada de <xref:System.Drawing.Design.ToolboxItem> puede extender una aplicación proporcionando un mayor control sobre cómo los datos de <xref:System.Drawing.Design.ToolboxItem> es el control serializado, mejorado de los metadatos del diseñador, compatibilidad con los formatos de Portapapeles no estándar, y la funcionalidad que permite la interacción del usuario final.  
  
     En el ejemplo, un cuadro de diálogo para las características seleccionadas pide confirmación para los usuarios:  
  
    ```vb#  
    <ToolboxItemAttribute(GetType(CustomControl))> _   
    <Serializable()> _   
    Class CustomControl   
        Inherits ToolboxItem   
  
        Public Sub New(ByVal type As Type)   
            MyBase.New(GetType(CustomControl))   
        End Sub   
        Public Sub New(ByVal type As Type, ByVal icon As Bitmap)   
            MyBase.New(GetType(SCustomControl))   
            Me.DisplayName = "CustomContorl"   
            Me.Bitmap = icon   
        End Sub   
  
        Private Sub New(ByVal info As SerializationInfo, ByVal context As StreamingContext)   
            Deserialize(info, context)   
        End Sub   
        Protected Overloads Overrides Function CreateComponentsCore(ByVal host As IDesignerHost) As IComponent()   
            Dim dialog As New CustomControlDialog(host)   
            Dim dialogResult__1 As DialogResult = dialog.ShowDialog()   
            If dialogResult__1 = DialogResult.OK Then   
                Dim component As IComponent = DirectCast(dialog.CustomInstance, IComponent)   
                Dim container As IContainer = host.Container   
                container.Add(component)   
                Return New IComponent() {component}   
            Else   
                Return New IComponent() {}   
            End If   
        End Function   
    End Class  
    ```  
  
    ```c#  
    [ToolboxItemAttribute(typeof(CustomControl))]  
    [Serializable]  
    class CustomControl : ToolboxItem {  
  
        public CustomControl(Type type) : base(typeof(CustomControl)) {}  
            public CustomControl(Type type, Bitmap icon) : base(typeof(SCustomControl)) {  
            this.DisplayName = "CustomContorl";  
            this.Bitmap = icon;  
        }  
  
        private CustomControl(SerializationInfo info, StreamingContext context) {  
            Deserialize(info, context);  
        }  
        protected override IComponent[] CreateComponentsCore(IDesignerHost host) {  
            CustomControlDialog dialog = new CustomControlDialog(host);  
            DialogResult dialogResult = dialog.ShowDialog();  
            if (dialogResult == DialogResult.OK) {  
                IComponent component = (IComponent)dialog.CustomInstance;  
                IContainer container = host.Container;  
                container.Add(component);  
                return new IComponent[] { component };  
            }  
            else {  
                return new IComponent[] {};  
            }  
        }  
    }  
    ```  
  
> [!NOTE]
>  También es posible que una clase derivada del objeto de <xref:System.Drawing.Design.ToolboxItem> proporcionar su propia implementación autónoma de control subyacente.  Esa clase a continuación es responsable de crear y proporcionar todos los componentes subyacentes.  
  
## Suma explícito de elementos de cuadro de herramientas  
 Para agregar al cuadro de herramientas, un control debe estar en una instancia de <xref:System.Drawing.Design.ToolboxItem> o un objeto derivado de <xref:System.Drawing.Design.ToolboxItem> y agregar a **Cuadro de herramientas** mediante la interfaz de <xref:System.Drawing.Design.IToolboxService> .  
  
#### Para encapsular y agregar los controles de cuadro de herramientas  
  
1.  Encapsula la implementación de <xref:System.ComponentModel.Component> en una instancia de un objeto de <xref:System.Drawing.Design.ToolboxItem> o <xref:System.Drawing.Design.ToolboxItem>\- objeto derivado llamando al método de <xref:System.Drawing.Design.ToolboxItem.Initialize%2A> de ese objeto con <xref:System.Type?displayProperty=fullName>del componente que implementa:  
  
    ```vb#  
    Dim customItem As New ToolboxItem()   
    If customItem IsNot Nothing Then   
        customItem.Initialize(userControl)   
    End If  
    ```  
  
    ```c#  
    ToolboxItem customItem = new ToolboxItem() ;  
    if (customItem != null) {  
        customItem.Initialize(userControl);  
    }  
    ```  
  
     Anterior es un ejemplo de un objeto `userControl` derivado de <xref:System.Windows.Forms.UserControl> \(una instancia del objeto de `ToolboxControl1` anterior\) utilizado para construir nuevo <xref:System.Drawing.Design.ToolboxItem>.  
  
    > [!NOTE]
    >  La implementación predeterminada del constructor de <xref:System.Drawing.Design.ToolboxItem> que toma un argumento de <xref:System.Type?displayProperty=fullName> \(el constructor de<xref:System.Drawing.Design.ToolboxItem.%23ctor%28System.Type%29> llama al método de <xref:System.Drawing.Design.ToolboxItem.Initialize%2A> del objeto de <xref:System.Drawing.Design.ToolboxItem> .  
  
2.  Use el servicio del cuadro de herramientas \(<xref:System.Drawing.Design.IToolboxService>\) para agregar el objeto de <xref:System.Drawing.Design.ToolboxItem> construido de la implementación subyacente del control.  
  
     En el ejemplo siguiente, el acceso al servicio de cuadro de herramientas se obtiene, algunas de las propiedades de la instancia `customItem` de <xref:System.Drawing.Design.ToolboxItem> se establecen y, a continuación `customItem` se agrega a **Cuadro de herramientas**:  
  
    ```vb#  
    Dim toolboxService As IToolboxService = TryCast(GetService(GetType(IToolboxService)), IToolboxService)  
    customItem.Bitmap = New System.Drawing.Bitmap(ToolBoxControl1, "Control1.bmp")  
    customItem.DisplayName = "Custom Item"   
    toolboxService.AddToolboxItem(item, "Custom Tab")  
    ```  
  
    ```c#  
    IToolboxService toolboxService = GetService(typeof(IToolboxService)) as IToolboxService;  
    customItem.Bitmap = new System.Drawing.Bitmap(ToolboxControl1,"Control1.bmp");  
    customItem.DisplayName= "Custom Item";  
    toolboxService.AddToolboxItem(item, "Custom Tab");  
    ```  
  
## Mediante la reflexión para agregar Controles de cuadro de herramientas  
 Aplicar atributos a la clase que implementa un control de cuadro de herramientas permite el entorno de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] o una aplicación basada [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] de utilizar la reflexión para detectar automáticamente y agregar correctamente los controles a **Cuadro de herramientas**.  
  
#### Para aplicar reflexión y atributos a los controles de cuadro de herramientas  
  
1.  Identificar todos los objetos utilizados para los controles de cuadro de herramientas de implementan con instancias de <xref:System.ComponentModel.ToolboxItemAttribute>.  
  
     El tipo de instancia de <xref:System.ComponentModel.ToolboxItemAttribute> a una dejarán de objeto determina si y cómo <xref:System.Drawing.Design.ToolboxItem> se construye de ella.  
  
    1.  Aplicando una instancia de <xref:System.ComponentModel.ToolboxItemAttribute> construyó con un valor de `BOOLEAN` de `false` a un objeto crea ese objeto disponible para el cuadro de herramientas mediante reflexión.  
  
         Esto puede ser útil para aislar un objeto, como <xref:System.Windows.Forms.UserControl> de **Cuadro de herramientas** durante el desarrollo.  
  
    2.  Aplicando una instancia de <xref:System.ComponentModel.ToolboxItemAttribute> construyó con un valor de `BOOLEAN` de `true` a un objeto crea que objeto disponible al cuadro de herramientas mediante la reflexión y requiere que el objeto se agrega al cuadro de herramientas utilizando un objeto predeterminado de <xref:System.Drawing.Design.ToolboxItem> .  
  
    3.  Aplicando una instancia de <xref:System.ComponentModel.ToolboxItemAttribute> construyó con <xref:System.Type> de un objeto personalizado derivado de <xref:System.Drawing.Design.ToolboxItem> crea el objeto disponibles para **Cuadro de herramientas** mediante la reflexión y requiere que el objeto se agrega al cuadro de herramientas utilizando este objeto personalizado derivado de <xref:System.Drawing.Design.ToolboxItem>.  
  
2.  Especifique \(al mecanismo de reflexión del entorno de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] \) el mapa de bits para utilizar para mostrar el control del cuadro de herramientas en **Cuadro de herramientas** agregando una instancia de <xref:System.Drawing.ToolboxBitmapAttribute> a la implementación del control de cuadro de herramientas.  
  
3.  Si es necesario, se aplican las instancias de <xref:System.ComponentModel.ToolboxItemFilterAttribute> a los objetos de <xref:System.Drawing.Design.ToolboxItem> a la utilizan la reflexión para marcarlos estáticamente con los objetos que tienen un atributo coincidente.  
  
     En el ejemplo siguiente, la implementación de un control de cuadro de herramientas tiene una instancia de <xref:Microsoft.VisualStudio.Shell.ProvideAssemblyFilterAttribute> aplicadas, que crea ese control disponibles en **Cuadro de herramientas** sólo cuando el documento de trabajo actual es los diseñadores de <xref:System.Windows.Forms.UserControl>  
  
    ```vb#  
    <ToolboxItemFilter(System.Windows.Forms.UserControl, ToolboxItemFilterType.Require)> _   
    <SerializableAttribute()> _   
    <GuidAttribute("XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX")> _   
    Friend Class CustomToolboxItem   
        Inherits ToolboxItem   
    End Class  
    ```  
  
    ```c#  
    [ToolboxItemFilter(System.Windows.Forms.UserControl,ToolboxItemFilterType.Require)]  
    [SerializableAttribute()]  //ToolboxItem implementations much has this attribute.  
    [GuidAttribute("XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX")]  
    internal class CustomToolboxItem : ToolboxItem   
    ```  
  
 Hay tres técnicas básicas para utilizar la reflexión para cargar automáticamente <xref:System.Drawing.Design.ToolboxItem>.  
  
### Utilizando la funcionalidad de ToolService para recuperar los Controles del cuadro de herramientas  
 <xref:System.Drawing.Design.ToolboxService> proporciona VSPackages con los métodos estáticos de <xref:System.Drawing.Design.ToolboxService.GetToolboxItems%2A> que utilizan la reflexión para examinar los ensamblados para todos los tipos que los elementos admiten el elemento del cuadro de herramientas, y devuelven para esos tipos.  Para devolver, un elemento de cuadro de herramientas debe:  
  
-   Ser público.  
  
-   implemente la clase de <xref:System.ComponentModel.IComponent> .  
  
-   No ser abstracto.  
  
-   Tenga <xref:System.ComponentModel.ToolboxItemAttribute> en el tipo.  
  
-   No tener <xref:System.ComponentModel.ToolboxItemAttribute> establecido en `false` en su tipo  
  
-   No contener parámetros genéricos.  
  
##### para obtener esta lista  
  
1.  Cree una instancia de <xref:System.Reflection.Assembly> que hace referencia al ensamblado que se analiza para los objetos de <xref:System.Drawing.Design.ToolboxItem> .  
  
    > [!NOTE]
    >  para obtener una instancia de <xref:System.Reflection.Assembly> para el ensamblado actual, utilice el método estático <xref:System.Reflection.Assembly.GetExecutingAssembly%2A>.  
  
2.  Llame a <xref:System.Drawing.Design.ToolboxService.GetToolboxItems%2A>, devolviendo un objeto de <xref:System.Collections.ICollection> que contiene una lista de los objetos adecuados.  
  
    > [!NOTE]
    >  Si un objeto de <xref:System.Collections.ICollection> devuelto tiene una instancia válida de <xref:System.Drawing.ToolboxBitmapAttribute> asignado a su implementación, el método de <xref:System.Drawing.Design.ToolboxService.GetToolboxItems%2A> establecerá la propiedad de <xref:System.Drawing.Design.ToolboxItem.Bitmap%2A> del objeto de <xref:System.Drawing.Design.ToolboxItem> .  
  
3.  Utilice <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> para obtener acceso a <xref:System.Drawing.Design.IToolboxService>, y utilice el método de <xref:System.Drawing.Design.IToolboxService.AddToolboxItem%2A> para agregar elementos de objeto devuelto de <xref:System.Collections.ICollection> al cuadro de herramientas.  
  
     El código debajo de consultas la aplicación actual y obtiene una lista de todos los objetos de <xref:System.Drawing.Design.ToolboxItem> y los carga.  Para obtener un ejemplo que muestra en ejecutar código, vea el método de `Initialization` en [Tutorial: Personalizar la configuración del elemento de cuadro de herramientas dinámicamente](../misc/walkthrough-customizing-toolbox-item-configuration-dynamically.md).  
  
    ```vb#  
    Protected ToolboxItemList As ICollection = Nothing  
    ToolboxItemList = ToolboxService.GetToolboxItems(Assembly.GetExecutingAssembly(), "")  
    If ToolboxItemList Is Nothing Then   
        Throw New ApplicationException("Unable to generate a toolbox Items listing for " & [GetType]().FullName)   
    End If   
    Dim toolboxService As IToolboxService = TryCast(GetService(GetType(IToolboxService)), IToolboxService)   
    For Each itemFromList As ToolboxItem In ToolboxItemList   
        toolboxService.AddToolboxItem(itemFromList, CategoryTab)   
    Next  
    ```  
  
    ```c#  
    protected ICollection ToolboxItemList = null;  
    ToolboxItemList = ToolboxService.GetToolboxItems(Assembly.GetExecutingAssembly(), "");  
    if (ToolboxItemList == null){  
        throw new ApplicationException("Unable to generate a toolbox Items listing for "  
    + GetType().FullName);  
    }  
    IToolboxService toolboxService = GetService(typeof(IToolboxService)) as IToolboxService;  
    foreach (ToolboxItem itemFromList in ToolboxItemList){  
        toolboxService.AddToolboxItem(itemFromList, CategoryTab);  
    }  
    ```  
  
### Mediante los recursos incrustados de texto para cargar automáticamente los Controles del cuadro de herramientas  
 Un recurso de texto en un ensamblado que contiene una lista con formato correcto de controles de cuadro de herramientas puede ser utilizado por <xref:Microsoft.VisualStudio.Shell.Package.ParseToolboxResource%2A> automáticamente para cargar un control de cuadro de herramientas si tiene el formato correcto.  
  
 Un recurso de texto que contiene una lista de objetos a la carga debe estar disponible en un ensamblado accesible al Paquete.  
  
##### Para agregar y hacer que esté disponible un recurso de texto al ensamblado  
  
1.  En **Explorador de soluciones**, haga clic con el botón secundario en el proyecto.  
  
2.  Elija **Agregar**, haga clic en **Nuevo elemento**.  
  
3.  En el cuadro de diálogo de **Agregar nuevo elemento** , seleccione **Archivo de texto** y escriba un nombre.  
  
4.  En **Explorador de soluciones**, haga clic con el botón secundario en el archivo de texto creado recientemente y establezca la propiedad de **Build Action** el recurso incrustado.  
  
     Las entradas del control de **Cuadro de herramientas** carga deben contener el nombre de la clase que implementa, el nombre del ensamblado que lo contiene.  
  
     Para obtener información sobre el formato de las entradas de los controles de cuadro de herramientas al recurso incrustado de texto, vea la página de referencia de <xref:Microsoft.VisualStudio.Shell.Package.ParseToolboxResource%2A> .  
  
5.  Configurar una ruta de búsqueda de archivos que contienen los ensamblados que hospedaban objetos de control del cuadro de herramientas.  
  
     <xref:Microsoft.VisualStudio.Shell.Package.ParseToolboxResource%2A>, directorios de las búsquedas solo especificados en la entrada del Registro HKEY\_CURRENT\_USER \\Software\\Microsoft\\VisualStudio \\ *\<versión\>* \\AssemblyFolders, donde es el número de versión  *\<versión\>*  de lanzamiento de Visual Studio \(por ejemplo, 8,0\).  
  
    > [!NOTE]
    >  La ruta de acceso raíz HKEY\_LOCAL\_MACHINE \\SOFTWARE\\Microsoft\\VisualStudio \\ *\<versión\>*  se puede reemplazar con la raíz alternativa cuando se inicializa el shell de Visual Studio, o el uso de <xref:Microsoft.VisualStudio.Shell.DefaultRegistryRootAttribute>.  Para obtener más información, vea [Modificadores de línea de comandos](../extensibility/command-line-switches-visual-studio-sdk.md).  
  
     Para obtener información sobre el formato correcto de las entradas del Registro de AssemblyFolder, vea la página de referencia de <xref:Microsoft.VisualStudio.Shell.Package.ParseToolboxResource%2A> .  
  
6.  Obtenga una instancia de <xref:System.IO.TextReader.Synchronized%2A> que tiene acceso al recurso incrustado de texto, y, si la compatibilidad de localización es necesario para los nombres de categoría, una instancia de <xref:System.Resources.ResourceManager>, y utiliza estos para invocar el método de <xref:Microsoft.VisualStudio.Shell.Package.ParseToolboxResource%2A> .  
  
    ```vb#  
    Dim rm As New ResourceManager("TbxCategories", Assembly.GetExecutingAssembly())  
    Dim toolboxStream As Stream = TbxItemProvider.[GetType]().Assembly.GetManifestResourceStream("ToolboxItems.txt")  
    If toolboxStream IsNot Nothing Then   
        Using reader As TextReader = New StreamReader(toolboxStream)   
            ParseToolboxResource(reader, rm)   
        End Using   
    End If  
    ```  
  
    ```c#  
    ResourceManager rm = new ResourceManager("TbxCategories", Assembly.GetExecutingAssembly());  
    Stream toolboxStream = TbxItemProvider.GetType().Assembly.GetManifestResourceStream("ToolboxItems.txt");  
    if (toolboxStream != null) {  
        using (TextReader reader = new StreamReader(toolboxStream)) {  
        ParseToolboxResource(reader, rm);  
    }  
    }  
    ```  
  
     En el ejemplo anterior, una lista contenida en un recurso incrustado de texto en el ensamblado que contiene la clase `TbxItemProvider` se pasa a <xref:Microsoft.VisualStudio.Shell.Package.ParseToolboxResource%2A> junto con los recursos de cadena de `TbxCategories` .  
  
     El método buscará todos los archivos que contienen ensamblados en los directorios especificados en la entrada de Registro de AssemblyFolders para los controles de cuadro de herramientas enumerados en el recurso y los cargará.  
  
    > [!NOTE]
    >  Si un control de cuadro de herramientas encontrado por <xref:Microsoft.VisualStudio.Shell.Package.ParseToolboxResource%2A> tiene una instancia válida de <xref:System.Drawing.ToolboxBitmapAttribute> asignado a su implementación, <xref:Microsoft.VisualStudio.Shell.Package.ParseToolboxResource%2A> establecerá el mapa de bits utilizado para mostrar el control de cuadro de herramientas.  
  
### Explícitamente Mediante la reflexión para cargar automáticamente los Controles del cuadro de herramientas  
 Si es necesario explícitamente ver los ensamblados para obtener información sobre los controles de **Cuadro de herramientas** que contienen, en lugar de delegando la tarea a <xref:System.Drawing.Design.ToolboxService.GetToolboxItems%2A>, puede hacerlo.  
  
##### Para explícitamente utilizar la reflexión para cargar automáticamente los controles de cuadro de herramientas  
  
1.  Cree una instancia de <xref:System.Reflection.Assembly>, haciendo referencia a cada ensamblado que se analiza para los objetos de <xref:System.Drawing.Design.ToolboxItem> .  
  
    > [!NOTE]
    >  para obtener una instancia de <xref:System.Reflection.Assembly> para el ensamblado actual, utilice el método estático <xref:System.Reflection.Assembly.GetExecutingAssembly%2A>.  
  
2.  Para cada ensamblado se digitaliza, utilice el método de <xref:System.Reflection.Assembly.GetTypes%2A> del objeto de <xref:System.Reflection.Assembly> para obtener una lista de cada <xref:System.Type?displayProperty=fullName> en el ensamblado.  
  
3.  Compruebe que el tipo no es abstracto y no admite la interfaz de <xref:System.ComponentModel.IComponent> \(todas las implementaciones de los controles de cuadro de herramientas utilizados para crear instancias de un objeto de <xref:System.Drawing.Design.ToolboxItem> deben implementar esta interfaz\).  
  
4.  Obtener los atributos de <xref:System.Type> y utilice esta información para determinar si deseos de VSPackage para cargar el objeto.  
  
    > [!NOTE]
    >  Aunque en una entidad de seguridad que es posible crear un objeto de <xref:System.Drawing.Design.ToolboxItem> de una implementación de la interfaz de <xref:System.ComponentModel.IComponent> sin una instancia de <xref:System.ComponentModel.ToolboxItemAttribute> no establecida en `false` aplicara el, no se recomienda el hacerlo.  
  
5.  El uso <xref:System.Type.GetConstructor%2A> de obtener los constructores de objetos de <xref:System.Drawing.Design.ToolboxItem> que el cuadro de herramientas controla requiere.  
  
6.  Construya los objetos de <xref:System.Drawing.Design.ToolboxItem> y agréguelos a **Cuadro de herramientas**.  
  
 Para ver un uso explícito que muestra el ejemplo de la reflexión para obtener y cargar automáticamente los controles de cuadro de herramientas, vea `CreateItemList` descrito en [Tutorial: Carga automática de elementos del cuadro de herramientas](../misc/walkthrough-autoloading-toolbox-items.md).  
  
## Configuración de Control adicional del cuadro de herramientas  
 Un Paquete puede ejercer un control adicional sobre cuándo y cómo un control de cuadro de herramientas se muestra mediante **Cuadro de herramientas**, con la implementación de <xref:Microsoft.VisualStudio.Shell.IConfigureToolboxItem>, y el uso de <xref:Microsoft.VisualStudio.Shell.ProvideAssemblyFilterAttribute>, y <xref:Microsoft.VisualStudio.Shell.ProvideToolboxItemConfigurationAttribute>.  
  
 Las instancias de <xref:System.ComponentModel.ToolboxItemFilterAttribute> que se aplican a una clase proporcionan solo el control estático sobre cuándo y cómo un control de **Cuadro de herramientas** está disponible.  
  
#### Para crear compatibilidad dinámica de la configuración para los controles de cuadro de herramientas  
  
1.  Cree una clase que implementa la interfaz de <xref:Microsoft.VisualStudio.Shell.IConfigureToolboxItem> como parte de un Paquete.  
  
    > [!NOTE]
    >  La interfaz de <xref:Microsoft.VisualStudio.Shell.IConfigureToolboxItem> no se debe implementar en la misma clase que proporciona la implementación de un Paquete de <xref:Microsoft.VisualStudio.Shell.Package>.  
  
2.  Asociar la implementación de <xref:Microsoft.VisualStudio.Shell.IConfigureToolboxItem> con objetos de ensamblados específicos aplicando una instancia de <xref:Microsoft.VisualStudio.Shell.ProvideAssemblyFilterAttribute> al.  
  
     El ejemplo siguiente se proporciona una configuración dinámica para los ensamblados del objeto de control del cuadro de herramientas dentro del espacio de nombres y de exigir de `Vsip.*` que algunos objetos de <xref:System.Drawing.Design.ToolboxItem> estén visibles sólo con <xref:System.Windows.Forms.UserControl>\- los diseñadores basados y otro nunca visible con <xref:System.Windows.Forms.UserControl>\- los diseñadores basados en.  
  
    ```vb#  
    <ProvideAssemblyFilterAttribute("Vsip.*, Version=*, Culture=*, PublicKeyToken=*")> _   
    <GuidAttribute("XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX")> _   
    Public NotInheritable Class ToolboxConfig   
        Implements IConfigureToolboxItem   
        Public Sub New()   
        End Sub  
  
        ''' <summary>   
        ''' Adds extra configuration information to this toolbox item.   
        ''' </summary>   
        Public Sub ConfigureToolboxItem(ByVal item As ToolboxItem)   
            If item Is Nothing Then   
                Exit Sub   
            End If   
  
            'hide from .NET Compact Framework on the device designer.   
            Dim newFilter As ToolboxItemFilterAttribute = Nothing   
            If item.TypeName = GetType(ToolboxControl1).ToString() Then   
                newFilter = New ToolboxItemFilterAttribute("System.Windows.Forms.UserControl", ToolboxItemFilterType.Require)   
            ElseIf item.TypeName = GetType(ToolboxControl2).ToString() Then   
  
                newFilter = New ToolboxItemFilterAttribute("System.Windows.Forms.UserControl", ToolboxItemFilterType.Prevent)   
            End If   
            If newFilter IsNot Nothing Then   
                Dim array As New ArrayList()   
                array.Add(newFilter)   
                item.Filter = DirectCast(array.ToArray(GetType(ToolboxItemFilterAttribute)), ToolboxItemFilterAttribute())   
            End If   
        End Sub   
    End Class  
    ```  
  
    ```c#  
    [ProvideAssemblyFilterAttribute("Vsip.*, Version=*, Culture=*, PublicKeyToken=*")]  
        [GuidAttribute("XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX")]  
        public sealed class ToolboxConfig : IConfigureToolboxItem {  
            public ToolboxConfig() {  
            }  
  
            /// <summary>  
            ///     Adds extra configuration information to this toolbox item.  
            /// </summary>  
            public void ConfigureToolboxItem(ToolboxItem item) {  
                if (item == null)  
                    return;  
  
                //hide from .NET Compact Framework  on the device designer.  
                ToolboxItemFilterAttribute newFilter = null;  
                if (item.TypeName == typeof(ToolboxControl1).ToString()) {  
                    newFilter = new ToolboxItemFilterAttribute("System.Windows.Forms.UserControl",  
                                                          ToolboxItemFilterType.Require);  
                }   
                else if (item.TypeName == typeof(ToolboxControl2).ToString()) {  
  
                    newFilter = new ToolboxItemFilterAttribute("System.Windows.Forms.UserControl",  
                                                          ToolboxItemFilterType.Prevent);  
                }  
                if (newFilter != null) {  
                    ArrayList array = new ArrayList();  
                    array.Add(newFilter);  
                    item.Filter = (ToolboxItemFilterAttribute[])  
                            array.ToArray(typeof(ToolboxItemFilterAttribute));  
                }  
            }  
        }  
    }  
    ```  
  
3.  Registre un VSPackage como proporcionar una implementación concreta de <xref:Microsoft.VisualStudio.Shell.IConfigureToolboxItem> aplicando una instancia de <xref:Microsoft.VisualStudio.Shell.ProvideToolboxItemConfigurationAttribute> a la implementación del Paquete de <xref:Microsoft.VisualStudio.Shell.Package>.  
  
     El ejemplo siguiente informaría al entorno de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] que el paquete implementado por `Vsip.ItemConfiguration.ItemConfiguration` proporciona la clase `Vsip.ItemConfiguration.ToolboxConfiguration` a <xref:System.Drawing.Design.ToolboxItem>dinámicos admiten.  
  
    ```vb#  
    <ProvideToolboxItemsAttribute(3)> _   
    <DefaultRegistryRoot("Software\Microsoft\VisualStudio\8.0")> _   
    <InstalledProductRegistration(False, "#100", "#102", "1.0", IconResourceID := 400)> _   
    <ProvideLoadKey("Standard", "1.0", "Package Name", "Company", 1)> _   
    <ProvideMenuResource(1000, 1)> _   
    <ProvideToolboxItemConfigurationAttribute(GetType(ToolboxConfig))> _   
    <GuidAttribute("YYYYYYYY-YYYY-YYYY-YYYY-YYYYYYYYYYYY")> _   
    Public Class ItemConfiguration   
        Inherits Package   
    End Class  
    ```  
  
    ```c#  
    [ProvideToolboxItemsAttribute(3)]  
    [DefaultRegistryRoot("Software\\Microsoft\\VisualStudio\\8.0")]  
    [InstalledProductRegistration(false, "#100", "#102", "1.0", IconResourceID = 400)]  
    [ProvideLoadKey("Standard", "1.0", "Package Name", "Company", 1)]  
    [ProvideMenuResource(1000, 1)]  
    [ProvideToolboxItemConfigurationAttribute(typeof(ToolboxConfig))]  
  
    [GuidAttribute("YYYYYYYY-YYYY-YYYY-YYYY-YYYYYYYYYYYY")]  
    public class ItemConfiguration : Package  
    ```  
  
## Compatibilidad de arrastrar y colocar  
 Además de agregar a **Cuadro de herramientas** propio, los objetos de <xref:System.Drawing.Design.ToolboxItem> y sus implementaciones se pueden utilizar para ampliar la compatibilidad de arrastrar y colocar en [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] el IDE.  Esto puede permitir que los formatos de Portapapeles arbitrarios están expuestos a **Cuadro de herramientas** y en editores.  
  
 VSPackages según el managed package debe registrar como proporcionar a formatos de Portapapeles personalizados de elementos de **Cuadro de herramientas** , aplicando una instancia de <xref:Microsoft.VisualStudio.Shell.ProvideToolboxFormatAttribute> a la clase que implementa <xref:Microsoft.VisualStudio.Shell.Package>.  
  
 Para obtener más información sobre el registro como proveedor de **Cuadro de herramientas** , vea [Registrar características de compatibilidad del Cuadro de herramientas](../misc/registering-toolbox-support-features.md).  
  
#### Para proporcionar formatos de Portapapeles personalizados y la compatibilidad de arrastrar y colocar con los controles de cuadro de herramientas  
  
1.  Crear una implementación del delegado de <xref:System.Drawing.Design.ToolboxItemCreatorCallback> .  
  
     Esta implementación debe devolver un objeto de <xref:System.Drawing.Design.ToolboxItem> que admita el formato del Portapapeles no estándar.  
  
     Para obtener un ejemplo de un delegado de <xref:System.Drawing.Design.ToolboxItemCreatorCallback> , vea las páginas de referencia de <xref:System.Drawing.Design.ToolboxItem> y de <xref:System.Drawing.Design.ToolboxItemCreatorCallback> .  
  
2.  Coloque esta implementación del delegado de <xref:System.Drawing.Design.ToolboxItemCreatorCallback> a disposición [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] **Cuadro de herramientas** para un cuadro de herramientas no estándar llamando a <xref:System.Drawing.Design.IToolboxService.AddCreator%2A>.  
  
    ```vb#  
    <GuidAttribute("7D91995B-A799-485e-BFC7-C52545DFB5DD")> _   
    <ProvideToolboxFormatAttribute("MyFormat")> _   
    Public Class ItemConfiguration   
        Inherits MSVSIP.Package   
        Public Overloads Overrides Sub Initialize()   
            '"Adding this class as a ToolboxItemCreator");   
            Dim toolbox As IToolboxService = DirectCast(host.GetService(GetType(IToolboxService)), IToolboxService)   
            If toolbox IsNot Nothing Then   
                toolboxCreator = New ToolboxItemCreatorCallback(Me.OnCreateToolboxItem)   
                toolbox.AddCreator(toolboxCreator, "MyFormat", host)   
            End If   
        End Sub   
    End Class  
    ```  
  
    ```c#  
    [GuidAttribute("7D91995B-A799-485e-BFC7-C52545DFB5DD")]  
    [ProvideToolboxFormatAttribute("MyFormat")]  
    public class ItemConfiguration : MSVSIP.Package  
    {  
        public override void Initialize() {   
            /*  
            *  
            */  
            //"Adding this class as a ToolboxItemCreator");  
            IToolboxService toolbox = (IToolboxService)host.GetService(typeof(IToolboxService));  
            if (toolbox != null) {  
                toolboxCreator = new ToolboxItemCreatorCallback(this.OnCreateToolboxItem);  
                toolbox.AddCreator(toolboxCreator, "MyFormat", host);  
            }  
            private ToolboxItem OnCreateToolboxItem(object serializedData, string format) {  
               /*  
                *  
                */  
            }  
        }  
    }  
    ```  
  
### En esta sección  
 [Cómo: admitir la función de arrastrar y colocar en el cuadro de herramientas](../misc/how-to-support-toolbox-drag-and-drop-functionality.md)  
 Describe cómo implementar la compatibilidad de arrastrar y colocar en una vista del documento.  
  
 [Cómo: Proporcionar elementos de Cuadro de herramientas personalizados mediante ensamblados de interoperabilidad](../misc/how-to-provide-custom-toolbox-items-by-using-interop-assemblies.md)  
 Describe la adición de nuevos controles y nuevos elementos ActiveX a [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] **Cuadro de herramientas**.  Estos nuevos elementos pueden tener un formato de Portapapeles estándar o un formato personalizado que admita el paquete VSPackage.  
  
 [Registrar características de compatibilidad del Cuadro de herramientas](../misc/registering-toolbox-support-features.md)  
 Describe cómo registrar un VSPackage como proveedor del cuadro de herramientas.  También habla de admitir o utilizar otras características del cuadro de herramientas.  
  
## Vea también  
 [Extensión del Cuadro de herramientas](../misc/extending-the-toolbox.md)   
 [Tutoriales del cuadro de herramientas](../misc/toolbox-walkthroughs.md)   
 [Registrar características de compatibilidad del Cuadro de herramientas](../misc/registering-toolbox-support-features.md)   
 [Cómo: Proporcionar elementos de Cuadro de herramientas personalizados mediante ensamblados de interoperabilidad](../misc/how-to-provide-custom-toolbox-items-by-using-interop-assemblies.md)   
 [Administración del cuadro de herramientas](../misc/managing-the-toolbox.md)   
 [Cómo: Controlar el Cuadro de herramientas](../Topic/How%20to:%20Control%20the%20Toolbox.md)