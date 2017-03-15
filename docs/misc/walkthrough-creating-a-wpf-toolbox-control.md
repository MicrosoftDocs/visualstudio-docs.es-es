---
title: "Tutorial: Crear un control de Cuadro de herramientas de WPF | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "toolbox"
  - "wpf"
ms.assetid: 8223c06e-f327-4778-8709-e0cc7eae2c78
caps.latest.revision: 15
caps.handback.revision: 15
manager: "douge"
---
# Tutorial: Crear un control de Cuadro de herramientas de WPF
La plantilla Control de cuadro de herramientas de WPF que se incluye en el SDK de Visual Studio permite crear controles de Windows Presentation Foundation \(WPF\) que se agregan automáticamente al **Cuadro de herramientas** cuando se instala la extensión. En este tutorial se muestra cómo usar la plantilla para crear un control de contador que se pueda distribuir a otros usuarios.  
  
## Requisitos previos  
 Para seguir este tutorial, debe instalar el SDK de Visual Studio. Para obtener más información, consulta [Visual Studio SDK](../extensibility/visual-studio-sdk.md).  
  
## Buscar la plantilla Control de cuadro de herramientas de WPF en Visual Studio  
 La plantilla Control de cuadro de herramientas de WPF está disponible en el cuadro de diálogo **Nuevo proyecto**, en **Plantillas instaladas**, en las siguientes ubicaciones:  
  
-   **Visual Basic**, **Extensibilidad**. El lenguaje del proyecto es Visual Basic.  
  
-   **Visual C\#**, **Extensibilidad**. El lenguaje del proyecto es C\#.  
  
## Crear un proyecto de Control de cuadro de herramientas de WPF  
 La plantilla Control de cuadro de herramientas de WPF crea un control de usuario no definido y proporciona todas las funciones necesarias para agregar el control al **Cuadro de herramientas**.  
  
#### Para crear el proyecto  
  
1.  En el menú **Archivo**, haga clic en **Nuevo** y, a continuación, haga clic en **Proyecto**.  
  
2.  En el cuadro de diálogo **Nuevo proyecto**, en **Plantillas instaladas**, haga clic en el nodo para elegir el lenguaje de programación preferido y luego haga clic en **Extensibilidad**. En la lista de tipos de proyecto, seleccione **Control de cuadro de herramientas de WPF**.  
  
3.  En el cuadro **Nombre**, escriba el nombre que desee usar para el proyecto. \(Este tutorial usa el nombre `Counter`\). Haga clic en **Aceptar**.  
  
     Se crea una solución que contiene un control de usuario, un atributo para colocar el control en el **Cuadro de herramientas** y el manifiesto de VSIX para la implementación. El cuadro **Nombre** establece el nombre de la solución y el del espacio de nombres, pero no establece el nombre del control, tal como aparece en el **Cuadro de herramientas**. Deberá establecerlo más adelante en el tutorial.  
  
### Crear una interfaz de usuario para el control  
 El control `Counter` requiere tres controles secundarios: dos controles <xref:System.Windows.Controls.Label> para mostrar el texto y el recuento actual, y un control <xref:System.Windows.Controls.Button> para restablecer el recuento a 0. No se necesitan más controles secundarios, dado que el hospedaje de aplicaciones incrementará el contador mediante programación.  
  
##### Para crear la interfaz de usuario  
  
1.  En el **Explorador de soluciones**, haga doble clic en ToolboxControl.cs para abrirlo en el diseñador.  
  
     El diseñador muestra un control <xref:System.Windows.Controls.Grid> que contiene un control <xref:System.Windows.Controls.Button>.  
  
2.  Seleccione el control <xref:System.Windows.Controls.Grid> y, después, haga clic en las barras azules que aparecen en los lados superior e izquierdo de la cuadrícula para dividirla en dos filas y dos columnas.  
  
3.  Desde el **Cuadro de herramientas**, arrastre un control <xref:System.Windows.Controls.Label> a cada una de las celdas de la fila superior de la cuadrícula.  
  
     En este punto, podría establecer el diseño del control organizando los elementos en la cuadrícula. En su lugar, puede editar directamente el lenguaje de marcado de aplicaciones extensible \(XAML\) para que el control cambie de tamaño dinámicamente para ajustarse al texto.  
  
4.  En el panel **XAML**, establezca la altura de los elementos `RowDefinition` y el ancho de los elementos `ColumnDefinition` en `"auto"`.  
  
5.  Edite el marcado del botón y las dos etiquetas de manera que se parezca al del ejemplo siguiente.  
  
     [!code-xml[ToolboxControlWPF#11](../misc/codesnippet/Xaml/walkthrough-creating-a-wpf-toolbox-control_1.xaml)]  
  
     Los atributos `Grid.Row` y `Grid.Column` establecen la posición de los elementos en la cuadrícula. El atributo `Grid.ColumnSpan` en el botón habilita la primera columna para que cambie de tamaño independientemente del ancho del botón.  
  
     Los atributos `Content` de las etiquetas usan una sintaxis `{Binding}` para el enlace a las propiedades que definirá más adelante en el tutorial.  
  
### Codificar el control de usuario  
 El control `Counter` presentará un método para incrementar el contador, un evento que se desencadenará cuando el contador se incremente, un botón `Reset` y tres propiedades para almacenar el recuento actual, el texto para mostrar y si se debe mostrar u ocultar el botón `Reset`. El atributo `ProvideTolboxControl` determina la ubicación del **Cuadro de herramientas** donde se mostrará el control `Counter`.  
  
 Podría escribir este control de la misma manera que escribiría un control de Windows Forms, es decir, mediante controladores de eventos y métodos públicos para establecer el contenido de las etiquetas. Sin embargo, en WPF puede establecer un contexto de datos para el control que le permita enlazar atributos de elementos XAML directamente a las propiedades del código. Este modelo también proporciona una capa de abstracción para separar las características básicas de la interfaz de usuario \(UI\) del control.  
  
 En este tutorial se muestra cómo crear una clase de modelo de datos y, después, cómo enlazar el contexto de datos del control al modelo de datos.  
  
##### Para crear un modelo de datos  
  
1.  Haga doble clic en el botón para abrir la ventana de código.  
  
2.  En la parte superior del archivo, agregue una directiva `using` para el espacio de nombres <xref:System.ComponentModel>.  
  
3.  Después de la clase generada, cree una clase pública para definir el contexto de datos.  
  
     [!code-cs[ToolboxControlWPF#01](../misc/codesnippet/CSharp/walkthrough-creating-a-wpf-toolbox-control_2.cs)]  
  
     Esta clase implementa la interfaz <xref:System.ComponentModel.INotifyPropertyChanged>, que permite el enlace de los elementos XAML a las propiedades definidas.  
  
4.  Haga clic con el botón derecho en la declaración de interfaz <xref:System.ComponentModel.INotifyPropertyChanged>, haga clic en **Implementar interfaz** y haga clic en **Implementar interfaz** de nuevo.  
  
     Visual Studio declara un evento `PropertyChanged`.  
  
5.  Después de la declaración de evento, cree el método privado siguiente para generar el evento.  
  
     [!code-cs[ToolboxControlWPF#02](../misc/codesnippet/CSharp/walkthrough-creating-a-wpf-toolbox-control_3.cs)]  
  
6.  Cree los siguientes campos privados y propiedades públicas para que contengan los valores de las dos etiquetas del control.  
  
     [!code-cs[ToolboxControlWPF#03](../misc/codesnippet/CSharp/walkthrough-creating-a-wpf-toolbox-control_4.cs)]  
  
     Al generar el evento `PropertyChanged`, el enlace XAML actualiza el contenido de los controles enlazados. Si las propiedades se establecen como `public`, estarán disponibles para el diseñador, pero no para otros programas, a menos que se enlacen a este contexto de datos.  
  
 Ahora que ha creado el modelo de datos, puede implementar la función de código subyacente del control.  
  
##### Para implementar el control  
  
1.  En la definición de la clase parcial que implementa el control, haga clic con el botón derecho en el nombre de clase, haga clic en **Refactorizar**, en **Cambiar nombre** y, después, cambie el nombre de la clase a `Counter`. Este es el nombre que se mostrará en el **Cuadro de herramientas** cuando se instale la extensión.  
  
2.  Justo encima de la definición de clase en la declaración de atributos de `ProvideToolboxControl`, cambie el valor del primer parámetro de `"Counter"` a `"General"`. Se establece el nombre del grupo de elementos que va a hospedar el control en el **Cuadro de herramientas**.  
  
     En el ejemplo siguiente se muestra el atributo `ProvideToolboxControl` y la definición de clase ajustada.  
  
     [!code-cs[ToolboxControlWPF#04](../misc/codesnippet/CSharp/walkthrough-creating-a-wpf-toolbox-control_5.cs)]  
  
3.  Cree un campo privado destinado a contener el contexto de datos del control y, luego, en el constructor, asigne el contexto de datos a la clase `MyDataModel`, como se muestra en el ejemplo siguiente.  
  
     [!code-cs[ToolboxControlWPF#05](../misc/codesnippet/CSharp/walkthrough-creating-a-wpf-toolbox-control_6.cs)]  
  
4.  Cree las siguientes propiedades públicas para reflejar las propiedades `Text` y `Count` del contexto de datos.  
  
     [!code-cs[ToolboxControlWPF#06](../misc/codesnippet/CSharp/walkthrough-creating-a-wpf-toolbox-control_7.cs)]  
  
     Estas propiedades hacen que el contenido del contexto de datos esté disponible para cualquier aplicación que incluya el control.  
  
5.  Cree el siguiente método público para incrementar el contador y un evento para notificar a la aplicación de hospedaje.  
  
     [!code-cs[ToolboxControlWPF#07](../misc/codesnippet/CSharp/walkthrough-creating-a-wpf-toolbox-control_8.cs)]  
  
6.  Implemente el controlador de clic para el botón `Reset` de la siguiente manera.  
  
     [!code-cs[ToolboxControlWPF#08](../misc/codesnippet/CSharp/walkthrough-creating-a-wpf-toolbox-control_9.cs)]  
  
7.  Agregue la siguiente propiedad pública para mostrar u ocultar el botón `Reset`.  
  
     [!code-cs[ToolboxControlWPF#09](../misc/codesnippet/CSharp/walkthrough-creating-a-wpf-toolbox-control_10.cs)]  
  
## Probar el control  
 Para probar un control del **Cuadro de herramientas**, pruébelo primero en el entorno de desarrollo y, luego, vuelva a probarlo en una aplicación de hospedaje.  
  
#### Para probar el control  
  
1.  Presione F5.  
  
     Se compila el proyecto y se abre una segunda instancia de Visual Studio que tiene el control instalado.  
  
2.  En la nueva instancia de Visual Studio, cree un proyecto de aplicación WPF.  
  
3.  En el **Explorador de soluciones**, haga doble clic en MainWindow.xaml para abrirlo en el diseñador.  
  
4.  Desde la sección **General** del **Cuadro de herramientas**, arrastre un control **Contador** al formulario y, luego, selecciónelo.  
  
     Las propiedades `Text` y `ShowReset` deben mostrarse en la ventana **Propiedades**, junto con las otras propiedades heredadas de <xref:System.Windows.Controls.UserControl>. La propiedad `Count` no debería mostrarse, ya que es de solo lectura.  
  
5.  Cambie el valor de la propiedad `Text`.  
  
     El texto de la etiqueta que se muestra en el diseñador debería cambiar.  
  
6.  Establezca la propiedad `ShowReset` en `Hidden` y, después, restablézcala a `Visible`.  
  
     El botón `Reset` del control debería desaparecer y volver a aparecer.  
  
7.  Arrastre un control <xref:System.Windows.Controls.Button> al formulario, establezca su atributo `Content``` en `Test` y, después, haga doble clic en el botón para abrir su controlador de clic en la vista de código.  
  
8.  Implemente el controlador de clic para llamar al método `Increment` del control.  
  
     [!code-cs[ToolboxControlWPF#21](../misc/codesnippet/CSharp/walkthrough-creating-a-wpf-toolbox-control_11.cs)]  
  
9. En la función constructora, después de la llamada a `InitializeComponent`, escriba `counter1.Implemented +=` y presione la tecla TAB dos veces para generar un controlador para el evento `Counter.Incremented`.  
  
10. Implemente el nuevo controlador tal como se muestra en el ejemplo siguiente.  
  
     [!code-cs[ToolboxControlWPF#22](../misc/codesnippet/CSharp/walkthrough-creating-a-wpf-toolbox-control_12.cs)]  
  
11. Presione F5.  
  
     La aplicación WPF debería abrirse.  
  
12. Haga clic en **Probar**.  
  
     El contador debería incrementarse y el botón debería atenuar ligeramente.  
  
13. Haga clic en **Probar** cuatro veces más.  
  
     El contador debería incrementarse y el botón se debería seguir atenuando hasta desaparecer. Si sigue haciendo clic en la posición donde se encontraba el botón, el contador debería seguir incrementándose.  
  
14. Haga clic en **Restablecer**.  
  
     El contador debería restablecerse a **0**.  
  
## Pasos siguientes  
 Cuando se crea un control del **Cuadro de herramientas**, Visual Studio crea un archivo denominado *NombreDelProyecto*.vsix en la carpeta \\bin\\debug\\ del proyecto. Para implementar el control, puede cargar el archivo .vsix en una red o un sitio web. Cuando un usuario abre el archivo .vsix, el control se instala y se agrega al **Cuadro de herramientas** de Visual Studio. O bien, si carga el archivo .vsix en el sitio web de la [Galería de Visual Studio](http://go.microsoft.com/fwlink/?LinkID=123847) para que los usuarios puedan buscarlo en el **Administrador de extensiones**.  
  
## Vea también  
 [Extensión del Cuadro de herramientas](../misc/extending-the-toolbox.md)   
 [Crear un Control de cuadro de herramientas de Windows Forms](../extensibility/creating-a-windows-forms-toolbox-control.md)   
 [Extensión de otras partes de Visual Studio](../extensibility/extending-other-parts-of-visual-studio.md)   
 [Trabajar con controles en WPF Designer](http://msdn.microsoft.com/es-es/c6235492-b10d-4c3c-ba67-6b6a545faee1)   
 [Información general sobre la creación de controles](../Topic/Control%20Authoring%20Overview.md)