---
title: "Tutorial: Carga autom&#225;tica de elementos del cuadro de herramientas | Microsoft Docs"
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
  - "Cuadro de herramientas [Visual Studio SDK], agregar controles mediante reflexión"
  - "reflexión, cuadro de herramientas"
ms.assetid: b03c0d62-3be0-475f-b1d9-725dee993ad6
caps.latest.revision: 56
caps.handback.revision: 56
manager: "douge"
---
# Tutorial: Carga autom&#225;tica de elementos del cuadro de herramientas
Este tutorial muestra cómo un VSPackage administrado puede usar la reflexión para cargar automáticamente todos los elementos <xref:System.Drawing.Design.ToolboxItem> proporcionados por su propio ensamblado.  
  
> [!NOTE]
>  La forma recomendada de agregar controles personalizados al cuadro de herramientas es usar las plantillas del control del cuadro de herramientas que vienen con el SDK de Visual Studio, que incluye compatibilidad con la carga automática. Este tema se conserva por compatibilidad con versiones anteriores, para agregar controles existentes al cuadro de herramientas y para el desarrollo avanzado del cuadro de herramientas.  
>   
>  Para obtener más información sobre cómo crear controles del cuadro de herramientas mediante plantillas, consulte [Cómo: Crear un control Toolbox que use formularios Windows Forms](../misc/how-to-create-a-toolbox-control-that-uses-windows-forms.md) y [Crear un Control de cuadro de herramientas WPF](../extensibility/creating-a-wpf-toolbox-control.md).  
  
 Este tutorial le guía a través de los pasos siguientes:  
  
1.  Agregar y registrar correctamente todos los controles del **cuadro de herramientas** en los objetos de VSPackage mediante <xref:System.ComponentModel.ToolboxItemAttribute>, <xref:System.Drawing.ToolboxBitmapAttribute> y <xref:System.ComponentModel.DisplayNameAttribute>.  
  
2.  Crear los siguientes dos controles y agregar iconos para cada uno al **cuadro de herramientas**:  
  
    -   Agregar un control mediante la clase <xref:System.Drawing.Design.ToolboxItem> predeterminada.  
  
    -   Agregar otro control usando una clase personalizada derivada de la clase <xref:System.Drawing.Design.ToolboxItem>.  
  
3.  Registrar VSPackage como proveedor de objetos <xref:System.Drawing.Design.ToolboxItem> con la clase <xref:Microsoft.VisualStudio.Shell.ProvideToolboxItemsAttribute>.  
  
4.  Usar la reflexión para generar una lista de todos los <xref:System.Drawing.Design.ToolboxItem> objetos que VSPackage proporciona cuando se carga.  
  
5.  Crear un controlador para los eventos <xref:Microsoft.VisualStudio.Shell.Package.ToolboxInitialized> y <xref:Microsoft.VisualStudio.Shell.Package.ToolboxUpgraded>. Esto garantiza que los objetos <xref:System.Drawing.Design.ToolboxItem> del VSPackage se cargan correctamente.  
  
6.  Implementar un comando en VSPackage para forzar la reinicialización del **cuadro de herramientas**.  
  
## Requisitos previos  
 Para seguir este tutorial, debe instalar el SDK de Visual Studio. Para obtener más información, consulta [Información general sobre la extensión de Visual Studio](../Topic/Extending%20Visual%20Studio%20Overview.md).  
  
## Ubicaciones de las plantillas de proyecto del paquete de Visual Studio  
 La plantilla de proyecto del paquete de Visual Studio puede encontrarse en tres ubicaciones diferentes en el cuadro de diálogo **Nuevo proyecto**:  
  
1.  En Extensibilidad de Visual Basic. El lenguaje predeterminado del proyecto es Visual Basic.  
  
2.  En Extensibilidad de C\#. El lenguaje predeterminado del proyecto es C\#.  
  
3.  En otro tipos de extensibilidad del proyecto. El lenguaje predeterminado del proyecto es C\+\+.  
  
## Crear un VSPackage administrado  
  
#### Para crear VSPackage LoadToolboxMembers  
  
1.  Cree un VSPackage denominado `LoadToolboxMembers`. Para obtener más información, consulta [Tutorial: Crear un comando de menú mediante la plantilla de paquete de Visual Studio](../Topic/Walkthrough:%20Creating%20a%20Menu%20Command%20By%20Using%20the%20Visual%20Studio%20Package%20Template.md).  
  
2.  Agregue un comando de menú.  
  
     Denomine el comando `Initialize LoadToolboxMembers VB` para Visual Basic o `Initialize LoadToolboxMembers CS` para Visual C\#.  
  
 Si sigue este tutorial para más de un lenguaje, debe actualizar el proyecto para eliminar la ambigüedad de los ensamblados generados.  
  
#### Para eliminar la ambigüedad de Visual Basic y Visual C\# VSPackages  
  
1.  Para [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]:  
  
    -   En el **Explorador de soluciones**, abra las propiedades del proyecto y seleccione la pestaña **Aplicación**.  
  
         Cambie el nombre de ensamblado a `LoadToolboxMembersVB` y cambie el espacio de nombres predeterminado a `Company.LoadToolboxMembersVB`.  
  
2.  Para [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)]:  
  
    1.  En el **Explorador de soluciones**, abra las propiedades del proyecto y seleccione la pestaña **Aplicación**.  
  
         Cambie el nombre de ensamblado a `LoadToolboxMembersCS` y cambie el espacio de nombres predeterminado a `Company.LoadToolboxMembersCS`.  
  
    2.  Abra la clase LoadToolboxMembersPackage en el editor de código.  
  
         Para usar las herramientas de refactorización para cambiar el nombre del espacio de nombres existente, haga clic en el nombre del espacio de nombres existente, `LoadToolboxMembers`, seleccione **Refactorizar** y, a continuación, haga clic en **Cambiar nombre**. Cambie el nombre a `LoadToolboxMembersCS`.  
  
3.  Guarde todos los cambios.  
  
#### Para agregar referencias complementarias  
  
1.  En el proyecto LoadToolboxMembers, agregue una referencia al componente <xref:System.Drawing.Design?displayProperty=fullName> de .NET Framework, de la forma siguiente:  
  
    1.  En el **Explorador de soluciones**, haga clic con el botón secundario en el proyecto LoadToolboxMembers y seleccione **Agregar**, **Referencia**.  
  
    2.  En la pestaña **.NET** del cuadro de diálogo **Referencias**, haga doble clic en **System.Drawing.Design**.  
  
2.  En Visual Basic, agregue los siguientes espacios de nombres a la lista de espacios de nombres importada en el proyecto:  
  
    -   Company.LoadToolboxMembersVB  
  
    -   Sistema  
  
    -   System.ComponentModel  
  
    -   System.Drawing  
  
    -   System.Windows.Forms  
  
#### Para probar código generado  
  
1.  Compile e inicie el VSPackage en el subárbol experimental de Visual Studio.  
  
2.  En el menú **Herramientas**, haga clic en **Inicializar LoadToolboxMembers VB** o en **Inicializar LoadToolboxMembers CS**.  
  
     Se abrirá un cuadro de mensaje que contiene el texto que indica que se ha llamado al controlador de elementos de menú del paquete.  
  
3.  Cierre la versión experimental de [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)].  
  
## Crear un control Toolbox  
 En esta sección, creará y registrará un control de usuario, `Control1`, que declara un valor predeterminado **Toolbox** asociado. Para obtener más información sobre cómo crear controles de formulario Windows Forms y la clase <xref:System.Drawing.Design.ToolboxItem>, consulte [Desarrollar controles de formularios Windows Forms en tiempo de diseño](../Topic/Developing%20Windows%20Forms%20Controls%20at%20Design%20Time.md).  
  
#### Para crear un control Toolbox que se utilizará con el valor predeterminado ToolboxItem  
  
1.  En el **Explorador de soluciones**, agregue un objeto <xref:System.Windows.Forms.UserControl> al proyecto LoadToolboxMembers, de la forma siguiente:  
  
    1.  En el **Explorador de soluciones**, haga clic con el botón secundario en el proyecto **LoadToolboxMembers**, seleccione **Agregar** y haga clic en **User Control**.  
  
    2.  En el cuadro de diálogo **Agregar nuevo elemento**, cambie el nombre a `Control1.vb` para [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] o a `Control1.cs` para [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)].  
  
         Para obtener más información sobre cómo agregar nuevos elementos a un proyecto, vea [NIB: Cómo: Agregar elementos de proyecto nuevos](http://msdn.microsoft.com/es-es/63d3e16b-de6e-4bb5-a0e3-ecec762201ce).  
  
     El nuevo control se abre en la vista Diseño.  
  
2.  Desde el **cuadro de herramientas**, arrastre un control de **botón** \(ubicado en la categoría  **Controles comunes**\) al diseñador.  
  
3.  Haga doble clic en el botón que acaba de crear. Esto genera un controlador de eventos para el evento <xref:System.Windows.Forms.Control.Click> del botón. Actualice el controlador de eventos usando el siguiente código:  
  
     [!code-cs[LoadToolboxMembers#01](../misc/codesnippet/CSharp/walkthrough-autoloading-toolbox-items_1.cs)]
     [!code-vb[LoadToolboxMembers#01](../misc/codesnippet/VisualBasic/walkthrough-autoloading-toolbox-items_1.vb)]  
  
4.  Modifique el constructor del control para establecer el texto del botón después de que se llame al método `InitializeComponent`:  
  
     [!code-cs[LoadToolboxMembers#02](../misc/codesnippet/CSharp/walkthrough-autoloading-toolbox-items_2.cs)]
     [!code-vb[LoadToolboxMembers#02](../misc/codesnippet/VisualBasic/walkthrough-autoloading-toolbox-items_2.vb)]  
  
5.  Agregue atributos al archivo para permitir que el VSPackage consulte la clase <xref:System.Drawing.Design.ToolboxItem> proporcionada:  
  
     [!code-cs[LoadToolboxMembers#03](../misc/codesnippet/CSharp/walkthrough-autoloading-toolbox-items_3.cs)]
     [!code-vb[LoadToolboxMembers#03](../misc/codesnippet/VisualBasic/walkthrough-autoloading-toolbox-items_3.vb)]  
  
6.  Guarde el archivo.  
  
 En el siguiente procedimiento, creará y registrará un segundo control de usuario, `Control2`, y un elemento personalizado asociado del **cuadro de herramientas**, `Control2_ToolboxItem`, que se deriva de la clase <xref:System.Drawing.Design.ToolboxItem>.  
  
#### Para crear un control Toolbox para usar una clase derivada personalizada de ToolboxItem  
  
1.  Cree un segundo control de usuario denominado `Control2`. Haga doble clic en el formulario para que aparezca el archivo de código.  
  
2.  Agregue `System.Drawing.Design` y `System.Globalization` a los espacios de nombres que se usan en la clase.  
  
     [!code-cs[LoadToolboxMembers#04](../misc/codesnippet/CSharp/walkthrough-autoloading-toolbox-items_4.cs)]
     [!code-vb[LoadToolboxMembers#04](../misc/codesnippet/VisualBasic/walkthrough-autoloading-toolbox-items_4.vb)]  
  
3.  Agregue un botón y un controlador de eventos de clic de botón, y actualice el constructor del control, al igual que actualiza el primer control.  
  
4.  Agregue los atributos <xref:System.ComponentModel.DisplayNameAttribute>, <xref:System.ComponentModel.DescriptionAttribute>, <xref:System.ComponentModel.ToolboxItemAttribute> y <xref:System.Drawing.ToolboxBitmapAttribute> al archivo.  
  
     Estos atributos permiten que el paquete VSPackage consulte una clase <xref:System.Drawing.Design.ToolboxItem>.  
  
     Para obtener más información y ejemplos sobre cómo escribir objetos <xref:System.Drawing.Design.ToolboxItem> personalizados, vea la explicación en la página de referencia de <xref:System.Drawing.Design.ToolboxItem>.  
  
     Junto con los cambios anteriores, la segunda clase del control debe ser similar a la del código siguiente. El símbolo `Control2_ToolboxMenu` quedará sin definir hasta después del siguiente paso.  
  
     [!code-cs[LoadToolboxMembers#05](../misc/codesnippet/CSharp/walkthrough-autoloading-toolbox-items_5.cs)]
     [!code-vb[LoadToolboxMembers#05](../misc/codesnippet/VisualBasic/walkthrough-autoloading-toolbox-items_5.vb)]  
  
5.  Cree una clase denominada `Control2_ToolboxItem`. Este <xref:System.Drawing.Design.ToolboxItem> se crea para el segundo control y se agrega al **cuadro de herramientas**. La clase debe tener `SerializableAttribute` aplicado.  
  
     [!code-cs[LoadToolboxMembers#06](../misc/codesnippet/CSharp/walkthrough-autoloading-toolbox-items_6.cs)]
     [!code-vb[LoadToolboxMembers#06](../misc/codesnippet/VisualBasic/walkthrough-autoloading-toolbox-items_6.vb)]  
  
6.  Guarde el archivo.  
  
## Incrustar iconos de mapa de bits  
 Las dos instancias de <xref:System.Drawing.ToolboxBitmapAttribute> usadas anteriormente indican que el proyecto representa los dos controles mediante los siguientes iconos:  
  
-   `Control1.bmp`, ubicado en el espacio de nombres que contiene el primer control.  
  
-   `Control2.bmp`, ubicado en el espacio de nombres que contiene el segundo control.  
  
#### Para incrustar iconos de mapa de bits para el elemento ToolboxItem  
  
1.  Agregue dos mapas de bits nuevos al proyecto de la forma siguiente:  
  
    1.  Haga clic con el botón secundario en el proyecto `LoadToolboxMembers`.  
  
    2.  Seleccione **Agregar** y haga clic en **Nuevo elemento**.  
  
    3.  En el cuadro de diálogo **Agregar nuevo elemento**, seleccione **Archivo de mapa de bits** y asigne al archivo el nombre `Control1.bmp`.  
  
    4.  Repita estos pasos para el segundo mapa de bits y asígnele el nombre `Control2.bmp`.  
  
         Esto abre cada mapa de bits en el editor de mapa de bits [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
2.  Establezca el tamaño de cada icono en 16 x 16, de la manera siguiente:  
  
    1.  Para cada mapa de bits, haga clic en la ventana **Propiedades**, en el menú **Ver**.  
  
    2.  En la ventana **Propiedades**, establezca el **Alto** y el **Ancho** en 16.  
  
3.  Use el editor de mapa de bits en [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] para crear una imagen para cada icono.  
  
4.  En el **Explorador de soluciones**, haga clic en cada archivo del mapa de bits y, en la ventana **Propiedades**, establezca la propiedad **Acción de compilación** en **Recurso incrustado**.  
  
5.  Guarde todos los archivos abiertos.  
  
## Modificar la implementación de VSPackage  
 La implementación predeterminada de VSPackage debe modificarse para realizar las siguientes acciones:  
  
-   Registrar la compatibilidad para ser un proveedor de elementos del **cuadro de herramientas**.  
  
-   Obtener una lista de objetos <xref:System.Drawing.Design.ToolboxItem> que admita el VSPackage.  
  
-   Cargar el objeto <xref:System.Drawing.Design.ToolboxItem> en el **cuadro de herramientas** de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] cuando se controlan eventos <xref:Microsoft.VisualStudio.Shell.Package.ToolboxInitialized> y <xref:Microsoft.VisualStudio.Shell.Package.ToolboxUpgraded>.  
  
 El siguiente procedimiento muestra cómo modificar la implementación del paquete.  
  
#### Para modificar la implementación del paquete para que sea un proveedor de elementos del cuadro de herramientas para el VSPackage  
  
1.  Abra el archivo LoadToolboxMembersPackage.cs o LoadToolboxMembersPackage.vb en el editor de código.  
  
2.  Modifique la declaración de la clase `LoadToolboxMembersPackage`, que es la implementación de la clase <xref:Microsoft.VisualStudio.Shell.Package> en la solución, de la forma siguiente:  
  
    1.  Agregue las siguientes directivas de espacio de nombres al archivo de clase `LoadToolboxMembersPackage`.  
  
         [!code-cs[LoadToolboxMembers#07](../misc/codesnippet/CSharp/walkthrough-autoloading-toolbox-items_7.cs)]
         [!code-vb[LoadToolboxMembers#07](../misc/codesnippet/VisualBasic/walkthrough-autoloading-toolbox-items_7.vb)]  
  
    2.  Registre el VSPackage como una clase <xref:System.Drawing.Design.ToolboxItem> agregando una instancia de <xref:Microsoft.VisualStudio.Shell.ProvideToolboxItemsAttribute>.  
  
        > [!NOTE]
        >  El único argumento de <xref:Microsoft.VisualStudio.Shell.ProvideToolboxItemsAttribute> es la versión de <xref:System.Drawing.Design.ToolboxItem> proporcionada por el VSPackage. Al cambiar este valor, se fuerza el IDE para cargar VSPackage incluso si tiene una versión anteriormente almacenada en caché de la clase <xref:System.Drawing.Design.ToolboxItem>.  
  
    3.  Agregue los dos campos `private` nuevos siguientes a la clase `LoadToolboxMembersPackage`:  
  
         Un miembro de <xref:System.Collections.ArrayList>, denominado `ToolboxItemList`, para mantener una lista de los objetos <xref:System.Drawing.Design.ToolboxItem> que administra la clase `LoadToolboxMembersPackage`.  
  
         Un <xref:System.String>, denominado `CategoryTab`, que contiene la categoría **Toolbox** o la pestaña que se usa para mantener los objetos de <xref:System.Drawing.Design.ToolboxItem> administrados por la clase `LoadToolboxMembersPackage`.  
  
     El resultado de esta modificación es similar al código siguiente:  
  
     [!code-cs[LoadToolboxMembers#08](../misc/codesnippet/CSharp/walkthrough-autoloading-toolbox-items_8.cs)]
     [!code-vb[LoadToolboxMembers#08](../misc/codesnippet/VisualBasic/walkthrough-autoloading-toolbox-items_8.vb)]  
  
3.  Expanda la región de los miembros del paquete para modificar el método `Initialize` para realizar las siguientes acciones:  
  
    -   Para [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)], subscríbase a los eventos <xref:Microsoft.VisualStudio.Shell.Package.ToolboxInitialized> y <xref:Microsoft.VisualStudio.Shell.Package.ToolboxUpgraded>.  
  
    -   Llame al método `CreateItemList` para rellenar el objeto `ToolboxItemList` de <xref:System.Collections.ArrayList>. El `ToolboxItemList` contendrá una lista de todos los elementos que administra `LoadToolboxMembersPackage`.  
  
     [!code-cs[LoadToolboxMembers#09](../misc/codesnippet/CSharp/walkthrough-autoloading-toolbox-items_9.cs)]
     [!code-vb[LoadToolboxMembers#09](../misc/codesnippet/VisualBasic/walkthrough-autoloading-toolbox-items_9.vb)]  
  
4.  Agregue dos métodos, `CreateItemList` y `CreateToolboxItem`, para construir, mediante metadatos, instancias de los objetos <xref:System.Drawing.Design.ToolboxItem> que están disponibles en el ensamblado `LoadToolboxMembers`, como sigue:  
  
     [!code-cs[LoadToolboxMembers#10](../misc/codesnippet/CSharp/walkthrough-autoloading-toolbox-items_10.cs)]
     [!code-vb[LoadToolboxMembers#10](../misc/codesnippet/VisualBasic/walkthrough-autoloading-toolbox-items_10.vb)]  
  
5.  Implemente el método `OnRefreshToolbox` para controlar los eventos <xref:Microsoft.VisualStudio.Shell.Package.ToolboxInitialized> y <xref:Microsoft.VisualStudio.Shell.Package.ToolboxUpgraded>.  
  
     El método `OnRefreshToolbox` usa la lista de objetos <xref:System.Drawing.Design.ToolboxItem> que se encuentra en el miembro `ToolboxItemList` de la clase `LoadToolboxMembersPackage`. También hace lo siguiente:  
  
    -   Quita todos los objetos <xref:System.Drawing.Design.ToolboxItem> que ya están presentes en la categoría Toolbox definida por la variable `CategoryTab`.  
  
    -   Agrega nuevas instancias de todos los objetos <xref:System.Drawing.Design.ToolboxItem> que aparecen en `ToolboxItemList` en la pestaña de categoría del VSProject.  
  
    -   Establece la pestaña activa **Cuadro de herramientas** en la pestaña de categoría del VSProject.  
  
     [!code-cs[LoadToolboxMembers#11](../misc/codesnippet/CSharp/walkthrough-autoloading-toolbox-items_11.cs)]
     [!code-vb[LoadToolboxMembers#11](../misc/codesnippet/VisualBasic/walkthrough-autoloading-toolbox-items_11.vb)]  
  
    > [!NOTE]
    >  Como ejercicio, se podría desarrollar un mecanismo para comprobar la versión de VSPackage o los elementos, y actualizar solo si ha cambiado la versión de VSPackage, o si la versión de <xref:System.Drawing.Design.ToolboxItem> ha cambiado.  
  
## Inicializar el cuadro de herramientas  
  
#### Implementar un comando para inicializar el cuadro de herramientas  
  
-   Cambie el método de controlador de comando del elemento de menú, `MenuItemCallBack`, de la siguiente forma:  
  
    1.  Reemplace la implementación existente de `MenuItemCallBack` por el código siguiente:  
  
         [!code-cs[LoadToolboxMembers#12](../misc/codesnippet/CSharp/walkthrough-autoloading-toolbox-items_12.cs)]
         [!code-vb[LoadToolboxMembers#12](../misc/codesnippet/VisualBasic/walkthrough-autoloading-toolbox-items_12.vb)]  
  
## Compilación y ejecución de la solución  
 Puede usar el producto de este tutorial mediante una instancia de Visual Studio que se está ejecutando en el subárbol experimental.  
  
#### Para ejecutar este tutorial  
  
1.  En Visual Studio, en el menú **Compilar**, haga clic en **Recompilar solución**.  
  
2.  Presione F5 para iniciar una segunda instancia de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] en el subárbol del registro experimental.  
  
     Para más información sobre cómo usar el subárbol experimental, consulte [La instancia Experimental](../extensibility/the-experimental-instance.md).  
  
3.  Haga clic en el menú **Herramientas**.  
  
     Un comando llamado **Inicializar LoadToolboxMembers VB** o **Inicializar LoadToolboxMembers CS** debe aparecer en la parte superior del menú, junto con un icono que tiene el número 1.  
  
4.  Cree una nueva aplicación de Windows Forms [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] o [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)].  
  
     Debe aparecer un diseñador basado en <xref:System.Windows.Forms.Form>.  
  
5.  Arrastre uno de los nuevos controles o los dos en las categorías **Tutorial LoadToolboxMembers VB** o **Tutorial LoadToolboxMembers CS** del **Cuadro de herramientas** al formulario en el diseñador.  
  
    > [!NOTE]
    >  Si el **Cuadro de herramientas** no se abre, vaya al menú **Ver** y haga clic en **Cuadro de herramientas**. Si la pestaña de la categoría de VSPackage no aparece en el **Cuadro de herramientas**, vuelva a inicializar el **Cuadro de herramientas** haciendo clic en **Inicializar LoadToolboxMembers VB** o en **Inicializar LoadToolboxMembers CS** en el menú **Herramientas**.  
  
6.  Compile la aplicación de Windows haciendo clic en **Volver a compilar solución** en el menú **Compilar**.  
  
7.  Ejecute la aplicación haciendo clic en **Iniciar** o en **Iniciar con depuración** en el menú **Depurar**.  
  
8.  Cuando se ejecute la aplicación, haga clic en uno de los controles que ha agregado a la aplicación.  
  
     Aparecerá un cuadro de mensaje, que mostrará `"Hello world from Company.LoadToolboxMembers.Control1"` o  `"Hello world from Company.LoadToolboxMembers.Control2"`.  
  
## Análisis de la implementación  
  
### Crear controles del cuadro de herramientas  
 Los atributos asignados a `Control1` y `Control2` los usa el método `CreateItemList` cuando consulta el `Assembly` para los controles del **Cuadro de herramientas** disponibles.  
  
-   <xref:System.ComponentModel.ToolboxItemAttribute> realiza las dos funciones siguientes:  
  
    -   La asignación de <xref:System.ComponentModel.ToolboxItemAttribute> a `Control1` y `Control2`, que indica que cada uno es un control del cuadro de herramientas.  
  
    -   El argumento para el constructor <xref:System.ComponentModel.ToolboxItemAttribute>, que indica si se usa el valor predeterminado <xref:System.Drawing.Design.ToolboxItem> o una clase personalizada derivada de <xref:System.Drawing.Design.ToolboxItem> cuando el control se agrega al **Cuadro de herramientas**.  
  
         La instancia de <xref:System.ComponentModel.ToolboxItemAttribute> que se asigna a `Control1` se crea mediante un argumento de `true`, lo que indica que usa una clase <xref:System.Drawing.Design.ToolboxItem> predeterminada cuando se agrega al **Cuadro de herramientas**.  
  
         La instancia de <xref:System.ComponentModel.ToolboxItemAttribute> que se asigna a `Control2` se crea mediante el <xref:System.Type> de una clase que se deriva de <xref:System.Drawing.Design.ToolboxItem>, `Control2_ToolboxItem`.  
  
-   La clase <xref:System.Drawing.ToolboxBitmapAttribute> especifica los mapas de bits que usa el entorno para identificar los controles.  
  
     Al incrustar un mapa de bits en un ensamblado estableciendo su propiedad **Acción de compilación** como **Recurso incrustado**, se pone el mapa de bits en el espacio de nombres del ensamblado. Por lo tanto, se puede hacer referencia a `Control1.bmp` como `Company.LoadToolboxMembers.Control1.bmp`.  
  
     <xref:System.Drawing.ToolboxBitmapAttribute> admite un constructor que toma esta ruta de acceso completa como argumento. Por ejemplo, una clase <xref:System.Drawing.ToolboxBitmapAttribute> podría aplicarse a `Control1` usando `[ToolboxBitmap("Company.LoadToolboxMembers.Control1.bmp")]`.  
  
     Para admitir la flexibilidad, este tutorial usa un constructor que toma una clase <xref:System.Type> como el primer argumento para el constructor <xref:System.Drawing.ToolboxBitmapAttribute>. El espacio de nombres que se usa para identificar el archivo de mapa de bits se obtiene de <xref:System.Type> y se inserta delante del nombre base del mapa de bits.  
  
     Dado que el objeto <xref:System.Type> que implementa <xref:Microsoft.VisualStudio.Shell.Package>, `LoadToolboxMembers` está en el espacio de nombres `Company.LoadToolboxMembers`, `[ToolboxBitmap(typeof(Control1), "Control1.bmp")]` es equivalente a `[ToolboxBitmap("Company.LoadToolboxMembers.Control1.bmp")]`.  
  
-   <xref:System.ComponentModel.DisplayNameAttribute> especifica el nombre del control en el **Cuadro de herramientas**.  
  
### Registrar un proveedor de control del Cuadro de herramientas  
 Aplicar la clase <xref:Microsoft.VisualStudio.Shell.ProvideToolboxItemsAttribute> a la clase que implementa <xref:Microsoft.VisualStudio.Shell.Package> afecta a la configuración del registro del VSPackage resultante. Para obtener más información sobre la entrada del Registro para un proveedor de <xref:System.Drawing.Design.ToolboxItem>, consulte [Registrar características de compatibilidad del Cuadro de herramientas](../misc/registering-toolbox-support-features.md).  
  
 El entorno [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] usa el argumento de la versión para el constructor <xref:Microsoft.VisualStudio.Shell.ProvideToolboxItemsAttribute> para administrar el almacenamiento en caché de VSPackages que proporcionan los elementos al **Cuadro de herramientas**. Una vez que un VSPackage se ha cargado para proporcionar elementos del **Cuadro de herramientas**, se usa una versión en caché de VSPackage hasta que cambie la versión registrada del proveedor. Por lo tanto, si desea modificar el producto de este tutorial después de la compilación, asegúrese de cambiar el argumento de la versión del constructor <xref:Microsoft.VisualStudio.Shell.ProvideToolboxItemsAttribute> que se aplica a `AddToolboxItem`. Por ejemplo, `[ProvideToolboxItems(1)]` debe cambiarse a `[ProvideToolboxItems(2)]`. Si no se cambia la versión, el entorno [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] no carga las modificaciones que han hecho.  
  
 En este tutorial, el VSPackage está configurado para proporcionar solo los controles del **Cuadro de herramientas** que admiten el formato del Portapapeles predeterminado. Para obtener una lista de formatos de Portapapeles predeterminados, consulte [Extensión del Cuadro de herramientas](../misc/extending-the-toolbox.md). Si desea admitir otros formatos de Portapapeles o decide no admitir un formato predeterminado, aplique el atributo <xref:Microsoft.VisualStudio.Shell.ProvideToolboxFormatAttribute> a la clase `LoadToolboxMembersPackage`. Para obtener más información sobre cómo registrar un proveedor de controles del **Cuadro de herramientas**, vea [Desarrollo avanzado de controles del cuadro de herramientas](../misc/advanced-toolbox-control-development.md).  
  
### Agregar controles al Cuadro de herramientas  
 La funcionalidad de `CreateItemList` emula lo que está disponible en <xref:System.Drawing.Design.ToolboxService.System%23Drawing%23Design%23IToolboxService%23GetToolboxItems%2A>.  
  
 El método `CreateItemList` examina solo objetos <xref:System.Type> no abstractos que implementan las interfaces de <xref:System.ComponentModel.IComponent>.  
  
## Pasos siguientes  
 Usar <xref:System.Drawing.Design.ToolboxService.System%23Drawing%23Design%23IToolboxService%23GetToolboxItems%2A> en lugar de `CreateItemList` haría que el producto de este tutorial fuera más sólido.  
  
 También podría modificar `CreateItemList` y usar <xref:Microsoft.VisualStudio.Shell.Package.ParseToolboxResource%2A> para cargar los controles en el **Cuadro de herramientas** basándose en una lista de texto insertada en el ensamblado `LoadToolboxMembers`.  
  
## Vea también  
 [Extensión del Cuadro de herramientas](../misc/extending-the-toolbox.md)   
 [Registrar características de compatibilidad del Cuadro de herramientas](../misc/registering-toolbox-support-features.md)   
 [Desarrollo avanzado de controles del cuadro de herramientas](../misc/advanced-toolbox-control-development.md)   
 [Tutoriales del cuadro de herramientas](../misc/toolbox-walkthroughs.md)