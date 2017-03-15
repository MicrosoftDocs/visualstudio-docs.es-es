---
title: "Tutorial: Personalizar la configuraci&#243;n del elemento de cuadro de herramientas din&#225;micamente | Microsoft Docs"
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
  - "Cuadro de herramientas [Visual Studio SDK], agregar controles (formatos personalizados)"
ms.assetid: 761f44b7-c748-4ff5-921f-fc4f71784b0e
caps.latest.revision: 45
caps.handback.revision: 45
manager: "douge"
---
# Tutorial: Personalizar la configuraci&#243;n del elemento de cuadro de herramientas din&#225;micamente
Este tutorial muestra cómo un VSPackage administrado puede proporcionar compatibilidad con la configuración dinámica para los objetos <xref:System.Drawing.Design.ToolboxItem>.  
  
> [!NOTE]
>  La forma más sencilla de agregar controles personalizados al cuadro de herramientas es usar las plantillas del control del cuadro de herramientas que se incluyen en el SDK de Visual Studio. Este tema está relacionado con el desarrollo avanzado del cuadro de herramientas.  
>   
>  Para obtener más información sobre cómo crear controles del cuadro de herramientas mediante plantillas, consulte [Cómo: Crear un control Toolbox que use formularios Windows Forms](../misc/how-to-create-a-toolbox-control-that-uses-windows-forms.md) y [Crear un Control de cuadro de herramientas WPF](../extensibility/creating-a-wpf-toolbox-control.md).  
  
 Este tutorial le guía a través de los pasos siguientes:  
  
1.  Agregar y registrar correctamente todos los controles del **cuadro de herramientas** en los objetos de VSPackage mediante <xref:System.ComponentModel.ToolboxItemAttribute> y <xref:System.Drawing.ToolboxBitmapAttribute>.  
  
2.  Crear los dos controles siguientes y agregar iconos para cada uno al **cuadro de herramientas**:  
  
    -   Un control que declara un objeto <xref:System.Drawing.Design.ToolboxItem> predeterminado asociado.  
  
    -   Un control que declara un elemento del **cuadro de herramientas** personalizado asociado derivado de la clase <xref:System.Drawing.Design.ToolboxItem>.  
  
3.  Escribir una implementación de <xref:Microsoft.VisualStudio.Shell.IConfigureToolboxItem> y registrarla haciendo lo siguiente:  
  
    1.  Definir una clase de filtro que se deriva de la clase <xref:Microsoft.VisualStudio.Shell.IConfigureToolboxItem> y especificar las instancias de <xref:System.Drawing.Design.ToolboxItem> en las que actuará esta implementación.  
  
    2.  Aplicar un objeto <xref:Microsoft.VisualStudio.Shell.ProvideToolboxItemConfigurationAttribute>, que hace referencia la clase de filtro, a la clase que implementa la clase <xref:Microsoft.VisualStudio.Shell.Package> para VSPackage.  
  
4.  Registrar el VSPackage como un proveedor de objetos <xref:System.Drawing.Design.ToolboxItem> aplicando el <xref:Microsoft.VisualStudio.Shell.ProvideToolboxItemsAttribute> a la clase que implementa la clase <xref:Microsoft.VisualStudio.Shell.Package> de VSPackage.  
  
5.  Durante la carga del paquete, usar la reflexión para generar una lista de todos los objetos <xref:System.Drawing.Design.ToolboxItem> que proporciona VSPackage.  
  
6.  Crear un controlador para los eventos <xref:Microsoft.VisualStudio.Shell.Package.ToolboxInitialized> y <xref:Microsoft.VisualStudio.Shell.Package.ToolboxUpgraded>. Esto garantiza que los objetos <xref:System.Drawing.Design.ToolboxItem> del VSPackage se cargan correctamente.  
  
7.  Implementar un comando en VSPackage para forzar la reinicialización del **cuadro de herramientas**.  
  
## Requisitos previos  
 Para seguir este tutorial, debe instalar el SDK de Visual Studio. Para obtener más información, consulta [Visual Studio SDK](../extensibility/visual-studio-sdk.md).  
  
## Ubicaciones de la plantilla de proyecto de paquete de Visual Studio  
 La plantilla de proyecto de paquete de Visual Studio puede encontrarse en tres ubicaciones diferentes en el cuadro de diálogo **Nuevo proyecto**:  
  
1.  En Extensibilidad de Visual Basic. El lenguaje predeterminado del proyecto es Visual Basic.  
  
2.  En Extensibilidad de C\#. El lenguaje predeterminado del proyecto es C\#.  
  
3.  En Extensibilidad de Otros tipos de proyectos. El lenguaje predeterminado del proyecto es C\+\+.  
  
## Crear un VSPackage administrado  
 Complete los procedimientos siguientes para crear un VSPackage administrado.  
  
#### Para crear un VSPackage administrado para proporcionar elementos de cuadro de herramientas  
  
1.  Cree un VSPackage denominado `ItemConfiguration`. Para obtener más información, consulta [Tutorial: Crear un comando de menú mediante la plantilla de paquete de Visual Studio](../Topic/Walkthrough:%20Creating%20a%20Menu%20Command%20By%20Using%20the%20Visual%20Studio%20Package%20Template.md).  
  
2.  En la plantilla del **paquete de Visual Studio**, agregue un comando de menú.  
  
     Denomine el comando `Initialize ItemConfigurationVB` para Visual Basic o `Initialize ItemConfigurationCS` para Visual C\#.  
  
3.  En [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)], agregue los siguientes espacios de nombres a la lista de espacios de nombres importada en el proyecto generado:  
  
    -   Company.ItemConfiguration  
  
    -   Sistema  
  
    -   System.ComponentModel  
  
    -   System.Drawing  
  
    -   System.Windows.Forms  
  
4.  Agregue una referencia al componente <xref:System.Drawing.Design?displayProperty=fullName> de .NET Framework.  
  
 Si sigue este tutorial para más de un lenguaje, debe actualizar el proyecto para eliminar la ambigüedad de los ensamblados generados.  
  
#### Para eliminar la ambigüedad de Visual Basic y Visual C\# VSPackages  
  
1.  Para [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]:  
  
    1.  Abra las propiedades del proyecto y seleccione la pestaña **Aplicación**.  
  
         Cambie el nombre de ensamblado a `ItemConfigurationVB` y cambie el espacio de nombres predeterminado a `Company.ItemConfigurationVB`.  
  
    2.  Seleccione la pestaña **Referencias**.  
  
         Actualice la lista de espacios de nombres importados.  
  
         Quite Company.ItemConfiguration.  
  
         Agregue Company.ItemConfigurationVB.  
  
2.  Para [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)]:  
  
    1.  Abra las propiedades del proyecto y seleccione la pestaña **Aplicación**.  
  
         Cambie el nombre de ensamblado a `ItemConfigurationCS` y cambie el espacio de nombres predeterminado a `Company.ItemConfigurationCS`.  
  
    2.  Abra la clase ItemConfigurationPackage en el editor de código.  
  
         Para usar las herramientas de refactorización para cambiar el nombre del espacio de nombres existente, haga clic en el nombre del espacio de nombres existente, `ItemConfiguration`, seleccione **Refactorizar** y, a continuación, haga clic en **Cambiar nombre**. Cambie el nombre a `ItemConfigurationCS`.  
  
3.  Guarde todos los cambios.  
  
#### Para probar código generado  
  
1.  Compile e inicie el VSPackage en el subárbol experimental de Visual Studio.  
  
2.  En el menú **Herramientas**, haga clic en **Inicializar configuración de elementos en VB** o **Inicializar configuración de elementos en CS**.  
  
     Al hacer esto, se abrirá un cuadro de mensaje que contiene el texto que indica que se ha llamado al controlador de elementos de menú del paquete.  
  
3.  Cierre la versión experimental de [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)].  
  
## Crear controles del cuadro de herramientas  
 En esta sección, creará y registrará un control de usuario, `Control1`, que declara un valor predeterminado **Toolbox** asociado. También creará y registrará un segundo control de usuario, `Control2`, y un elemento personalizado asociado del **cuadro de herramientas**, `Control2_ToolboxItem`, que se deriva de la clase <xref:System.Drawing.Design.ToolboxItem>. Para obtener más información sobre cómo crear controles Windows Forms y clases <xref:System.Drawing.Design.ToolboxItem>, consulte [Desarrollar controles de formularios Windows Forms en tiempo de diseño](../Topic/Developing%20Windows%20Forms%20Controls%20at%20Design%20Time.md).  
  
#### Para crear elementos de cuadro de herramientas personalizados y predeterminados  
  
1.  Siga las instrucciones de [Tutorial: Carga automática de elementos del cuadro de herramientas](../misc/walkthrough-autoloading-toolbox-items.md) para crear un elemento del **Cuadro de herramientas** predeterminado y un elemento del **Cuadro de herramientas** personalizado, como se indica a continuación.  
  
    1.  Complete el procedimiento "Para crear un control **Toolbox** que se utilizará con el valor predeterminado ToolboxItem". Actualice el valor de <xref:System.ComponentModel.DescriptionAttribute> para que haga referencia a este proyecto.  
  
         El código resultante de la clase `Control1` debe ser similar al código siguiente.  
  
         [!code-cs[DynamicToolboxMembers#01](../misc/codesnippet/CSharp/walkthrough-customizing-toolbox-item-configuration-dynamically_1.cs)]
         [!code-vb[DynamicToolboxMembers#01](../misc/codesnippet/VisualBasic/walkthrough-customizing-toolbox-item-configuration-dynamically_1.vb)]  
  
    2.  Complete el procedimiento "Para crear un control **Toolbox** para usar una clase derivada personalizada de ToolboxItem". Actualice el valor de <xref:System.ComponentModel.DescriptionAttribute> para que haga referencia a este proyecto.  
  
         El código resultante de las clases `Control2` y `Control2_ToolboxItem` debe ser similar al código siguiente.  
  
         [!code-vb[DynamicToolboxMembers#02](../misc/codesnippet/VisualBasic/walkthrough-customizing-toolbox-item-configuration-dynamically_2.vb)]
         [!code-cs[DynamicToolboxMembers#02](../misc/codesnippet/CSharp/walkthrough-customizing-toolbox-item-configuration-dynamically_2.cs)]  
  
2.  Guarde los archivos.  
  
## Incrustar iconos de mapa de bits  
 El atributo <xref:System.Drawing.ToolboxBitmapAttribute> que se aplica a cada control especifica qué icono se debe asociar a ese control. Cree los mapas de bits para ambos controles y asígneles los siguientes nombres:  
  
-   `Control1.bmp`, para la clase `Control1`.  
  
-   `Control2.bmp`, para la clase `Control2`.  
  
#### Para incrustar un icono de mapa de bits para un elemento del cuadro de herramientas  
  
1.  Agregue un nuevo mapa de bits al proyecto de la forma siguiente:  
  
    1.  En el **Explorador de soluciones**, haga clic con el botón derecho en el proyecto VSPackage, **Agregar** y después haga clic en **Nuevo elemento**.  
  
    2.  En el cuadro de diálogo **Agregar nuevo elemento**, seleccione **Archivo de mapa de bits** y especifique el nombre del mapa de bits.  
  
2.  Use el editor de mapa de bits para crear un icono de 16x16 de la forma siguiente:  
  
    1.  En el menú **Ver**, haga clic en la **Ventana Propiedades**.  
  
    2.  En la ventana **Propiedades**, establezca el **Alto** y el **Ancho** en 16.  
  
    3.  Use el editor para crear la imagen del icono.  
  
3.  En el **Explorador de soluciones**, haga clic con el botón secundario en el elemento del mapa de bits y seleccione **Propiedades**.  
  
4.  Establezca la propiedad **Acción de compilación** en **Recurso incrustado**.  
  
5.  Guarde todos los archivos abiertos.  
  
## Agregar un proveedor de configuración dinámica de cuadro de herramientas  
 En esta sección, creará y registrará una clase que implementa la interfaz <xref:Microsoft.VisualStudio.Shell.IConfigureToolboxItem>. El entorno de desarrollo integrado \(IDE\) de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] crea y usa esta clase para configurar los controles del **Cuadro de herramientas**.  
  
> [!NOTE]
>  Dado que el entorno de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] crea una instancia de la implementación de <xref:Microsoft.VisualStudio.Shell.IConfigureToolboxItem>, no implemente la interfaz <xref:Microsoft.VisualStudio.Shell.IConfigureToolboxItem> en la clase que implementa <xref:Microsoft.VisualStudio.Shell.Package> para un VSPackage.  
  
#### Para crear y registrar un objeto de configuración del control de cuadro de herramientas  
  
1.  En el **Explorador de soluciones**, agregue una clase al proyecto ItemConfiguration y asígnele el nombre `ToolboxConfig`.  
  
2.  Agregue al archivo las instrucciones siguientes del espacio de nombres.  
  
     [!code-cs[DynamicToolboxMembers#03](../misc/codesnippet/CSharp/walkthrough-customizing-toolbox-item-configuration-dynamically_3.cs)]
     [!code-vb[DynamicToolboxMembers#03](../misc/codesnippet/VisualBasic/walkthrough-customizing-toolbox-item-configuration-dynamically_3.vb)]  
  
3.  Asegúrese de que la clase `ToolboxConfig` es `public` e implementa la interfaz <xref:Microsoft.VisualStudio.Shell.IConfigureToolboxItem>.  
  
4.  Aplique un <xref:System.Runtime.InteropServices.GuidAttribute> y un <xref:Microsoft.VisualStudio.Shell.ProvideAssemblyFilterAttribute> a la clase `ToolboxConfig``.`  
  
    -   Para [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)], use un nombre de ensamblado de `"ItemConfigurationVB, Version=*, Culture=*, PublicKeyToken=*"`.  
  
    -   Para [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)], use un nombre de ensamblado de `"ItemConfigurationCS, Version=*, Culture=*, PublicKeyToken=*"`.  
  
     Esto restringe la clase `ToolboxConfig` para que funcione en objetos <xref:System.Drawing.Design.ToolboxItem> proporcionados por el ensamblado que contiene el VSPackage actual.  
  
     [!code-cs[DynamicToolboxMembers#04](../misc/codesnippet/CSharp/walkthrough-customizing-toolbox-item-configuration-dynamically_4.cs)]
     [!code-vb[DynamicToolboxMembers#04](../misc/codesnippet/VisualBasic/walkthrough-customizing-toolbox-item-configuration-dynamically_4.vb)]  
  
     Puede generar un GUID haciendo clic en **Crear GUID** en el menú **Herramientas**. Seleccione el **formato con corchetes**, haga clic en **Copiar** y pegue el GUID en el código. Cambie la palabra clave `GUID` a `Guid`.  
  
5.  Implemente el método <xref:Microsoft.VisualStudio.Shell.IConfigureToolboxItem.ConfigureToolboxItem%2A> de la <xref:Microsoft.VisualStudio.Shell.IConfigureToolboxItem> interfaz para que el método solo actúe en las dos clases <xref:System.Drawing.Design.ToolboxItem>, `Control1` y `Control2`.  
  
     La implementación de <xref:Microsoft.VisualStudio.Shell.IConfigureToolboxItem.ConfigureToolboxItem%2A> aplica instancias de <xref:System.ComponentModel.ToolboxItemFilterAttribute> a los dos objetos <xref:System.Drawing.Design.ToolboxItem> para que:  
  
    -   El <xref:System.Drawing.Design.ToolboxItem> que implementa `Control1` solo esté disponible en el **Cuadro de herramientas** para los diseñadores que administran objetos <xref:System.Windows.Forms.UserControl>.  
  
    -   El <xref:System.Drawing.Design.ToolboxItem> que implementa `Control2` no esté disponible en el **Cuadro de herramientas** para los diseñadores que administran objetos <xref:System.Windows.Forms.UserControl>.  
  
     [!code-cs[DynamicToolboxMembers#05](../misc/codesnippet/CSharp/walkthrough-customizing-toolbox-item-configuration-dynamically_5.cs)]
     [!code-vb[DynamicToolboxMembers#05](../misc/codesnippet/VisualBasic/walkthrough-customizing-toolbox-item-configuration-dynamically_5.vb)]  
  
## Modificar la implementación de VSPackage  
 La implementación predeterminada de VSPackage proporcionada por la plantilla de paquete de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] debe modificarse para realizar las siguientes acciones:  
  
-   Registrarse como un proveedor de elementos del **Cuadro de herramientas**.  
  
-   Registrar la clase que proporciona la configuración dinámica de controles del **Cuadro de herramientas** para el VSPackage.  
  
-   Usar <xref:System.Drawing.Design.ToolboxService> para cargar todos los objetos <xref:System.Drawing.Design.ToolboxItem> proporcionados por el ensamblado de VSPackage.  
  
-   Controlar los eventos <xref:Microsoft.VisualStudio.Shell.Package.ToolboxInitialized> y <xref:Microsoft.VisualStudio.Shell.Package.ToolboxUpgraded>.  
  
#### Para modificar la implementación del paquete para que sea un proveedor de elementos del cuadro de herramientas en el VSPackage  
  
1.  Abra la clase ItemConfigurationPackage en el editor de código.  
  
2.  Modifique la declaración de la clase `ItemConfigurationPackage`, que es la implementación de la clase <xref:Microsoft.VisualStudio.Shell.Package> en la solución.  
  
    1.  Agregue al archivo las instrucciones siguientes del espacio de nombres.  
  
         [!code-vb[DynamicToolboxMembers#06](../misc/codesnippet/VisualBasic/walkthrough-customizing-toolbox-item-configuration-dynamically_6.vb)]
         [!code-cs[DynamicToolboxMembers#06](../misc/codesnippet/CSharp/walkthrough-customizing-toolbox-item-configuration-dynamically_6.cs)]  
  
    2.  Para registrar el VSPackage como proveedor de elementos del **Cuadro de herramientas**, aplique un <xref:Microsoft.VisualStudio.Shell.ProvideToolboxItemsAttribute> al paquete. Para registrar la clase `ToolboxConfig` como proveedor de la configuración dinámica de controles del **Cuadro de herramientas**, aplique un <xref:Microsoft.VisualStudio.Shell.ProvideToolboxItemConfigurationAttribute> al paquete.  
  
         [!code-vb[DynamicToolboxMembers#07](../misc/codesnippet/VisualBasic/walkthrough-customizing-toolbox-item-configuration-dynamically_7.vb)]
         [!code-cs[DynamicToolboxMembers#07](../misc/codesnippet/CSharp/walkthrough-customizing-toolbox-item-configuration-dynamically_7.cs)]  
  
        > [!NOTE]
        >  El único argumento de <xref:Microsoft.VisualStudio.Shell.ProvideToolboxItemsAttribute> es la versión de <xref:System.Drawing.Design.ToolboxItem> proporcionada por el VSPackage. Al cambia este valor, se fuerza el IDE para cargar el VSPackage incluso si tiene una versión anteriormente almacenada en caché de <xref:System.Drawing.Design.ToolboxItem>.  
  
    3.  Cree dos nuevos campos `private` en la clase `ItemConfiguration` de la forma siguiente:  
  
         Un miembro de <xref:System.Collections.ArrayList>, denominado `ToolboxItemList`, para mantener una lista de los objetos <xref:System.Drawing.Design.ToolboxItem> que administra la clase `ItemConfiguration`.  
  
         Un <xref:System.String>, denominado `CategoryTab`, que contiene la pestaña **Cuadro de herramientas** que se usa para mantener los objetos de <xref:System.Drawing.Design.ToolboxItem> administrados por la clase `ItemConfiguration`.  
  
         [!code-vb[DynamicToolboxMembers#08](../misc/codesnippet/VisualBasic/walkthrough-customizing-toolbox-item-configuration-dynamically_8.vb)]
         [!code-cs[DynamicToolboxMembers#08](../misc/codesnippet/CSharp/walkthrough-customizing-toolbox-item-configuration-dynamically_8.cs)]  
  
     El resultado de esta modificación es similar al código siguiente:  
  
     [!code-vb[DynamicToolboxMembers#09](../misc/codesnippet/VisualBasic/walkthrough-customizing-toolbox-item-configuration-dynamically_9.vb)]
     [!code-cs[DynamicToolboxMembers#09](../misc/codesnippet/CSharp/walkthrough-customizing-toolbox-item-configuration-dynamically_9.cs)]  
  
3.  Defina un método `OnRefreshToolbox` para controlar los eventos <xref:Microsoft.VisualStudio.Shell.Package.ToolboxInitialized> y <xref:Microsoft.VisualStudio.Shell.Package.ToolboxUpgraded>.  
  
     El método `OnRefreshToolbox` usa la lista de objetos <xref:System.Drawing.Design.ToolboxItem> que se encuentra en el campo `ToolboxItemList` y realiza lo siguiente:  
  
    -   Quita todos los objetos <xref:System.Drawing.Design.ToolboxItem> de la pestaña **Cuadro de herramientas** definida por el campo `CategoryTab`.  
  
    -   Agrega a la pestaña **Cuadro de herramientas** nuevas instancias de todos los objetos <xref:System.Drawing.Design.ToolboxItem> que aparecen en el campo `ToolboxItemList`.  
  
    -   Establece la pestaña **Cuadro de herramientas** como la pestaña activa.  
  
     [!code-vb[DynamicToolboxMembers#10](../misc/codesnippet/VisualBasic/walkthrough-customizing-toolbox-item-configuration-dynamically_10.vb)]
     [!code-cs[DynamicToolboxMembers#10](../misc/codesnippet/CSharp/walkthrough-customizing-toolbox-item-configuration-dynamically_10.cs)]  
  
4.  Para [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)], en el constructor, registre el método `OnRefreshToolbox` como el controlador de eventos para los eventos <xref:Microsoft.VisualStudio.Shell.Package.ToolboxInitialized> y <xref:Microsoft.VisualStudio.Shell.Package.ToolboxUpgraded>.  
  
     [!code-cs[DynamicToolboxMembers#11](../misc/codesnippet/CSharp/walkthrough-customizing-toolbox-item-configuration-dynamically_11.cs)]  
  
5.  Modifique el método `Initialize` en `ItemConfigurationPackage` para rellenar el campo `ToolboxItemList` llamando al método <xref:System.Drawing.Design.ToolboxService.GetToolboxItems%2A> de la clase <xref:System.Drawing.Design.ToolboxService?displayProperty=fullName>. El servicio **Cuadro de herramientas** obtiene todas las clases de elementos del **Cuadro de herramientas** definidas en el ensamblado que se está ejecutando actualmente. Los controladores de eventos del **Cuadro de herramientas** usan el campo `ToolboxItemList` para cargar los elementos del **Cuadro de herramientas**.  
  
     Agregue el código siguiente al final del método `Initialize`.  
  
     [!code-vb[DynamicToolboxMembers#12](../misc/codesnippet/VisualBasic/walkthrough-customizing-toolbox-item-configuration-dynamically_12.vb)]
     [!code-cs[DynamicToolboxMembers#12](../misc/codesnippet/CSharp/walkthrough-customizing-toolbox-item-configuration-dynamically_12.cs)]  
  
    > [!NOTE]
    >  Como ejercicio, se podría desarrollar un mecanismo para comprobar la versión de VSPackage o los elementos, y actualizar solo si ha cambiado la versión de VSPackage, o si la versión de <xref:System.Drawing.Design.ToolboxItem> ha cambiado.  
  
## Inicializar el cuadro de herramientas  
  
#### Implementar un comando para inicializar el cuadro de herramientas  
  
-   En la clase `ItemConfigurationPackage`, cambie el método `MenuItemCallBack`, que es el controlador de comandos del elemento de menú.  
  
     Reemplace la implementación existente del método `MenuItemCallBack` usando el código siguiente:  
  
     [!code-vb[DynamicToolboxMembers#13](../misc/codesnippet/VisualBasic/walkthrough-customizing-toolbox-item-configuration-dynamically_13.vb)]
     [!code-cs[DynamicToolboxMembers#13](../misc/codesnippet/CSharp/walkthrough-customizing-toolbox-item-configuration-dynamically_13.cs)]  
  
## Compilar y ejecutar la solución  
 Puede usar el producto de este tutorial mediante una instancia de Visual Studio que se está ejecutando en el subárbol experimental.  
  
#### Para ejecutar este tutorial  
  
1.  En Visual Studio, en el menú **Compilar**, haga clic en **Recompilar solución**.  
  
2.  Presione F5 para iniciar una segunda instancia de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] en el subárbol del registro experimental.  
  
     Para más información sobre cómo usar el subárbol experimental, consulte [La instancia Experimental](../extensibility/the-experimental-instance.md).  
  
3.  Haga clic en el menú **Herramientas**.  
  
     Aparecerá un comando llamado **Inicializar ItemConfiguration VB** o **Inicializar ItemConfiguration CS** en la parte superior del menú, junto con un icono que tiene el número 1.  
  
4.  Cree una nueva aplicación de Windows Forms [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] o [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)].  
  
     Aparecerá el diseñador basado en <xref:System.Windows.Forms.Form>.  
  
5.  Agregue un control de usuario al proyecto.  
  
     Aparecerá un diseñador de controles de usuario.  
  
6.  Ancle el **Cuadro de herramientas** abierto y cambie entre las dos vistas de diseño.  
  
     Observe que el elemento del **Cuadro de herramientas** que esté visible y el que está oculto dependen del diseñador que tiene el foco.  
  
7.  Arrastre el primer elemento del **Cuadro de herramientas** al control de usuario para agregar una instancia de `Control1` al control de usuario.  
  
8.  Arrastre el segundo elemento del **Cuadro de herramientas** al formulario para agregar una instancia de `Control2` al formulario.  
  
9. Compile la aplicación para Windows.  
  
     El control de usuario para la aplicación está ahora disponible en el **Cuadro de herramientas**.  
  
10. Agregue el control de usuario de la aplicación al formulario, y luego vuelva a compilar la aplicación y ejecútela.  
  
     Cuando se ejecute la aplicación, haga clic en cada control del formulario para abrir el cuadro de mensaje asociado.  
  
## Análisis de la implementación  
 Puesto que el parámetro `assemblyFilter` está presente en el constructor de clase <xref:Microsoft.VisualStudio.Shell.ProvideAssemblyFilterAttribute>, solo los objetos <xref:System.Drawing.Design.ToolboxItem> en el ensamblado producidos en este tutorial actuarán en el método <xref:Microsoft.VisualStudio.Shell.IConfigureToolboxItem.ConfigureToolboxItem%2A> de la clase `ToolboxConfg`.  
  
 Por lo tanto, siempre que la categoría **ItemConfiguration Walkthrough** esté activa en el **Cuadro de herramientas**, se llamará al método <xref:Microsoft.VisualStudio.Shell.IConfigureToolboxItem.ConfigureToolboxItem%2A> de la clase `ToolboxConfg`, y se aplicarán instancias de <xref:System.ComponentModel.ToolboxItemFilterAttribute> en los objetos de <xref:System.Drawing.Design.ToolboxItem> implementados por `Control1` y `Control2`.  
  
## Vea también  
 [Extensión del Cuadro de herramientas](../misc/extending-the-toolbox.md)   
 [Registrar características de compatibilidad del Cuadro de herramientas](../misc/registering-toolbox-support-features.md)   
 [Desarrollo avanzado de controles del cuadro de herramientas](../misc/advanced-toolbox-control-development.md)   
 [Tutoriales del cuadro de herramientas](../misc/toolbox-walkthroughs.md)