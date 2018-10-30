---
title: Información general sobre el modelo de objetos de cinta de opciones
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Ribbon [Office development in Visual Studio], object model
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 25e34dcb38685a885ae0730740c25e1cb502e15c
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49910594"
---
# <a name="ribbon-object-model-overview"></a>Información general sobre el modelo de objetos de cinta de opciones
  La [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] expone un modelo de objetos fuertemente tipados que puede usar para obtener y establecer las propiedades de controles de cinta de opciones en tiempo de ejecución. Por ejemplo, dinámicamente puede rellenar los controles de menú, o mostrar y ocultar controles contextualmente. También puede agregar pestañas, grupos y controles a una cinta de opciones, pero antes de que se carga la cinta de opciones mediante la aplicación de Office. Para obtener información, consulte [establecer las propiedades que se vuelven de solo lectura](#SettingReadOnlyProperties).  
  
 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]  
  
 Este modelo de objetos de la cinta de opciones consiste principalmente en el [clase Ribbon](#RibbonClass), [eventos de la cinta de opciones](#RibbonEvents), y [clases de controles de cinta de opciones](#RibbonControlClasses).  
  
##  <a name="RibbonClass"></a> Clase Ribbon  
 Cuando se agrega un nuevo **cinta (diseñador Visual)** elemento a un proyecto, Visual Studio agrega un **cinta** clase al proyecto. El **cinta** clase hereda de la <xref:Microsoft.Office.Tools.Ribbon.RibbonBase> clase.  
  
 Esta clase aparece como una clase parcial que se divide entre el archivo de código de la cinta de opciones y el archivo de código del Diseñador de cinta.  
  
##  <a name="RibbonEvents"></a> Eventos de Ribbon  
 El **cinta** clase contiene los siguientes tres eventos:  
  
|evento|Descripción|  
|-----------|-----------------|  
|<xref:Microsoft.Office.Tools.Ribbon.RibbonBase.Load>|Se genera cuando la personalización de la cinta de opciones de carga de la aplicación de Office. El <xref:Microsoft.Office.Tools.Ribbon.OfficeRibbon.Load> controlador de eventos se agrega automáticamente al archivo de código de cinta de opciones. Utilice este controlador de eventos para ejecutar código personalizado cuando se cargue la cinta de opciones.|  
|<xref:Microsoft.Office.Tools.Ribbon.RibbonBase.LoadImage>|Permite a las imágenes de la memoria caché en la personalización de la cinta de opciones cuando se cargue la cinta de opciones. Puede obtener una ligera mejora del rendimiento si escribe código para almacenar en caché las imágenes de la cinta de opciones en este controlador de eventos. Para obtener más información, consulta <xref:Microsoft.Office.Tools.Ribbon.OfficeRibbon.LoadImage>.|  
|<xref:Microsoft.Office.Tools.Ribbon.RibbonBase.Close>|Se genera cuando se cierra la instancia de la cinta de opciones.|  
  
##  <a name="RibbonControlClasses"></a> Controles de cinta de opciones  
 El <xref:Microsoft.Office.Tools.Ribbon> espacio de nombres contiene un tipo para cada control que se ve en el **controles de la cinta de Office** grupo de la **cuadro de herramientas**.  
  
 En la tabla siguiente se muestra el tipo para cada `Ribbon` control. Para obtener una descripción de cada control, vea [información general de la cinta de opciones](../vsto/ribbon-overview.md).  
  
|Nombre del control|Nombre de la clase|  
|------------------|----------------|  
|**Box**|<xref:Microsoft.Office.Tools.Ribbon.RibbonBox>|  
|**Button**|<xref:Microsoft.Office.Tools.Ribbon.RibbonButton>|  
|**Grupo de botones**|<xref:Microsoft.Office.Tools.Ribbon.RibbonButtonGroup>|  
|**CheckBox**|<xref:Microsoft.Office.Tools.Ribbon.RibbonCheckBox>|  
|**ComboBox**|<xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox>|  
|**Lista desplegable**|<xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown>|  
|**Cuadro de edición**|<xref:Microsoft.Office.Tools.Ribbon.RibbonEditBox>|  
|**Galería**|<xref:Microsoft.Office.Tools.Ribbon.RibbonGallery>|  
|**Grupo**|<xref:Microsoft.Office.Tools.Ribbon.RibbonGroup>|  
|**Label**|<xref:Microsoft.Office.Tools.Ribbon.RibbonLabel>|  
|**Menu**|<xref:Microsoft.Office.Tools.Ribbon.RibbonMenu>|  
|**Separator**|<xref:Microsoft.Office.Tools.Ribbon.RibbonSeparator>|  
|**SplitButton**|<xref:Microsoft.Office.Tools.Ribbon.RibbonSplitButton>|  
|**Tabulación**|<xref:Microsoft.Office.Tools.Ribbon.RibbonTab>|  
|**ToggleButton**|<xref:Microsoft.Office.Tools.Ribbon.RibbonToggleButton>|  
  
 El <xref:Microsoft.Office.Tools.Ribbon> espacio de nombres utiliza el prefijo "Ribbon" para estos tipos para evitar un conflicto de nombres con los nombres de clases de control en el <xref:System.Windows.Forms> espacio de nombres.  
  
 Cuando se agrega un control en el Diseñador de cinta, el Diseñador de cinta declara la clase de ese control como un campo en el archivo de código del Diseñador de cinta.  
  
### <a name="common-tasks-using-the-properties-of-ribbon-controls"></a>Tareas comunes mediante las propiedades de controles de cinta de opciones  
 Cada `Ribbon` control contiene propiedades que puede usar para realizar diversas tareas, como asignar una etiqueta a un control, u ocultar y mostrar los controles.  
  
 En algunos casos, las propiedades serán de solo lectura después de que se cargue la cinta de opciones o después de agregar un control a un menú dinámico. Para obtener más información, consulte [establecer las propiedades que se vuelven de solo lectura](#SettingReadOnlyProperties).  
  
 En la tabla siguiente se describe algunas de las tareas que puede realizar mediante `Ribbon` propiedades del control.  
  
|Para efectuar esta tarea:|Haga lo siguiente:|  
|--------------------|--------------|  
|Ocultar o mostrar un control.|Utilice la propiedad Visible.|  
|Habilitar o deshabilitar un control.|Utilice la propiedad Enabled.|  
|Establezca el tamaño de un control.|Use la propiedad ControlSize.|  
|Obtiene la imagen que aparece en un control.|Use la propiedad de imagen.|  
|Cambiar la etiqueta de un control.|Utilice la propiedad Label.|  
|Agregar datos definidos por el usuario a un control.|Utilice la propiedad Tag.|  
|Obtener los elementos de un <xref:Microsoft.Office.Tools.Ribbon.RibbonBox>, <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown>, <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery>, o<br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonSplitButton> control.|Utilice la propiedad Items.|  
|Agregar elementos a un <xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox>, <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown>, o <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery> control.|Utilice la propiedad Items.|  
|Agregar controles a un <xref:Microsoft.Office.Tools.Ribbon.RibbonMenu>.|Utilice la propiedad Items.<br /><br /> Para agregar controles a la <xref:Microsoft.Office.Tools.Ribbon.RibbonMenu> después de carga la cinta de opciones en la aplicación de Office, debe establecer el <xref:Microsoft.Office.Tools.Ribbon.RibbonMenu.Dynamic%2A> propiedad **true** antes de carga la cinta de opciones en la aplicación de Office. Para obtener información, consulte [establecer las propiedades que se vuelven de solo lectura](#SettingReadOnlyProperties).|  
|Obtener el elemento seleccionado de un <xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox>,<br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown>, o <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery>.|Use la propiedad SelectedItem. Para un <xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox>, utilice el <xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox.Text%2A> propiedad.|  
|Obtener los grupos de un <xref:Microsoft.Office.Tools.Ribbon.RibbonTab>.|Utilice la propiedad <xref:Microsoft.Office.Tools.Ribbon.RibbonTab.Groups%2A>.|  
|Especifique el número de filas y columnas que aparecen en un <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery>.|Use la <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery.RowCount%2A> y <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery.ColumnCount%2A> propiedades.|  
  
##  <a name="SettingReadOnlyProperties"></a> Establecer las propiedades que se vuelven de solo lectura  
 Algunas propiedades solo pueden establecerse antes de que cargue la cinta de opciones. Hay tres lugares para establecer estas propiedades:  
  
- En Visual Studio **propiedades** ventana.  
  
- En el constructor de la **cinta** clase.  
  
- En el `CreateRibbonExtensibilityObject` método de la `ThisAddin`, `ThisWorkbook`, o `ThisDocument` clase del proyecto.  
  
  Menús dinámicos proporcionan algunas excepciones. Puede crear nuevos controles, establecer sus propiedades y, a continuación, agregarlos a un menú dinámico en tiempo de ejecución, incluso una vez cargada la cinta de opciones que contiene el menú.  
  
  Propiedades de controles que agregue a un menú dinámico se pueden establecer en cualquier momento.  
  
  Para obtener más información, consulte [propiedades que se vuelven de solo lectura](#ReadOnlyProperties).  
  
### <a name="set-properties-in-the-constructor-of-the-ribbon"></a>Establecer propiedades en el constructor de la cinta de opciones  
 Puede establecer las propiedades de un `Ribbon` control en el constructor de la **cinta** clase. Este código debe aparecer después de llamar a la `InitializeComponent` método. El ejemplo siguiente agrega un nuevo botón a un grupo si la hora actual es 17:00 hora del Pacífico (UTC-8) o una versión posterior.  
  
 Agregue el código siguiente.  
  
 [!code-csharp[Trin_Ribbon_ObjectModel#1](../vsto/codesnippet/CSharp/trin_Ribbon_objectmodel_dotnet4/Ribbon1.Designer.cs#1)]
 [!code-vb[Trin_Ribbon_ObjectModel#1](../vsto/codesnippet/VisualBasic/trin_Ribbon_objectmodel_dotnet4/Ribbon1.Designer.vb#1)]  
  
 En proyectos de Visual C# que se actualizó desde Visual Studio 2008, el constructor aparece en el archivo de código de la cinta de opciones.  
  
 En proyectos de Visual Basic o en proyectos de Visual C# creados en [!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)], el constructor aparece en el archivo de código del Diseñador de cinta. Este archivo se denomina *suElementoDeCinta*. Designer.cs o *suElementoDeCinta*. Designer.vb. Para ver este archivo en proyectos de Visual Basic, primero debe hacer clic el **mostrar todos los archivos** botón en el Explorador de soluciones.  
  
### <a name="set-properties-in-the-createribbonextensibilityobject-method"></a>Establecer propiedades en el método CreateRibbonExtensibilityObject  
 Puede establecer las propiedades de un `Ribbon` controlar al invalidar el `CreateRibbonExtensibilityObject` método en el `ThisAddin`, `ThisWorkbook`, o `ThisDocument` clase del proyecto. Para obtener más información sobre la `CreateRibbonExtensibilityObject` método, consulte [información general de la cinta de opciones](../vsto/ribbon-overview.md).  
  
 El ejemplo siguiente establece las propiedades de la cinta de opciones en el `CreateRibbonExtensibilityObject` método de la `ThisWorkbook` clase de un proyecto de libro de Excel.  
  
 Agregue el código siguiente.  
  
 [!code-vb[Trin_Ribbon_ObjectModel#2](../vsto/codesnippet/VisualBasic/trin_Ribbon_objectmodel_dotnet4/ThisWorkbook.vb#2)]
 [!code-csharp[Trin_Ribbon_ObjectModel#2](../vsto/codesnippet/CSharp/trin_Ribbon_objectmodel_dotnet4/ThisWorkbook.cs#2)]  
  
###  <a name="ReadOnlyProperties"></a> Propiedades que se vuelven de solo lectura  
 La siguiente tabla muestra las propiedades que solo pueden establecerse antes de que cargue la cinta de opciones.  
  
> [!NOTE]  
>  Puede establecer las propiedades de los controles de menús dinámicos en cualquier momento. Esta tabla no se aplica en ese caso.  
  
|Property|Clase de control de la cinta de opciones|  
|--------------|--------------------------|  
|**BoxStyle**|<xref:Microsoft.Office.Tools.Ribbon.RibbonBox>|  
|**ButtonType**|<xref:Microsoft.Office.Tools.Ribbon.RibbonSplitButton>|  
|**ColumnCount**|<xref:Microsoft.Office.Tools.Ribbon.RibbonGallery>|  
|**ControlId**|<xref:Microsoft.Office.Tools.Ribbon.RibbonTab>|  
|**DialogLauncher**|<xref:Microsoft.Office.Tools.Ribbon.RibbonGroup>|  
|**Dinámico**|<xref:Microsoft.Office.Tools.Ribbon.RibbonMenu>|  
|**Global**|<xref:Microsoft.Office.Tools.Ribbon.OfficeRibbon>|  
|**Grupos**|<xref:Microsoft.Office.Tools.Ribbon.RibbonTab>|  
|**ImageName**|<xref:Microsoft.Office.Tools.Ribbon.RibbonButton><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonDialogLauncher><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonEditBox><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonMenu><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonSplitButton><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonToggleButton>|  
|**ItemSize**|<xref:Microsoft.Office.Tools.Ribbon.RibbonMenu><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonSplitButton>|  
|**MaxLength**|<xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonEditBox>|  
|**Name**|<xref:Microsoft.Office.Tools.Ribbon.RibbonComponent>|  
|**Posición**|<xref:Microsoft.Office.Tools.Ribbon.RibbonButton><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonCheckBox><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonGroup><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonMenu><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonSeparator><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonSplitButton><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonTab><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonToggleButton>|  
|**RibbonType**|<xref:Microsoft.Office.Tools.Ribbon.OfficeRibbon>|  
|**Recuento de filas**|<xref:Microsoft.Office.Tools.Ribbon.RibbonGallery>|  
|**ShowItemImage**|<xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery>|  
|**ShowItemLabel**|<xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery>|  
|**ShowItemSelection**|<xref:Microsoft.Office.Tools.Ribbon.RibbonGallery>|  
|**SizeString**|<xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonEditBox>|  
|**StartFromScratch**|<xref:Microsoft.Office.Tools.Ribbon.OfficeRibbon>|  
|**Pestañas**|<xref:Microsoft.Office.Tools.Ribbon.OfficeRibbon>|  
|**Título**|<xref:Microsoft.Office.Tools.Ribbon.RibbonSeparator>|  
  
### <a name="set-properties-for-ribbons-that-appear-in-outlook-inspectors"></a>Establecer las propiedades de las cintas de opciones que aparecen en los inspectores de Outlook  
 Cada vez que un usuario abre un Inspector en el que aparece la cinta de opciones, se crea una nueva instancia de la cinta de opciones. Sin embargo, puede establecer las propiedades enumeradas en la tabla anterior sólo antes de crea la primera instancia de la cinta de opciones. Después de la primera instancia se crea estas propiedades son de sólo lectura porque la primera instancia define el archivo XML que utiliza Outlook para cargar la cinta de opciones.  
  
 Si tiene lógica condicional que establece cualquiera de estas propiedades en un valor diferente cuando se crean otras instancias de la cinta de opciones, este código no tendrá ningún efecto.  
  
> [!NOTE]  
>  Asegúrese de que el **nombre** propiedad se establece para cada control que se agrega a una cinta de Outlook. Si agrega un control a una cinta de Outlook en tiempo de ejecución, debe establecer esta propiedad en el código. Si agrega un control a una cinta de Outlook en tiempo de diseño, se establece automáticamente la propiedad Name.  
  
## <a name="ribbon-control-events"></a>Eventos de control de la cinta de opciones  
 Cada clase de control contiene uno o varios eventos. En la tabla siguiente se describe estos eventos.  
  
|evento|Descripción|  
|-----------|-----------------|  
|Clic|Se produce cuando se hace clic en un control.|  
|TextChanged|Se produce cuando se cambia el texto de un cuadro de edición o cuadro combinado.|  
|ItemsLoading|Se produce cuando se solicita la colección de elementos del control de Office. Office almacena en caché la colección de elementos hasta que el código cambia las propiedades del control, o bien llamar el <xref:Microsoft.Office.Core.IRibbonUI.InvalidateControl%2A> método.|  
|ButtonClick|Se produce cuando un botón en un <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery> o <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown> se hace clic en.|  
|Evento SelectionChanged|Se produce cuando la selección en un <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown> o <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery> cambios.|  
|DialogLauncherClick|Se produce cuando se hace clic en el icono del selector de cuadro de diálogo en la esquina inferior derecha de un grupo.|  
  
 Los controladores de eventos para estos eventos tienen los dos parámetros siguientes.  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|*Remitente*|Un <xref:System.Object> que representa el control que provocó el evento.|  
|*e*|Un <xref:Microsoft.Office.Tools.Ribbon.RibbonControlEventArgs> que contiene un <xref:Microsoft.Office.Core.IRibbonControl>. Use este control para tener acceso a cualquier propiedad que no está disponible en el modelo de objetos de la cinta de opciones proporcionado la [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)].|  
  
## <a name="see-also"></a>Vea también  
 [Obtener acceso a la cinta de opciones en tiempo de ejecución](../vsto/accessing-the-ribbon-at-run-time.md)   
 [Información general de la cinta de opciones](../vsto/ribbon-overview.md)   
 [Cómo: empezar a personalizar la cinta de opciones](../vsto/how-to-get-started-customizing-the-ribbon.md)   
 [Diseñador de cinta](../vsto/ribbon-designer.md)   
 [Tutorial: Crear una pestaña personalizada usando el Diseñador de cinta de opciones](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)   
 [Tutorial: Actualizar los controles de una cinta en tiempo de ejecución](../vsto/walkthrough-updating-the-controls-on-a-ribbon-at-run-time.md)   
 [Personalizar una cinta de opciones para Outlook](../vsto/customizing-a-ribbon-for-outlook.md)   
 [Cómo: personalizar una pestaña integrada](../vsto/how-to-customize-a-built-in-tab.md)   
 [Cómo: agregar controles a la vista Backstage](../vsto/how-to-add-controls-to-the-backstage-view.md)   
 [Cómo: exportar una cinta desde el Diseñador de cinta al XML de cinta](../vsto/how-to-export-a-ribbon-from-the-ribbon-designer-to-ribbon-xml.md)   
 [Cómo: agregar en Mostrar errores de interfaz de usuario](../vsto/how-to-show-add-in-user-interface-errors.md)  
 