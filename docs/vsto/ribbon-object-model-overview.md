---
title: Información general sobre el modelo de objetos de la cinta de opciones
description: Obtenga información sobre cómo Visual Studio Tools tiempo de ejecución de Office expone un modelo de objetos fuertemente especificado que puede usar para obtener y establecer las propiedades de los controles de la cinta de opciones en tiempo de ejecución.
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
ms.openlocfilehash: f053e87f8cdfd2bdf87bbdf4b7d115f6d9bbec26
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/21/2021
ms.locfileid: "107823995"
---
# <a name="ribbon-object-model-overview"></a>Información general sobre el modelo de objetos de la cinta de opciones
  expone un modelo de objetos fuertemente tipo que puede usar para obtener y establecer las propiedades de los controles de la cinta de opciones [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] en tiempo de ejecución. Por ejemplo, puede rellenar dinámicamente controles de menú o mostrar y ocultar controles contextualmente. También puede agregar pestañas, grupos y controles a una cinta de opciones, pero solo antes de que la aplicación de Office cargue la cinta de opciones. Para obtener información, vea [Establecer propiedades que se convierten en de solo lectura.](#SettingReadOnlyProperties)

 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]

 Este modelo de objetos ribbon consta principalmente de las clases [de clase Ribbon](#RibbonClass), Eventos de cinta [de](#RibbonEvents)opciones y Clases de [control Ribbon](#RibbonControlClasses).

## <a name="ribbon-class"></a><a name="RibbonClass"></a> Clase Ribbon
 Al agregar un nuevo elemento **Ribbon (Visual Designer)** a un proyecto, Visual Studio clase **Ribbon** al proyecto. La **clase Ribbon** hereda de la clase <xref:Microsoft.Office.Tools.Ribbon.RibbonBase> .

 Esta clase aparece como una clase parcial que se divide entre el archivo de código de la cinta de opciones y el archivo de código del Diseñador de cinta de opciones.

## <a name="ribbon-events"></a><a name="RibbonEvents"></a> Eventos de la cinta de opciones
 La **clase Ribbon** contiene los tres eventos siguientes:

|Evento|Descripción|
|-----------|-----------------|
|<xref:Microsoft.Office.Tools.Ribbon.RibbonBase.Load>|Se genera cuando la aplicación de Office carga la personalización de la cinta de opciones. El controlador de eventos se agrega automáticamente al archivo de código <xref:Microsoft.Office.Tools.Ribbon.OfficeRibbon.Load> de la cinta de opciones. Use este controlador de eventos para ejecutar código personalizado cuando se cargue la cinta de opciones.|
|<xref:Microsoft.Office.Tools.Ribbon.RibbonBase.LoadImage>|Permite almacenar en caché imágenes en la personalización de la cinta cuando se carga la cinta de opciones. Puede obtener un ligero aumento del rendimiento si escribe código para almacenar en caché las imágenes de la cinta en este controlador de eventos. Para obtener más información, vea <xref:Microsoft.Office.Tools.Ribbon.OfficeRibbon.LoadImage>.|
|<xref:Microsoft.Office.Tools.Ribbon.RibbonBase.Close>|Se genera cuando se cierra la instancia de la cinta de opciones.|

## <a name="ribbon-controls"></a><a name="RibbonControlClasses"></a> Controles de cinta de opciones
 El espacio de nombres contiene un tipo para cada control que se ve en el grupo Controles de la cinta de opciones <xref:Microsoft.Office.Tools.Ribbon> de **Office** del cuadro **de herramientas**.

 En la tabla siguiente se muestra el tipo de cada `Ribbon` control. Para obtener una descripción de cada control, vea Información general [de la cinta de opciones.](../vsto/ribbon-overview.md)

|Nombre del control|Nombre de la clase|
|------------------|----------------|
|**Box**|<xref:Microsoft.Office.Tools.Ribbon.RibbonBox>|
|**Botón**|<xref:Microsoft.Office.Tools.Ribbon.RibbonButton>|
|**ButtonGroup**|<xref:Microsoft.Office.Tools.Ribbon.RibbonButtonGroup>|
|**CheckBox**|<xref:Microsoft.Office.Tools.Ribbon.RibbonCheckBox>|
|**ComboBox**|<xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox>|
|**Desplegable**|<xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown>|
|**EditBox**|<xref:Microsoft.Office.Tools.Ribbon.RibbonEditBox>|
|**Galería**|<xref:Microsoft.Office.Tools.Ribbon.RibbonGallery>|
|**Grupo**|<xref:Microsoft.Office.Tools.Ribbon.RibbonGroup>|
|**Label**|<xref:Microsoft.Office.Tools.Ribbon.RibbonLabel>|
|**Menú**|<xref:Microsoft.Office.Tools.Ribbon.RibbonMenu>|
|**Separador**|<xref:Microsoft.Office.Tools.Ribbon.RibbonSeparator>|
|**SplitButton**|<xref:Microsoft.Office.Tools.Ribbon.RibbonSplitButton>|
|**Tabulador**|<xref:Microsoft.Office.Tools.Ribbon.RibbonTab>|
|**ToggleButton**|<xref:Microsoft.Office.Tools.Ribbon.RibbonToggleButton>|

 El <xref:Microsoft.Office.Tools.Ribbon> espacio de nombres usa el prefijo "Ribbon" para estos tipos para evitar una colisión de nombres con los nombres de las clases de control en el espacio de nombres <xref:System.Windows.Forms> .

 Al agregar un control al Diseñador de cinta de opciones, el Diseñador de cinta de opciones declara la clase para ese control como un campo en el archivo de código del Diseñador de cinta de opciones.

### <a name="common-tasks-using-the-properties-of-ribbon-controls"></a>Tareas comunes que usan las propiedades de los controles de la cinta de opciones
 Cada control contiene propiedades que puede usar para realizar varias tareas, como asignar una etiqueta a un control o ocultar `Ribbon` y mostrar controles.

 En algunos casos, las propiedades se convierten en de solo lectura después de que se cargue la cinta de opciones o después de agregar un control a un menú dinámico. Para obtener más información, vea [Establecer propiedades que se convierten en de solo lectura.](#SettingReadOnlyProperties)

 En la tabla siguiente se describen algunas de las tareas que puede realizar mediante propiedades `Ribbon` de control.

|Para efectuar esta tarea:|Haga esto:|
|--------------------|--------------|
|Ocultar o mostrar un control.|Use la propiedad Visible.|
|Habilite o deshabilite un control.|Use la propiedad Enabled.|
|Establezca el tamaño de un control.|Use la propiedad ControlSize.|
|Obtiene la imagen que aparece en un control .|Use la propiedad Image.|
|Cambie la etiqueta de un control .|Use la propiedad Label.|
|Agregar datos definidos por el usuario a un control .|Use la propiedad Tag.|
|Obtener los elementos de <xref:Microsoft.Office.Tools.Ribbon.RibbonBox> , <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown> , <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery> o<br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonSplitButton> Control.|Use la propiedad Items.|
|Agregue elementos a <xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox> un control , o <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown> <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery> .|Use la propiedad Items.|
|Agregue controles a <xref:Microsoft.Office.Tools.Ribbon.RibbonMenu> un .|Use la propiedad Items.<br /><br /> Para agregar controles a después de cargar la cinta de opciones en la aplicación de Office, debe establecer la propiedad en true antes de que la cinta de opciones se cargue <xref:Microsoft.Office.Tools.Ribbon.RibbonMenu> en la aplicación de <xref:Microsoft.Office.Tools.Ribbon.RibbonMenu.Dynamic%2A> Office.  Para obtener información, vea [Establecer propiedades que se convierten en de solo lectura.](#SettingReadOnlyProperties)|
|Obtener el elemento seleccionado de <xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox> un objeto ,<br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown>, o <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery> .|Use la propiedad SelectedItem. Para , <xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox> use la <xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox.Text%2A> propiedad .|
|Obtiene los grupos de <xref:Microsoft.Office.Tools.Ribbon.RibbonTab> un .|Utilice la propiedad <xref:Microsoft.Office.Tools.Ribbon.RibbonTab.Groups%2A>.|
|Especifique el número de filas y columnas que aparecen en <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery> .|Use las <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery.RowCount%2A> propiedades <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery.ColumnCount%2A> y .|

## <a name="set-properties-that-become-read-only"></a><a name="SettingReadOnlyProperties"></a> Establecimiento de propiedades que se convierten en de solo lectura
 Algunas propiedades solo se pueden establecer antes de que se cargue la cinta de opciones. Hay tres lugares para establecer estas propiedades:

- En la Visual Studio **propiedades.**

- En el constructor de la **clase Ribbon.**

- En el `CreateRibbonExtensibilityObject` método de la clase , o del `ThisAddin` `ThisWorkbook` `ThisDocument` proyecto.

  Los menús dinámicos proporcionan algunas excepciones. Puede crear nuevos controles, establecer sus propiedades y, a continuación, agregarlas a un menú dinámico en tiempo de ejecución, incluso después de cargar la cinta de opciones que contiene el menú.

  Las propiedades de los controles que agregue a un menú dinámico se pueden establecer en cualquier momento.

  Para obtener más información, vea [Propiedades que se convierten en de solo lectura.](#ReadOnlyProperties)

### <a name="set-properties-in-the-constructor-of-the-ribbon"></a>Establecer propiedades en el constructor de la cinta de opciones
 Puede establecer las propiedades de un `Ribbon` control en el constructor de la clase **Ribbon.** Este código debe aparecer después de la llamada al `InitializeComponent` método . En el ejemplo siguiente se agrega un nuevo botón a un grupo si la hora actual es 17:00 Hora del Pacífico (UTC-8) o posterior.

 Agregue el código siguiente:

 :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_Ribbon_objectmodel_dotnet4/Ribbon1.Designer.cs" id="Snippet1":::
 :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_Ribbon_objectmodel_dotnet4/Ribbon1.Designer.vb" id="Snippet1":::

 En los proyectos de Visual C# que actualizó Visual Studio 2008, el constructor aparece en el archivo de código de la cinta de opciones.

 En Visual Basic o en los proyectos de Visual C# que creó en , el constructor aparece en el archivo de código del Diseñador de cinta [!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)] de opciones. Este archivo se denomina *YourRibbonItem.* Designer.cs o *YourRibbonItem*. Designer.vb. Para ver este archivo en Visual Basic proyectos, primero debe hacer clic en el botón **Mostrar** todos los archivos de Explorador de soluciones.

### <a name="set-properties-in-the-createribbonextensibilityobject-method"></a>Establecimiento de propiedades en el método CreateRibbonExtensibilityObject
 Puede establecer las propiedades de un control al invalidar el método `Ribbon` en la clase , o del `CreateRibbonExtensibilityObject` `ThisAddin` `ThisWorkbook` `ThisDocument` proyecto. Para obtener más información sobre el `CreateRibbonExtensibilityObject` método , vea Información general de la cinta de [opciones.](../vsto/ribbon-overview.md)

 En el ejemplo siguiente se establecen las propiedades de la cinta `CreateRibbonExtensibilityObject` de opciones en el método de la clase de un proyecto de libro de `ThisWorkbook` Excel.

 Agregue el código siguiente:

 :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_Ribbon_objectmodel_dotnet4/ThisWorkbook.vb" id="Snippet2":::
 :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_Ribbon_objectmodel_dotnet4/ThisWorkbook.cs" id="Snippet2":::

### <a name="properties-that-become-read-only"></a><a name="ReadOnlyProperties"></a> Propiedades que se convierten en de solo lectura
 En la tabla siguiente se muestran las propiedades que solo se pueden establecer antes de que se cargue la cinta de opciones.

> [!NOTE]
> Puede establecer las propiedades de los controles en los menús dinámicos en cualquier momento. Esta tabla no se aplica en ese caso.

|Propiedad|Clase de control Ribbon|
|--------------|--------------------------|
|**BoxStyle**|<xref:Microsoft.Office.Tools.Ribbon.RibbonBox>|
|**ButtonType**|<xref:Microsoft.Office.Tools.Ribbon.RibbonSplitButton>|
|**ColumnCount**|<xref:Microsoft.Office.Tools.Ribbon.RibbonGallery>|
|**ControlId**|<xref:Microsoft.Office.Tools.Ribbon.RibbonTab>|
|**DialogLauncher**|<xref:Microsoft.Office.Tools.Ribbon.RibbonGroup>|
|**Dinámica**|<xref:Microsoft.Office.Tools.Ribbon.RibbonMenu>|
|**Global**|<xref:Microsoft.Office.Tools.Ribbon.OfficeRibbon>|
|**Grupos**|<xref:Microsoft.Office.Tools.Ribbon.RibbonTab>|
|**ImageName**|<xref:Microsoft.Office.Tools.Ribbon.RibbonButton><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonDialogLauncher><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonEditBox><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonMenu><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonSplitButton><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonToggleButton>|
|**ItemSize**|<xref:Microsoft.Office.Tools.Ribbon.RibbonMenu><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonSplitButton>|
|**MaxLength**|<xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonEditBox>|
|**Nombre**|<xref:Microsoft.Office.Tools.Ribbon.RibbonComponent>|
|**Position**|<xref:Microsoft.Office.Tools.Ribbon.RibbonButton><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonCheckBox><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonGroup><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonMenu><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonSeparator><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonSplitButton><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonTab><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonToggleButton>|
|**RibbonType**|<xref:Microsoft.Office.Tools.Ribbon.OfficeRibbon>|
|**Rowcount**|<xref:Microsoft.Office.Tools.Ribbon.RibbonGallery>|
|**ShowItemImage**|<xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery>|
|**ShowItemLabel**|<xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery>|
|**ShowItemSelection**|<xref:Microsoft.Office.Tools.Ribbon.RibbonGallery>|
|**SizeString**|<xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonEditBox>|
|**StartFromScratch**|<xref:Microsoft.Office.Tools.Ribbon.OfficeRibbon>|
|**Pestañas**|<xref:Microsoft.Office.Tools.Ribbon.OfficeRibbon>|
|**Título**|<xref:Microsoft.Office.Tools.Ribbon.RibbonSeparator>|

### <a name="set-properties-for-ribbons-that-appear-in-outlook-inspectors"></a>Establecer las propiedades de las cintas de opciones que aparecen en los inspectores de Outlook
 Cada vez que un usuario abre un inspector en el que aparece la cinta de opciones, se crea una nueva instancia de la cinta. Sin embargo, puede establecer las propiedades enumeradas en la tabla anterior solo antes de que se cree la primera instancia de la cinta de opciones. Una vez creada la primera instancia, estas propiedades se convierten en de solo lectura porque la primera instancia define el archivo XML que Outlook usa para cargar la cinta de opciones.

 Si tiene lógica condicional que establece cualquiera de estas propiedades en un valor diferente cuando se crean otras instancias de la cinta de opciones, este código no tendrá ningún efecto.

> [!NOTE]
> Asegúrese de que **la propiedad** Nombre está establecida para cada control que agregue a una cinta de opciones de Outlook. Si agrega un control a una cinta de outlook en tiempo de ejecución, debe establecer esta propiedad en el código. Si agrega un control a una cinta de opciones de Outlook en tiempo de diseño, la propiedad Name se establece automáticamente.

## <a name="ribbon-control-events"></a>Eventos de control de cinta de opciones
 Cada clase de control contiene uno o varios eventos. En la tabla siguiente se describen estos eventos.

|Evento|Descripción|
|-----------|-----------------|
|Haga clic en|Se produce cuando se hace clic en un control .|
|TextChanged|Se produce cuando se cambia el texto de un cuadro de edición o un cuadro combinado.|
|ItemsLoading|Se produce cuando Office solicita la colección Items del control. Office almacena en caché la colección Items hasta que el código cambia las propiedades del control o se llama al <xref:Microsoft.Office.Core.IRibbonUI.InvalidateControl%2A> método .|
|ButtonClick|Se produce cuando se hace clic en <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery> un botón de o <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown> .|
|SelectionChanged|Se produce cuando cambia la selección en <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown> <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery> o .|
|DialogLauncherClick|Se produce cuando se hace clic en el icono del iniciador del cuadro de diálogo situado en la esquina inferior derecha de un grupo.|

 Los controladores de eventos para estos eventos tienen los dos parámetros siguientes.

|Parámetro|Descripción|
|---------------|-----------------|
|*Remitente*|Objeto <xref:System.Object> que representa el control que provocó el evento.|
|*e*|Un objeto <xref:Microsoft.Office.Tools.Ribbon.RibbonControlEventArgs> que contiene un control <xref:Microsoft.Office.Core.IRibbonControl>. Use este control para tener acceso a cualquier propiedad que no esté disponible en el modelo de objetos de la cinta de opciones proporcionado por [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] .|

## <a name="see-also"></a>Consulte también
- [Acceso a la cinta de opciones en tiempo de ejecución](../vsto/accessing-the-ribbon-at-run-time.md)
- [Información general sobre la cinta de opciones](../vsto/ribbon-overview.md)
- [Cómo: Introducción a la personalización de la cinta de opciones](../vsto/how-to-get-started-customizing-the-ribbon.md)
- [Diseñador de la cinta de opciones](../vsto/ribbon-designer.md)
- [Tutorial: Crear una pestaña personalizada mediante el Diseñador de cinta de opciones](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)
- [Tutorial: Actualización de los controles de una cinta de opciones en tiempo de ejecución](../vsto/walkthrough-updating-the-controls-on-a-ribbon-at-run-time.md)
- [Personalización de una cinta de opciones para Outlook](../vsto/customizing-a-ribbon-for-outlook.md)
- [Personalización de una pestaña integrada](../vsto/how-to-customize-a-built-in-tab.md)
- [Cómo: Agregar controles a la vista Backstage](../vsto/how-to-add-controls-to-the-backstage-view.md)
- [Cómo: Exportar una cinta de opciones desde el Diseñador de la cinta de opciones al XML de la cinta de opciones](../vsto/how-to-export-a-ribbon-from-the-ribbon-designer-to-ribbon-xml.md)
- [Cómo: Mostrar errores de la interfaz de usuario del complemento](../vsto/how-to-show-add-in-user-interface-errors.md)
