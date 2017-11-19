---
title: Controles de contenido | Documentos de Microsoft
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VST.Toolbox.DropDownListContentControl
- VST.Toolbox.RichTextContentControl
- VST.Toolbox.PlainTextContentControl
- VST.Toolbox.ComboBoxContentControl
- VST.Toolbox.CCBuildingBlockGalleryContentControl
- VST.Toolbox.DatePickerContentControl
- VST.Toolbox.PictureContentControl
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- document building blocks [Office development in Visual Studio]
- restricted permissions [Office development in Visual Studio]
- ComboBoxContentControl class
- PictureContentControl class
- PlainTextContentControl class
- Office documents [Office development in Visual Studio], restricted permissions
- RichTextContentControl class
- content controls [Office development in Visual Studio]
- building block gallery [Office development in Visual Studio]
- controls [Office development in Visual Studio], content controls
- GroupContentControl class
- documents [Office development in Visual Studio], restricted permissions
- DropDownListContentControl class
- DatePickerContentControl class
- data binding [Office development in Visual Studio], content controls
- content controls [Office development in Visual Studio], about content controls
- custom XML parts, content controls
- templates [Office development in Visual Studio], content controls
- BuildingBlockGalleryContentControl class
ms.assetid: ed59e522-dd6e-4c82-8d49-f5dbcfcc950d
caps.latest.revision: "65"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 5b2950370b35eb8e2f60f15c5de032284c5546f3
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="content-controls"></a>Controles de contenido
  Los controles de contenido proporcionan un mecanismo para diseñar documentos y plantillas con las siguientes características:  
  
-   Una interfaz de usuario que tiene la entrada controlada, como un formulario.  
  
-   Restricciones que impiden que los usuarios editen secciones protegidas del documento o plantilla. Para obtener más información, consulte [proteger elementos de documentos mediante controles de contenido](#Protection).  
  
-   Enlace de datos a un origen de datos. Para obtener más información, consulte [enlazar datos a controles de contenido](#DataBinding).  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
 ![vínculo a vídeo](../vsto/media/playvideo.gif "vínculo a vídeo") para una demostración en vídeo relacionada, vea [enlazar datos a Word 2007 contenido controles mediante Visual Studio Tools para Office System (3.0)](http://go.microsoft.com/fwlink/?LinkId=136785).  
  
## <a name="overview-of-content-controls"></a>Información general sobre los controles de contenido  
 Los controles de contenido proporcionan una interfaz de usuario que está optimizada para la entrada e impresión de datos. Cuando se agrega un control de contenido a un documento, este control se identifica por un borde, un título o un texto provisional que puede proporcionar instrucciones al usuario. El borde y el título del control no aparecen en las versiones impresas del documento.  
  
 Por ejemplo, si desea que el usuario escriba una fecha en una sección del documento, puede agregar un control de contenido de selector de fecha al documento. Cuando los usuarios hagan clic en el control, aparecerá la interfaz de usuario de selector de fecha estándar. También puede establecer las propiedades del control para configurar el calendario regional mostrado y especificar el formato de fecha. Una vez que el usuario elige una fecha, la interfaz de usuario del control se oculta y, si el usuario imprime el documento, solo aparecerá la fecha.  
  
 Los controles de contenido también le ayudan a llevar a cabo las siguientes tareas:  
  
-   Impedir que los usuarios editen o eliminen elementos de un documento. Esto resulta útil si tiene información en un documento o plantilla que los usuarios deberían leer, pero no editar, o si desea que los usuarios puedan modificar controles de contenido, pero no eliminarlos.  
  
-   Enlazar a datos los elementos de un documento o plantilla. Puede enlazar los controles de contenido a los campos de una base de datos, los objetos administrados de [!INCLUDE[dnprdnshort](../sharepoint/includes/dnprdnshort-md.md)], los elementos XML que están almacenados en el documento y otros orígenes de datos.  
  
 En proyectos de nivel de documento, puede agregar controles de contenido al documento en tiempo de diseño o en tiempo de ejecución. En proyectos de complemento de VSTO, puede agregar controles de contenido a cualquier documento abierto en tiempo de ejecución. Para obtener más información, consulte [Cómo: agregar controles de contenido a documentos de Word](../vsto/how-to-add-content-controls-to-word-documents.md).  
  
> [!NOTE]  
>  Los controles de contenido solo se pueden usar en documentos que se han guardado con el formato Open XML. No puede usar controles de contenido en documentos que se han guardado con el formato Documento de Word 97-2003 (.doc).  
  
## <a name="types-of-content-controls"></a>Tipos de controles de contenido  
 Existen nueve tipos diferentes de controles de contenido que se pueden agregar a los documentos. La mayoría de ellos tienen un tipo correspondiente en el espacio de nombres <xref:Microsoft.Office.Tools.Word>. También se puede usar un tipo <xref:Microsoft.Office.Tools.Word.ContentControl> genérico, que puede representar cualquiera de los controles de contenido disponibles. Para ver un tutorial que muestra cómo utilizar cada uno de los controles de contenido disponibles, vea [Tutorial: crear una plantilla mediante controles de contenido](../vsto/walkthrough-creating-a-template-by-using-content-controls.md).  
  
### <a name="building-block-gallery"></a>Galería de bloques de creación  
 Una galería de bloques de creación permite a los usuarios seleccionar de una lista de *bloques de creación de documentos* para insertar en un documento. Un bloque de creación de documento es un fragmento de contenido que se ha creado para usarse varias veces, como una portada, una tabla con formato o un encabezado común. Para obtener más información, consulte el tipo <xref:Microsoft.Office.Tools.Word.BuildingBlockGalleryContentControl>. Para obtener más información acerca de los bloques de creación, vea [Novedades para programadores en Word 2007](http://msdn.microsoft.com/en-us/74aa6688-65b3-4167-997d-131f26ad8f84).  
  
### <a name="check-box"></a>Casilla  
 Una casilla proporciona una interfaz de usuario que representa un estado binario: activada o desactivada.  
  
 A diferencia de los demás tipos de controles de contenido, [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] no proporciona ningún tipo específico que represente un control de contenido de casilla. En otras palabras, no hay ningún tipo CheckBoxContentControl. Sin embargo, puede crear un control de contenido de casilla agregando un <xref:Microsoft.Office.Tools.Word.ContentControl> genérico a un documento mediante programación. Para obtener más información, consulte [controles de contenido de casilla en proyectos de Word](#checkbox).  
  
### <a name="combo-box"></a>Cuadro combinado  
 En los cuadros combinados se muestra una lista de elementos que los usuarios pueden seleccionar. A diferencia de las listas desplegables, los cuadros combinados permiten a los usuarios agregar sus propios elementos. Para obtener más información, consulte el tipo <xref:Microsoft.Office.Tools.Word.ComboBoxContentControl>.  
  
### <a name="date-picker"></a>Selector de fecha  
 Un selector de fecha proporciona una interfaz de usuario de calendario en la que se puede seleccionar una fecha. El calendario aparece cuando el usuario hace clic en la flecha de lista desplegable del control. Puede usar calendarios regionales y formatos de fecha diferentes. Para obtener más información, consulte el tipo <xref:Microsoft.Office.Tools.Word.DatePickerContentControl>.  
  
### <a name="drop-down-list"></a>Lista desplegable  
 En las listas desplegables se muestra una lista de elementos que los usuarios pueden seleccionar. A diferencia de los cuadros combinados, las listas desplegables no permiten que los usuarios agreguen o modifiquen elementos. Para obtener más información, consulte el tipo <xref:Microsoft.Office.Tools.Word.DropDownListContentControl>.  
  
### <a name="group"></a>Grupo  
 Un control de grupo define una región protegida de un documento que los usuarios no pueden editar ni eliminar. Un control de grupo puede contener cualquier elemento del documento, como texto, tablas, gráficos y otros controles de contenido. Para obtener más información, consulte el tipo <xref:Microsoft.Office.Tools.Word.GroupContentControl>.  
  
### <a name="picture"></a>Imagen  
 Un control de imagen muestra una imagen. Puede especificar la imagen en tiempo de diseño o tiempo de ejecución; asimismo, los usuarios pueden hacer clic en este control para seleccionar la imagen que se va a insertar en el documento. Para obtener más información, consulte el tipo <xref:Microsoft.Office.Tools.Word.PictureContentControl>.  
  
### <a name="rich-text"></a>Texto enriquecido  
 Un control de texto enriquecido contiene texto u otros elementos, como tablas, imágenes u otros controles de contenido. Para obtener más información, consulte el tipo <xref:Microsoft.Office.Tools.Word.RichTextContentControl>.  
  
### <a name="plain-text"></a>Texto sin formato  
 Un control de texto sin formato contiene texto. Un control de texto sin formato no puede incluir otros elementos, como tablas, imágenes u otros controles de contenido. Además, todo el texto de un control de texto sin formato tiene el mismo formato. Por ejemplo, si pone en cursiva una palabra de una frase que se encuentra en un control de texto sin formato, todo el texto incluido en el control se pone en cursiva. Para obtener más información, consulte el tipo <xref:Microsoft.Office.Tools.Word.PlainTextContentControl>.  
  
### <a name="generic-content-control"></a>Control de contenido genérico  
 Un control de contenido genérico es un objeto <xref:Microsoft.Office.Tools.Word.ContentControl> que puede representar cualquiera de los tipos de controles de contenido disponibles. Se puede cambiar un objeto <xref:Microsoft.Office.Tools.Word.ContentControl> para que se comporte como un control de contenido de un tipo distinto mediante la propiedad <xref:Microsoft.Office.Tools.Word.ContentControl.Type%2A>. Por ejemplo, si crea un objeto <xref:Microsoft.Office.Tools.Word.ContentControl> que representa un control de texto sin formato, puede cambiarlo en tiempo de ejecución para que se comporte como un cuadro combinado.  
  
 Solo puede crear objetos <xref:Microsoft.Office.Tools.Word.ContentControl> en tiempo de ejecución, no en tiempo de diseño. Para obtener más información, consulte [Cómo: agregar controles de contenido a documentos de Word](../vsto/how-to-add-content-controls-to-word-documents.md).  
  
## <a name="common-features-of-content-controls"></a>Características comunes de los controles de contenido  
 La mayor parte de los controles de contenido comparten un conjunto de miembros que se pueden usar para llevar a cabo tareas comunes. En la tabla siguiente se describen algunas de las tareas que puede llevar a cabo con estos miembros.  
  
|Para efectuar esta tarea:|Haga lo siguiente:|  
|--------------------|--------------|  
|Obtener o establecer el texto que se muestra en el control.|Use la **texto** propiedad. **Nota:** el <xref:Microsoft.Office.Tools.Word.PictureContentControl> y <xref:Microsoft.Office.Tools.Word.ContentControl> tipos no tienen esta propiedad.|  
|Obtener o establecer el texto provisional que se muestra en el control hasta que un usuario lo edita, se rellena con datos de un origen de datos o se elimina el contenido del control.|Use la **PlaceholderText** propiedad. **Nota:** el <xref:Microsoft.Office.Tools.Word.PictureContentControl> tipo no tiene esta propiedad.|  
|Obtener o establecer el título que se muestra en el borde del control de contenido cuando el usuario hace clic en él.|Use la **título** propiedad.|  
|Quitar automáticamente el control del documento una vez que el usuario lo haya editado (el texto del control permanece en el documento).|Use la **temporal** propiedad.|  
|Ejecutar el código cuando el usuario haga clic en el control de contenido o cuando el cursor se mueva al control de contenido mediante programación.|Controle el evento <xref:Microsoft.Office.Tools.Word.ContentControlBase.Entering> del control.|  
|Ejecutar el código cuando el usuario haga clic fuera del control de contenido o cuando el cursor se mueva fuera del control de contenido mediante programación.|Controle el evento <xref:Microsoft.Office.Tools.Word.ContentControlBase.Exiting> del control.|  
|Ejecutar el código una vez que el control de contenido se haya agregado al documento como resultado de una operación de deshacer o rehacer.|Controle el evento <xref:Microsoft.Office.Tools.Word.ContentControlBase.Added> del control.|  
|Ejecutar el código justo antes de que se elimine el control de contenido del documento.|Controle el evento <xref:Microsoft.Office.Tools.Word.ContentControlBase.Deleting> del control.|  
  
##  <a name="Protection"></a>Proteger elementos de documentos mediante controles de contenido  
 Al proteger un elemento de un documento, se impide que los usuarios cambien o eliminen el contenido de ese elemento. Existen varios modos de proteger los elementos de un documento mediante los controles de contenido.  
  
 Si el área que desea proteger está dentro de un control de contenido, puede usar las propiedades del control de contenido para impedir que los usuarios editen o eliminen el control:  
  
-   El **LockContents** propiedad impide que los usuarios editen el contenido.  
  
-   El **LockContentControl** propiedad evita que los usuarios eliminen el control.  
  
 Si el área que desea proteger no está dentro de un control de contenido o si desea proteger un área que contiene controles de contenido además de otros tipos de contenido, puede situar el área completa en un <xref:Microsoft.Office.Tools.Word.GroupContentControl>. A diferencia de otros controles de contenido, el <xref:Microsoft.Office.Tools.Word.GroupContentControl> no proporciona una interfaz de usuario visible para el usuario. Su único propósito es definir una región que los usuarios no puedan modificar.  
  
> [!NOTE]  
>  Si crea un <xref:Microsoft.Office.Tools.Word.GroupContentControl> que contiene controles de contenido insertados, estos controles no se protegerán automáticamente. Debe utilizar el **LockContents** propiedad de cada uno de los controles insertados para impedir que los usuarios editen su contenido.  
  
 Para obtener más información acerca de cómo usar controles de contenido para proteger elementos de documentos, consulte [Cómo: proteger elementos de documentos mediante controles de contenido](../vsto/how-to-protect-parts-of-documents-by-using-content-controls.md).  
  
##  <a name="DataBinding"></a>Enlazar datos a controles de contenido  
 Puede mostrar los datos en documentos estableciendo enlaces entre un control de contenido y un origen de datos. Cuando el origen de datos se actualice, el control de contenido reflejará los cambios. También puede volver a guardar los cambios en el origen de datos.  
  
 Los controles de contenido proporcionan las siguientes opciones de enlace de datos:  
  
-   Puede enlazar controles de contenido a los campos de una base de datos o a los objetos administrados usando el mismo modelo de enlace de datos que Windows Forms.  
  
-   Puede enlazar controles de contenido a elementos de los elementos XML (también denominada *elementos XML personalizados*) que están incrustados en el documento.  
  
 Para obtener información general sobre cómo enlazar controles de host en las soluciones de Office a los datos, vea [enlazar datos a controles en soluciones de Office](../vsto/binding-data-to-controls-in-office-solutions.md).  
  
### <a name="using-the-windows-forms-data-binding-model"></a>Usar el modelo de enlace de datos de Windows Forms  
 La mayor parte de los controles de contenido admite el modelo simple de enlace de datos que usa Windows Forms. Un enlace de datos simple significa que un control se enlaza a un único elemento de datos, como un valor de una columna de una tabla de datos. Para obtener más información, consulta [Data Binding and Windows Forms](/dotnet/framework/winforms/data-binding-and-windows-forms).  
  
 En los proyectos de nivel de documento, puede enlazar datos a controles de contenido mediante el uso de la **orígenes de datos** ventana en [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. Para obtener más información sobre cómo agregar controles de contenido enlazados a datos a los documentos, consulte [Cómo: rellenar documentos con datos de una base de datos](../vsto/how-to-populate-documents-with-data-from-a-database.md) y [Cómo: rellenar documentos con datos de objetos](../vsto/how-to-populate-documents-with-data-from-objects.md).  
  
 En la tabla siguiente se enumera los controles de contenido que se pueden enlazar a cada tipo de datos en el **orígenes de datos** ventana.  
  
|Tipo de datos|Control de contenido predeterminado|Otros controles de contenido que se pueden enlazar a este tipo de datos|  
|---------------|-----------------------------|----------------------------------------------------------------|  
|<xref:System.Boolean><br /><br /> <xref:System.Byte><br /><br /> <xref:System.Char><br /><br /> <xref:System.Double><br /><br /> <xref:System.Enum><br /><br /> <xref:System.Guid><br /><br /> <xref:System.Int16><br /><br /> <xref:System.Int32><br /><br /> <xref:System.Int64><br /><br /> <xref:System.SByte><br /><br /> <xref:System.Single><br /><br /> <xref:System.String><br /><br /> <xref:System.TimeSpan><br /><br /> <xref:System.UInt16><br /><br /> <xref:System.UInt32><br /><br /> <xref:System.UInt64>|<xref:Microsoft.Office.Tools.Word.PlainTextContentControl>|<xref:Microsoft.Office.Tools.Word.BuildingBlockGalleryContentControl><br /><br /> <xref:Microsoft.Office.Tools.Word.ComboBoxContentControl><br /><br /> <xref:Microsoft.Office.Tools.Word.DatePickerContentControl><br /><br /> <xref:Microsoft.Office.Tools.Word.RichTextContentControl>|  
|<xref:System.DateTime>|<xref:Microsoft.Office.Tools.Word.DatePickerContentControl>|<xref:Microsoft.Office.Tools.Word.BuildingBlockGalleryContentControl><br /><br /> <xref:Microsoft.Office.Tools.Word.ComboBoxContentControl><br /><br /> <xref:Microsoft.Office.Tools.Word.PlainTextContentControl><br /><br /> <xref:Microsoft.Office.Tools.Word.RichTextContentControl>|  
|<xref:System.Drawing.Image><br /><br /> Matriz <xref:System.Byte>|<xref:Microsoft.Office.Tools.Word.PictureContentControl>|Ninguna|  
  
 En los proyectos de nivel de documento y de complemento de VSTO puede enlazar un control de contenido a un origen de datos mediante programación con el método <xref:System.Windows.Forms.ControlBindingsCollection.Add%2A> de la propiedad <xref:System.Windows.Forms.IBindableComponent.DataBindings%2A> del control. Si lo hace, pase la cadena **texto** a la *propertyName* parámetro de la <xref:System.Windows.Forms.ControlBindingsCollection.Add%2A> método. El **texto** propiedad es la propiedad de enlace de datos predeterminada de los controles de contenido.  
  
 Los controles de contenido también admiten el enlace de datos bidireccional, mediante el cual los cambios que se efectúan en el control se actualizan en el origen de datos. Para obtener más información, consulta [How to: Update a Data Source with Data from a Host Control](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md).  
  
> [!NOTE]  
>  Los controles de contenido no admiten el enlace de datos complejo. Si enlaza un control <xref:Microsoft.Office.Tools.Word.DropDownListContentControl> o <xref:Microsoft.Office.Tools.Word.ComboBoxContentControl> a un origen de datos mediante el modelo de datos de Windows Forms, los usuarios solo verán un valor único cuando hagan clic en el control. Si desea enlazar estos controles a un conjunto de valores de datos que los usuarios pueden elegir, puede enlazarlos a los elementos de un elemento XML personalizado.  
  
### <a name="binding-content-controls-to-custom-xml-parts"></a>Enlazar controles de contenido a elementos XML personalizados  
 Puede enlazar algunos controles de contenido a los elementos XML personalizados que están insertados en el documento. Para obtener más información acerca de los elementos XML personalizados, vea [información general sobre elementos XML personalizados](../vsto/custom-xml-parts-overview.md).  
  
 Para enlazar un control de contenido a un elemento en un elemento XML personalizado, use la **XMLMapping** propiedad del control. En el siguiente ejemplo de código se muestra cómo se enlaza un control <xref:Microsoft.Office.Tools.Word.PlainTextContentControl> al elemento `Price` situado bajo el nodo `Product` de un elemento XML personalizado que ya se ha agregado al documento.  
  
```vb  
plainTextContentControl1.XMLMapping.SetMapping("/Product/Price")  
```  
  
```csharp  
plainTextContentControl1.XMLMapping.SetMapping("/Product/Price", String.Empty, null);  
```  
  
 Para ver un tutorial que muestra cómo enlazar controles de contenido a elementos XML personalizados con más detalle, consulte [Tutorial: enlazar controles de contenido a elementos XML personalizados](../vsto/walkthrough-binding-content-controls-to-custom-xml-parts.md).  
  
 Al enlazar un control de contenido a un elemento XML personalizado, se habilita automáticamente el enlace de datos bidireccional. Si un usuario edita el texto del control, los elementos XML correspondientes se actualizan automáticamente. De igual forma, si se modifican los valores de los elementos XML personalizados, los controles de contenido que están enlazados a los elementos XML mostrarán los nuevos datos.  
  
 Puede enlazar los siguientes tipos de controles de contenido a elementos XML personalizados:  
  
-   <xref:Microsoft.Office.Tools.Word.ComboBoxContentControl>  
  
-   <xref:Microsoft.Office.Tools.Word.DatePickerContentControl>  
  
-   <xref:Microsoft.Office.Tools.Word.DropDownListContentControl>  
  
-   <xref:Microsoft.Office.Tools.Word.PictureContentControl>  
  
-   <xref:Microsoft.Office.Tools.Word.PlainTextContentControl>  
  
### <a name="data-binding-events-for-content-controls"></a>Eventos de enlace de datos de controles de contenido  
 Todos los controles de contenido proporcionan un conjunto de eventos que puede controlar para llevar a cabo tareas relacionadas con datos, como validar que el texto de un control cumple determinados criterios antes de actualizar el origen de datos. En la siguiente tabla se enumeran los eventos de los controles de contenido que están relacionados con el enlace de datos.  
  
|Tarea|Evento|  
|----------|-----------|  
|Ejecutar código inmediatamente antes de que Word actualice automáticamente el texto de un control de contenido que está enlazado a un elemento XML personalizado.|<xref:Microsoft.Office.Tools.Word.ContentControlBase.ContentUpdating>|  
|Ejecutar código inmediatamente antes de que Word actualice automáticamente los datos de un elemento XML personalizado que está enlazado a un control de contenido (es decir, después de modificar el texto en el control de contenido).|<xref:Microsoft.Office.Tools.Word.ContentControlBase.StoreUpdating>|  
|Ejecutar su propio código para validar el contenido del control según unos criterios personalizados.|<xref:Microsoft.Office.Tools.Word.ContentControlBase.Validating>|  
|Ejecutar el código una vez que se haya validado correctamente el contenido del control.|<xref:Microsoft.Office.Tools.Word.ContentControlBase.Validated>|  
  
## <a name="limitations-of-content-controls"></a>Limitaciones de los controles de contenido  
 Al usar controles de contenido en los proyectos de Office, tenga en cuenta las siguientes limitaciones.  
  
### <a name="behavior-differences-between-design-time-and-run-time"></a>Diferencias de comportamiento entre tiempo de diseño y tiempo de ejecución  
 Muchas de las limitaciones que Microsoft Office Word impone a los controles de contenido en tiempo de ejecución no se aplican en tiempo de diseño. Al diseñar la interfaz de usuario de una solución de nivel de documento en [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], asegúrese de que los cambios que efectúa en los controles de contenido se admiten en tiempo de ejecución.  
  
 Si modifica un control de contenido en tiempo de diseño de forma que el control no se admite en tiempo de ejecución, el diseñador de [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] no le avisará de que los cambios no se admiten. Sin embargo, al depurar o ejecutar el proyecto, o si guarda y vuelve a abrir el proyecto, Word mostrará un mensaje de error y un permiso de solicitud para reparar el documento. Al reparar el documento, Word quitará todo el contenido y el formato no admitido del control.  
  
 Por ejemplo, Word no impide que se agregue una tabla a un control <xref:Microsoft.Office.Tools.Word.PlainTextContentControl> en tiempo de diseño. Sin embargo, dado que los objetos <xref:Microsoft.Office.Tools.Word.PlainTextContentControl> no pueden contener tablas en tiempo de ejecución, Word mostrará un mensaje de error cuando se abra el documento.  
  
 Tenga en cuenta también que muchas propiedades que definen el comportamiento de los controles de contenido no tienen ningún efecto en tiempo de diseño. Por ejemplo, si establece la **LockContents** propiedad de un control de contenido **True** en tiempo de diseño, todavía puede editar texto en el control en el [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] diseñador. Esta propiedad solo impide que los usuarios editen el control en tiempo de ejecución.  
  
### <a name="event-limitations"></a>Limitaciones de los eventos  
 Los controles de contenido no proporcionan ningún evento que se produzca cuando el usuario cambia el texto u otros elementos del control. Por ejemplo, no hay ningún evento que se produzca cuando un usuario selecciona un elemento distinto en un control <xref:Microsoft.Office.Tools.Word.DropDownListContentControl> o <xref:Microsoft.Office.Tools.Word.ComboBoxContentControl>.  
  
 Para determinar cuándo un usuario edita el contenido de un control de contenido, puede enlazar el control a un elemento XML personalizado y controlar el evento <xref:Microsoft.Office.Tools.Word.ContentControlBase.StoreUpdating>. Este evento se desencadena cuando el usuario cambia el contenido de un control que está enlazado a un elemento XML personalizado. Para ver un tutorial que muestra cómo enlazar un control de contenido a un elemento XML personalizado, vea [Tutorial: enlazar controles de contenido a elementos XML personalizados](../vsto/walkthrough-binding-content-controls-to-custom-xml-parts.md).  
  
###  <a name="checkbox"></a>Controles de contenido de casilla en proyectos de Word  
 Word 2010 introdujo un nuevo tipo de control de contenido que representa una casilla. Sin embargo, la [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] no proporciona un tipo de CheckBoxContentControl correspondiente para su uso en proyectos de Office. Para crear un control de contenido de casilla en un proyecto de [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)] o de Word 2010, use el método <xref:Microsoft.Office.Tools.Word.ControlCollection.AddContentControl%2A> para crear un objeto <xref:Microsoft.Office.Tools.Word.ContentControl> y pase el valor <xref:Microsoft.Office.Interop.Word.WdContentControlType.wdContentControlCheckBox> al método para especificar un control de contenido de casilla. En el ejemplo de código siguiente se muestra cómo utilizar este recurso.  
  
 [!code-vb[Trin_ContentControlReference#800](../vsto/codesnippet/VisualBasic/trin_contentcontrolreference/checkbox.vb#800)]
 [!code-csharp[Trin_ContentControlReference#800](../vsto/codesnippet/CSharp/trin_wordcontentcontrolreference/checkbox.cs#800)]  
  
## <a name="see-also"></a>Vea también  
 [Automatizar Word con objetos extendidos](../vsto/automating-word-by-using-extended-objects.md)   
 [Cómo: agregar controles de contenido a documentos de Word](../vsto/how-to-add-content-controls-to-word-documents.md)   
 [Tutorial: Crear una plantilla mediante controles de contenido](../vsto/walkthrough-creating-a-template-by-using-content-controls.md)   
 [Datos en soluciones de Office](../vsto/data-in-office-solutions.md)   
 [Enlazar datos a controles en soluciones de Office](../vsto/binding-data-to-controls-in-office-solutions.md)   
 [Limitaciones de programación de elementos y controles Host](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)  
