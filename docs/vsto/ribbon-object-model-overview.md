---
title: Información general del modelo de objetos de la cinta
description: Obtenga información sobre cómo el motor en tiempo de ejecución de Visual Studio Tools para Office expone un modelo de objetos fuertemente tipados que puede usar para obtener y establecer las propiedades de los controles de la cinta de opciones en tiempo de ejecución.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Ribbon [Office development in Visual Studio], object model
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 6306b13cc40d8b93de734168fe1e6df92c256d21
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99888698"
---
# <a name="ribbon-object-model-overview"></a>Información general del modelo de objetos de la cinta
  [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]Expone un modelo de objetos fuertemente tipado que puede usar para obtener y establecer las propiedades de los controles de la cinta de opciones en tiempo de ejecución. Por ejemplo, puede rellenar dinámicamente los controles de menú o mostrar y ocultar controles de forma contextual. También puede Agregar pestañas, grupos y controles a una cinta de opciones, pero solo antes de que la aplicación de Office cargue la cinta de opciones. Para obtener más información, vea [establecer propiedades que pasan a ser de solo lectura](#SettingReadOnlyProperties).

 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]

 Este modelo de objetos de la cinta de opciones se compone principalmente de la [clase de cinta](#RibbonClass), [los eventos de cinta](#RibbonEvents)y [las clases de control de cinta](#RibbonControlClasses).

## <a name="ribbon-class"></a><a name="RibbonClass"></a> Ribbon (clase)
 Al agregar un nuevo elemento **cinta (diseñador visual)** a un proyecto, Visual Studio agrega una clase **Ribbon** al proyecto. La clase **Ribbon** hereda de la <xref:Microsoft.Office.Tools.Ribbon.RibbonBase> clase.

 Esta clase aparece como una clase parcial que se divide entre el archivo de código de la cinta de opciones y el archivo de código del diseñador de la cinta.

## <a name="ribbon-events"></a><a name="RibbonEvents"></a> Eventos de la cinta
 La clase **Ribbon** contiene los tres eventos siguientes:

|Evento|Descripción|
|-----------|-----------------|
|<xref:Microsoft.Office.Tools.Ribbon.RibbonBase.Load>|Se genera cuando la aplicación de Office carga la personalización de la cinta de opciones. El <xref:Microsoft.Office.Tools.Ribbon.OfficeRibbon.Load> controlador de eventos se agrega automáticamente al archivo de código de la cinta de opciones. Use este controlador de eventos para ejecutar código personalizado cuando se cargue la cinta de opciones.|
|<xref:Microsoft.Office.Tools.Ribbon.RibbonBase.LoadImage>|Permite almacenar en caché imágenes en la personalización de la cinta de opciones cuando se carga la cinta de opciones. Puede obtener una ligera mejora del rendimiento si escribe código para almacenar en caché las imágenes de la cinta de opciones en este controlador de eventos. Para obtener más información, vea <xref:Microsoft.Office.Tools.Ribbon.OfficeRibbon.LoadImage>.|
|<xref:Microsoft.Office.Tools.Ribbon.RibbonBase.Close>|Se genera cuando se cierra la instancia de la cinta de opciones.|

## <a name="ribbon-controls"></a><a name="RibbonControlClasses"></a> Controles de la cinta
 El <xref:Microsoft.Office.Tools.Ribbon> espacio de nombres contiene un tipo para cada control que se ve en el grupo controles de la cinta de opciones de **Office** del **cuadro de herramientas**.

 En la tabla siguiente se muestra el tipo de cada `Ribbon` control. Para obtener una descripción de cada control, vea [información general sobre la cinta](../vsto/ribbon-overview.md)de opciones.

|Nombre del control|Nombre de la clase|
|------------------|----------------|
|**Box**|<xref:Microsoft.Office.Tools.Ribbon.RibbonBox>|
|**Button**|<xref:Microsoft.Office.Tools.Ribbon.RibbonButton>|
|**ButtonGroup**|<xref:Microsoft.Office.Tools.Ribbon.RibbonButtonGroup>|
|**CheckBox**|<xref:Microsoft.Office.Tools.Ribbon.RibbonCheckBox>|
|**ComboBox**|<xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox>|
|**Plegable**|<xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown>|
|**EditBox**|<xref:Microsoft.Office.Tools.Ribbon.RibbonEditBox>|
|**Galería**|<xref:Microsoft.Office.Tools.Ribbon.RibbonGallery>|
|**Grupo**|<xref:Microsoft.Office.Tools.Ribbon.RibbonGroup>|
|**Label**|<xref:Microsoft.Office.Tools.Ribbon.RibbonLabel>|
|**Menú**|<xref:Microsoft.Office.Tools.Ribbon.RibbonMenu>|
|**Separador**|<xref:Microsoft.Office.Tools.Ribbon.RibbonSeparator>|
|**SplitButton**|<xref:Microsoft.Office.Tools.Ribbon.RibbonSplitButton>|
|**Tabulador**|<xref:Microsoft.Office.Tools.Ribbon.RibbonTab>|
|**ToggleButton**|<xref:Microsoft.Office.Tools.Ribbon.RibbonToggleButton>|

 El <xref:Microsoft.Office.Tools.Ribbon> espacio de nombres usa el prefijo "Ribbon" para estos tipos a fin de evitar un conflicto de nombres con los nombres de las clases de control del <xref:System.Windows.Forms> espacio de nombres.

 Al agregar un control al diseñador de la cinta de opciones, el diseñador de la cinta de opciones declara la clase de ese control como un campo en el archivo de código del diseñador de la cinta de opciones.

### <a name="common-tasks-using-the-properties-of-ribbon-controls"></a>Tareas comunes mediante las propiedades de los controles de la cinta de opciones
 Cada `Ribbon` control contiene propiedades que puede usar para realizar varias tareas, como asignar una etiqueta a un control u ocultar y mostrar controles.

 En algunos casos, las propiedades pasan a ser de solo lectura después de que se cargue la cinta o después de que se agregue un control a un menú dinámico. Para obtener más información, vea [establecer propiedades que pasan a ser de solo lectura](#SettingReadOnlyProperties).

 En la tabla siguiente se describen algunas de las tareas que puede realizar mediante `Ribbon` las propiedades del control.

|Para efectuar esta tarea:|Haga esto:|
|--------------------|--------------|
|Ocultar o mostrar un control.|Use la propiedad visible.|
|Habilitar o deshabilitar un control.|Use la propiedad Enabled.|
|Establezca el tamaño de un control.|Use la propiedad de control.|
|Obtiene la imagen que aparece en un control.|Use la propiedad Image.|
|Cambiar la etiqueta de un control.|Use la propiedad etiqueta.|
|Agregar datos definidos por el usuario a un control.|Use la propiedad Tag.|
|Obtener los elementos de un elemento <xref:Microsoft.Office.Tools.Ribbon.RibbonBox> , <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown> , <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery> o<br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonSplitButton> control.|Use la propiedad items.|
|Agregar elementos a un <xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox> <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown> control, o <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery> .|Use la propiedad items.|
|Agregue controles a un <xref:Microsoft.Office.Tools.Ribbon.RibbonMenu> .|Use la propiedad items.<br /><br /> Para agregar controles a <xref:Microsoft.Office.Tools.Ribbon.RibbonMenu> después de cargar la cinta de opciones en la aplicación de Office, debe establecer la <xref:Microsoft.Office.Tools.Ribbon.RibbonMenu.Dynamic%2A> propiedad en **true** antes de que se cargue la cinta de opciones en la aplicación de Office. Para obtener más información, vea [establecer propiedades que pasan a ser de solo lectura](#SettingReadOnlyProperties).|
|Obtiene el elemento seleccionado <xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox> de un objeto.<br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown>, o <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery> .|Use la propiedad SelectedItem. Para <xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox> , use la <xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox.Text%2A> propiedad.|
|Obtener los grupos en un <xref:Microsoft.Office.Tools.Ribbon.RibbonTab> .|Utilice la propiedad <xref:Microsoft.Office.Tools.Ribbon.RibbonTab.Groups%2A>.|
|Especifique el número de filas y columnas que aparecen en un <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery> .|Use las <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery.RowCount%2A> <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery.ColumnCount%2A> propiedades y.|

## <a name="set-properties-that-become-read-only"></a><a name="SettingReadOnlyProperties"></a> Establecer propiedades que pasan a ser de solo lectura
 Algunas propiedades solo se pueden establecer antes de que se cargue la cinta de opciones. Hay tres lugares para establecer estas propiedades:

- En la ventana **propiedades** de Visual Studio.

- En el constructor de la clase **Ribbon** .

- En el `CreateRibbonExtensibilityObject` método de la `ThisAddin` `ThisWorkbook` clase, o `ThisDocument` del proyecto.

  Los menús dinámicos proporcionan algunas excepciones. Puede crear nuevos controles, establecer sus propiedades y, a continuación, agregarlos a un menú dinámico en tiempo de ejecución, incluso después de que se cargue la cinta de opciones que contiene el menú.

  Las propiedades de los controles que se agregan a un menú dinámico se pueden establecer en cualquier momento.

  Para obtener más información, vea [propiedades que pasan a ser de solo lectura](#ReadOnlyProperties).

### <a name="set-properties-in-the-constructor-of-the-ribbon"></a>Establecer propiedades en el constructor de la cinta de opciones
 Puede establecer las propiedades de un `Ribbon` control en el constructor de la clase **Ribbon** . Este código debe aparecer después de la llamada al `InitializeComponent` método. En el ejemplo siguiente se agrega un botón nuevo a un grupo si la hora actual es 17:00 hora del Pacífico (UTC-8) o posterior.

 Agregue el código siguiente:

 [!code-csharp[Trin_Ribbon_ObjectModel#1](../vsto/codesnippet/CSharp/trin_Ribbon_objectmodel_dotnet4/Ribbon1.Designer.cs#1)]
 [!code-vb[Trin_Ribbon_ObjectModel#1](../vsto/codesnippet/VisualBasic/trin_Ribbon_objectmodel_dotnet4/Ribbon1.Designer.vb#1)]

 En los proyectos de Visual C# que se actualizaron desde Visual Studio 2008, el constructor aparece en el archivo de código de la cinta de opciones.

 En proyectos de Visual Basic, o en proyectos de Visual C# creados en [!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)] , el constructor aparece en el archivo de código del diseñador de la cinta de opciones. Este archivo se denomina *suElementoDeCinta*. Designer.cs o *suElementoDeCinta*. Designer. VB. Para ver este archivo en proyectos de Visual Basic, primero debe hacer clic en el botón **Mostrar todos los archivos** en explorador de soluciones.

### <a name="set-properties-in-the-createribbonextensibilityobject-method"></a>Establecer propiedades en el método CreateRibbonExtensibilityObject
 Puede establecer las propiedades de un `Ribbon` control cuando invalide el `CreateRibbonExtensibilityObject` método en la `ThisAddin` `ThisWorkbook` clase, o `ThisDocument` del proyecto. Para obtener más información sobre el `CreateRibbonExtensibilityObject` método, consulte [información general](../vsto/ribbon-overview.md)de la cinta de opciones.

 En el ejemplo siguiente se establecen las propiedades de la cinta de opciones en el `CreateRibbonExtensibilityObject` método de la `ThisWorkbook` clase de un proyecto de libro de Excel.

 Agregue el código siguiente:

 [!code-vb[Trin_Ribbon_ObjectModel#2](../vsto/codesnippet/VisualBasic/trin_Ribbon_objectmodel_dotnet4/ThisWorkbook.vb#2)]
 [!code-csharp[Trin_Ribbon_ObjectModel#2](../vsto/codesnippet/CSharp/trin_Ribbon_objectmodel_dotnet4/ThisWorkbook.cs#2)]

### <a name="properties-that-become-read-only"></a><a name="ReadOnlyProperties"></a> Propiedades que pasan a ser de solo lectura
 En la tabla siguiente se muestran las propiedades que solo se pueden establecer antes de que se cargue la cinta de opciones.

> [!NOTE]
> Puede establecer las propiedades de los controles en menús dinámicos en cualquier momento. Esta tabla no se aplica en ese caso.

|Propiedad|Ribbon (clase de control)|
|--------------|--------------------------|
|**BoxStyle**|<xref:Microsoft.Office.Tools.Ribbon.RibbonBox>|
|**ButtonType**|<xref:Microsoft.Office.Tools.Ribbon.RibbonSplitButton>|
|**NúmeroDeColumnas**|<xref:Microsoft.Office.Tools.Ribbon.RibbonGallery>|
|**ControlId**|<xref:Microsoft.Office.Tools.Ribbon.RibbonTab>|
|**DialogLauncher**|<xref:Microsoft.Office.Tools.Ribbon.RibbonGroup>|
|**Dinámica**|<xref:Microsoft.Office.Tools.Ribbon.RibbonMenu>|
|**Global**|<xref:Microsoft.Office.Tools.Ribbon.OfficeRibbon>|
|**Grupos**|<xref:Microsoft.Office.Tools.Ribbon.RibbonTab>|
|**ImageName**|<xref:Microsoft.Office.Tools.Ribbon.RibbonButton><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonDialogLauncher><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonEditBox><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonMenu><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonSplitButton><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonToggleButton>|
|**Items**|<xref:Microsoft.Office.Tools.Ribbon.RibbonMenu><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonSplitButton>|
|**MaxLength**|<xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonEditBox>|
|**Nombre**|<xref:Microsoft.Office.Tools.Ribbon.RibbonComponent>|
|**Position**|<xref:Microsoft.Office.Tools.Ribbon.RibbonButton><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonCheckBox><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonGroup><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonMenu><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonSeparator><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonSplitButton><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonTab><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonToggleButton>|
|**RibbonType**|<xref:Microsoft.Office.Tools.Ribbon.OfficeRibbon>|
|**Empleado**|<xref:Microsoft.Office.Tools.Ribbon.RibbonGallery>|
|**ShowItemImage**|<xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery>|
|**ShowItemLabel**|<xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery>|
|**ShowItemSelection**|<xref:Microsoft.Office.Tools.Ribbon.RibbonGallery>|
|**SizeString**|<xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonEditBox>|
|**StartFromScratch**|<xref:Microsoft.Office.Tools.Ribbon.OfficeRibbon>|
|**Pestañas**|<xref:Microsoft.Office.Tools.Ribbon.OfficeRibbon>|
|**Título**|<xref:Microsoft.Office.Tools.Ribbon.RibbonSeparator>|

### <a name="set-properties-for-ribbons-that-appear-in-outlook-inspectors"></a>Establecer propiedades para las cintas de opciones que aparecen en los inspectores de Outlook
 Cada vez que un usuario abre un inspector en el que aparece la cinta de opciones, se crea una nueva instancia de la cinta de opciones. Sin embargo, puede establecer las propiedades enumeradas en la tabla anterior solo antes de que se cree la primera instancia de la cinta de opciones. Una vez creada la primera instancia, estas propiedades pasan a ser de solo lectura, ya que la primera instancia define el archivo XML que Outlook usa para cargar la cinta de opciones.

 Si tiene lógica condicional que establece cualquiera de estas propiedades en un valor diferente cuando se crean otras instancias de la cinta, este código no tendrá ningún efecto.

> [!NOTE]
> Asegúrese de que la propiedad **nombre** esté establecida para cada control que agregue a una cinta de opciones de Outlook. Si agrega un control a una cinta de opciones de Outlook en tiempo de ejecución, debe establecer esta propiedad en el código. Si agrega un control a una cinta de opciones de Outlook en tiempo de diseño, la propiedad nombre se establece automáticamente.

## <a name="ribbon-control-events"></a>Eventos de control de la cinta
 Cada clase de control contiene uno o varios eventos. En la tabla siguiente se describen estos eventos.

|Evento|Descripción|
|-----------|-----------------|
|Haga clic|Se produce cuando se hace clic en un control.|
|TextChanged|Se produce cuando cambia el texto de un cuadro de edición o un cuadro combinado.|
|ItemsLoading|Se produce cuando Office solicita la colección de elementos del control. Office almacena en caché la colección de elementos hasta que el código cambia las propiedades del control o se llama al <xref:Microsoft.Office.Core.IRibbonUI.InvalidateControl%2A> método.|
|ButtonClick|Se produce cuando <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery> se hace clic en un botón de un o <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown> .|
|SelectionChanged|Se produce cuando cambia la selección de un <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown> o <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery> .|
|DialogLauncherClick|Se produce cuando se hace clic en el icono del iniciador del cuadro de diálogo situado en la esquina inferior derecha de un grupo.|

 Los controladores de eventos de estos eventos tienen los dos parámetros siguientes.

|Parámetro|Descripción|
|---------------|-----------------|
|*remitente*|Objeto <xref:System.Object> que representa el control que provocó el evento.|
|*e*|Un objeto <xref:Microsoft.Office.Tools.Ribbon.RibbonControlEventArgs> que contiene un control <xref:Microsoft.Office.Core.IRibbonControl>. Utilice este control para tener acceso a cualquier propiedad que no esté disponible en el modelo de objetos de la cinta de opciones proporcionado por [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] .|

## <a name="see-also"></a>Vea también
- [Obtener acceso a la cinta de opciones en tiempo de ejecución](../vsto/accessing-the-ribbon-at-run-time.md)
- [Información general sobre la cinta](../vsto/ribbon-overview.md)
- [Cómo: Introducción a la personalización de la cinta de opciones](../vsto/how-to-get-started-customizing-the-ribbon.md)
- [Diseñador de la cinta de opciones](../vsto/ribbon-designer.md)
- [Tutorial: crear una pestaña personalizada mediante el diseñador de la cinta de opciones](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)
- [Tutorial: actualizar los controles de una cinta de opciones en tiempo de ejecución](../vsto/walkthrough-updating-the-controls-on-a-ribbon-at-run-time.md)
- [Personalización de una cinta para Outlook](../vsto/customizing-a-ribbon-for-outlook.md)
- [Cómo: personalizar una pestaña integrada](../vsto/how-to-customize-a-built-in-tab.md)
- [Cómo: agregar controles a la vista backstage](../vsto/how-to-add-controls-to-the-backstage-view.md)
- [Cómo: exportar una cinta de opciones del diseñador de la cinta de opciones a XML de la cinta](../vsto/how-to-export-a-ribbon-from-the-ribbon-designer-to-ribbon-xml.md)
- [Cómo: Mostrar errores de la interfaz de usuario de complementos](../vsto/how-to-show-add-in-user-interface-errors.md)
