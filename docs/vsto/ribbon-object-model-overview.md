---
title: "Informaci&#243;n general sobre el modelo de objetos para la cinta de opciones | Microsoft Docs"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "Cinta [desarrollo de Office en Visual Studio], modelo de objetos"
ms.assetid: cae24f66-e980-41ee-a915-d4c8e03efbc1
caps.latest.revision: 75
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 74
---
# Informaci&#243;n general sobre el modelo de objetos para la cinta de opciones
  [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] expone un modelo de objetos fuertemente tipado que se puede utilizar para obtener y establecer propiedades de la Cinta en tiempo de ejecución.  Por ejemplo, puede rellenar controles de menú de forma dinámica o bien mostrar y ocultar controles contextualmente.  También puede agregar pestañas, grupos, y controles a una cinta, pero solo antes de la cinta se cargue la aplicación de Office.  Para obtener información, vea [Establecer propiedades que pasan a ser de solo lectura](#SettingReadOnlyProperties).  
  
 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]  
  
 Este modelo de objetos para la cinta de opciones se compone principalmente de la [clase Ribbon](#RibbonClass), [eventos Ribbon](#RibbonEvents) y [clases de controles de la cinta de opciones](#RibbonControlClasses).  
  
##  <a name="RibbonClass"></a> Clase Ribbon  
 Cuando agregue un nuevo elemento **Cinta \(diseñador visual\)** a un proyecto, Visual Studio agrega una clase **Ribbon** al proyecto.  La clase **Ribbon** hereda de la clase <xref:Microsoft.Office.Tools.Ribbon.RibbonBase>.  
  
 Esta clase aparece como clase parcial que se divide entre el archivo de código de la cinta de opciones y el archivo de código del diseñador de la cinta de opciones.  
  
##  <a name="RibbonEvents"></a> Eventos Ribbon  
 La clase **Ribbon** contiene los tres eventos siguientes:  
  
|Evento|Descripción|  
|------------|-----------------|  
|<xref:Microsoft.Office.Tools.Ribbon.RibbonBase.Load>|Se provoca cuando la aplicación de Office carga la personalización de la cinta de opciones.  Se agregará el controlador de eventos <xref:Microsoft.Office.Tools.Ribbon.OfficeRibbon.Load> automáticamente al archivo de código de la cinta de opciones.  Utilice este controlador de eventos para ejecutar código personalizado cuando se cargue la cinta.|  
|<xref:Microsoft.Office.Tools.Ribbon.RibbonBase.LoadImage>|Permite almacenar en caché las imágenes de la personalización de la cinta cuando se cargue la cinta.  Puede obtener una ligera mejora del rendimiento si escribe código para almacenar en caché las imágenes de la cinta en este controlador de eventos.  Para obtener más información, vea <xref:Microsoft.Office.Tools.Ribbon.OfficeRibbon.LoadImage>.|  
|<xref:Microsoft.Office.Tools.Ribbon.RibbonBase.Close>|Se genera cuando se cierra la instancia de la cinta de opciones.|  
  
##  <a name="RibbonControlClasses"></a> Controles de la cinta de opciones  
 El espacio de nombres <xref:Microsoft.Office.Tools.Ribbon> contiene un tipo para cada control que aparece en el grupo **Controles de la cinta de opciones de Office** del **Cuadro de herramientas**.  
  
 La tabla siguiente muestra el tipo para cada control `Ribbon` .  Para obtener una descripción de cada control, vea [Información general sobre la cinta de opciones](../vsto/ribbon-overview.md).  
  
|Nombre del control|Nombre de la clase|  
|------------------------|------------------------|  
|**Box**|<xref:Microsoft.Office.Tools.Ribbon.RibbonBox>|  
|**Button**|<xref:Microsoft.Office.Tools.Ribbon.RibbonButton>|  
|**ButtonGroup**|<xref:Microsoft.Office.Tools.Ribbon.RibbonButtonGroup>|  
|**CheckBox**|<xref:Microsoft.Office.Tools.Ribbon.RibbonCheckBox>|  
|**ComboBox**|<xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox>|  
|**DropDown**|<xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown>|  
|**EditBox**|<xref:Microsoft.Office.Tools.Ribbon.RibbonEditBox>|  
|**Gallery**|<xref:Microsoft.Office.Tools.Ribbon.RibbonGallery>|  
|**Agrupar**|<xref:Microsoft.Office.Tools.Ribbon.RibbonGroup>|  
|**Etiqueta**|<xref:Microsoft.Office.Tools.Ribbon.RibbonLabel>|  
|**Menú**|<xref:Microsoft.Office.Tools.Ribbon.RibbonMenu>|  
|**Separator**|<xref:Microsoft.Office.Tools.Ribbon.RibbonSeparator>|  
|**SplitButton**|<xref:Microsoft.Office.Tools.Ribbon.RibbonSplitButton>|  
|**Tab**|<xref:Microsoft.Office.Tools.Ribbon.RibbonTab>|  
|**ToggleButton**|<xref:Microsoft.Office.Tools.Ribbon.RibbonToggleButton>|  
  
 El espacio de nombres <xref:Microsoft.Office.Tools.Ribbon> utiliza el prefijo "Ribbon" para estos tipos a fin de evitar conflictos con los nombres de clases de control del espacio de nombres <xref:System.Windows.Forms>.  
  
 Al agregar un control al diseñador de la cinta de opciones, dicho diseñador declara la clase de ese control como un campo en el archivo de código del diseñador de la cinta de opciones.  
  
### Tareas comunes con las propiedades de los controles de la cinta de opciones  
 Cada control `Ribbon` contiene las propiedades que puede utilizar para realizar varias tareas, como asignar una etiqueta a un control, o mostrar y ocultar controles.  
  
 En algunos casos, las propiedades pasan a ser de solo lectura una vez cargada la cinta o tras agregar un control a un menú dinámico.  Para obtener más información, vea [Establecer propiedades que pasan a ser de solo lectura](#SettingReadOnlyProperties).  
  
 En la tabla siguiente se describen algunas de las tareas que puede realizar utilizando propiedades del control `Ribbon` .  
  
|En esta tarea:|Haga lo siguiente:|  
|--------------------|------------------------|  
|Ocultar o mostrar un control.|Utilice la propiedad Visible.|  
|Habilitar o deshabilitar un control.|Utilice la propiedad Enabled.|  
|Establecer el tamaño de un control.|Utilice la propiedad ControlSize.|  
|Obtener la imagen que aparece en un control.|Utilice la propiedad Image.|  
|Cambiar la etiqueta de un control.|Utilice la propiedad Label.|  
|Agregar datos definidos por el usuario a un control.|Utilice la propiedad Tag.|  
|Obtener los elementos de un control <xref:Microsoft.Office.Tools.Ribbon.RibbonBox>, <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown>, <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery> o<br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonSplitButton>.|Utilice la propiedad Items.|  
|Agregar elementos a un control <xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox>, <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown> o <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery>.|Utilice la propiedad Items.|  
|Agregar controles a <xref:Microsoft.Office.Tools.Ribbon.RibbonMenu>.|Utilice la propiedad Items.<br /><br /> Para agregar controles a <xref:Microsoft.Office.Tools.Ribbon.RibbonMenu> una vez cargada la cinta de opciones en la aplicación de Office, debe establecer la propiedad <xref:Microsoft.Office.Tools.Ribbon.RibbonMenu.Dynamic%2A> en **true** antes de cargar la cinta de opciones en la aplicación de Office.  Para obtener información, vea [Establecer propiedades que pasan a ser de solo lectura](#SettingReadOnlyProperties).|  
|Obtener el elemento seleccionado en <xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox>,<br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown> o <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery>.|Utilice la propiedad SelectedItem.  Para <xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox>, utilice la propiedad <xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox.Text%2A>.|  
|Obtener los grupos de una <xref:Microsoft.Office.Tools.Ribbon.RibbonTab>.|Utilice la propiedad <xref:Microsoft.Office.Tools.Ribbon.RibbonTab.Groups%2A>.|  
|Especificar el número de filas y columnas que aparecen en <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery>.|Utilice las propiedades <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery.RowCount%2A> y <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery.ColumnCount%2A>.|  
  
##  <a name="SettingReadOnlyProperties"></a> Establecer propiedades que pasan a ser de solo lectura  
 Algunas propiedades solo se pueden establecer antes de que se cargue la cinta.  Estas propiedades se establecen en tres lugares:  
  
-   En la ventana **Propiedades** de Visual Studio.  
  
-   En el constructor de la clase **Ribbon** .  
  
-   En el método CreateRibbonExtensibilityObject de la clase `ThisAddin`, `ThisWorkbook` o `ThisDocument` del proyecto.  
  
 Los menús dinámicos presentan algunas excepciones.  Puede crear nuevos controles, establecer sus propiedades, y después agregarlas a un menú dinámico en tiempo de ejecución, incluso después la cinta que contiene el menú.  
  
 Las propiedades de los controles que se agregan a un menú dinámico se pueden establecer en cualquier momento.  
  
 Para obtener más información, vea [Propiedades que pasan a ser de solo lectura](#ReadOnlyProperties).  
  
### Establecer propiedades en el constructor de la cinta de opciones  
 Puede establecer las propiedades de un control `Ribbon` en el constructor de la clase **Ribbon** .  Este código debe aparecer después de la llamada al método `InitializeComponent`.  En el ejemplo siguiente se agrega un nuevo botón a un grupo si la hora actual son las 17:00 Hora del Pacífico \(UTC\-8\) o más tarde.  
  
 Agregue el código siguiente:  
  
 [!code-csharp[Trin_Ribbon_ObjectModel#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_Ribbon_ObjectModel/CS/Ribbon1.Designer.cs#1)]
 [!code-vb[Trin_Ribbon_ObjectModel#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_Ribbon_ObjectModel/VB/Ribbon1.Designer.vb#1)]  
  
 En Visual C\# actualizados de Visual Studio 2008, el constructor aparece en el archivo de código de la cinta de opciones.  
  
 En proyectos de Visual Basic, o en Visual C\# creados en [!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)], el constructor aparece en el archivo de código del diseñador de la cinta de opciones.  Este archivo se denomina *YourRibbonItem*. Designer.cs o *YourRibbonItem*. Designer.vb.  Para ver este archivo en los proyectos de Visual Basic, primero debe hacer clic en el botón **Mostrar todos los archivos** en el Explorador de soluciones.  
  
### Establecer propiedades en el método CreateRibbonExtensibilityObject  
 Puede establecer las propiedades de `Ribbon` cuando reemplace el método CreateRibbonExtensibilityObject en `ThisAddin`, `ThisWorkbook`, o la clase `ThisDocument` del proyecto.  Para obtener más información sobre el método CreateRibbonExtensibilityObject, vea [Información general sobre la cinta de opciones](../vsto/ribbon-overview.md).  
  
 El ejemplo siguiente establece las propiedades de Ribbon en el método CreateRibbonExtensibilityObject de la clase `ThisWorkbook` de un proyecto de libro de Excel.  
  
 Agregue el código siguiente:  
  
 [!code-csharp[Trin_Ribbon_ObjectModel#2](../snippets/csharp/VS_Snippets_OfficeSP/Trin_Ribbon_ObjectModel/CS/ThisWorkbook.cs#2)]
 [!code-vb[Trin_Ribbon_ObjectModel#2](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_Ribbon_ObjectModel/VB/ThisWorkbook.vb#2)]  
  
###  <a name="ReadOnlyProperties"></a> Propiedades que pasan a ser de solo lectura  
 En la tabla siguiente se muestran propiedades que solo se pueden establecer antes de que se cargue la cinta de opciones.  
  
> [!NOTE]  
>  Es posible establecer en cualquier momento las propiedades de los controles de menús dinámicos.  Esta tabla no se aplica en ese caso.  
  
|Propiedad|Clase de control de la cinta de opciones|  
|---------------|----------------------------------------------|  
|**BoxStyle**|<xref:Microsoft.Office.Tools.Ribbon.RibbonBox>|  
|**ButtonType**|<xref:Microsoft.Office.Tools.Ribbon.RibbonSplitButton>|  
|**ColumnCount**|<xref:Microsoft.Office.Tools.Ribbon.RibbonGallery>|  
|**ControlId**|<xref:Microsoft.Office.Tools.Ribbon.RibbonTab>|  
|**DialogLauncher**|<xref:Microsoft.Office.Tools.Ribbon.RibbonGroup>|  
|**Dinámico**|<xref:Microsoft.Office.Tools.Ribbon.RibbonMenu>|  
|**Global**|<xref:Microsoft.Office.Tools.Ribbon.OfficeRibbon>|  
|**Groups**|<xref:Microsoft.Office.Tools.Ribbon.RibbonTab>|  
|**ImageName**|<xref:Microsoft.Office.Tools.Ribbon.RibbonButton><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonDialogLauncher><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonEditBox><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonMenu><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonSplitButton><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonToggleButton>|  
|**ItemSize**|<xref:Microsoft.Office.Tools.Ribbon.RibbonMenu><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonSplitButton>|  
|**MaxLength**|<xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonEditBox>|  
|**Nombre**|<xref:Microsoft.Office.Tools.Ribbon.RibbonComponent>|  
|**Posición**|<xref:Microsoft.Office.Tools.Ribbon.RibbonButton><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonCheckBox><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonGroup><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonMenu><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonSeparator><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonSplitButton><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonTab><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonToggleButton>|  
|**RibbonType**|<xref:Microsoft.Office.Tools.Ribbon.OfficeRibbon>|  
|**RowCount**|<xref:Microsoft.Office.Tools.Ribbon.RibbonGallery>|  
|**ShowItemImage**|<xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery>|  
|**ShowItemLabel**|<xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery>|  
|**ShowItemSelection**|<xref:Microsoft.Office.Tools.Ribbon.RibbonGallery>|  
|**SizeString**|<xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonEditBox>|  
|**StartFromScratch**|<xref:Microsoft.Office.Tools.Ribbon.OfficeRibbon>|  
|**Tabulaciones**|<xref:Microsoft.Office.Tools.Ribbon.OfficeRibbon>|  
|**Título**|<xref:Microsoft.Office.Tools.Ribbon.RibbonSeparator>|  
  
### Establecer propiedades para las cintas de opciones que aparecen en inspectores de Outlook  
 Nueva instancia de la cinta se crea cada vez que un usuario abre un inspector en el que aparece la cinta de opciones.  Sin embargo, puede establecer las propiedades enumeradas en la tabla anterior antes de la primera instancia de la cinta se crea.  Después de crear la primera instancia, estas propiedades pasan a ser de solo lectura porque la primera instancia define el archivo XML que utiliza Outlook para cargar la cinta.  
  
 Si tiene lógica condicional que establece cualquiera de estas propiedades en un valor distinto cuando otras instancias de la cinta se crean, este código no tendrá ningún efecto.  
  
> [!NOTE]  
>  Asegúrese de que la propiedad **Nombre** se establece para cada control que agregue a una cinta de opciones de Outlook.  Si agrega un control a una cinta de opciones de Outlook en tiempo de ejecución, debe establecer esta propiedad en el código.  Si agrega un control a una cinta de opciones de Outlook en tiempo de diseño, la propiedad Name se establece automáticamente.  
  
## Eventos de controles de la cinta de opciones  
 Cada clase de control contiene uno o varios eventos.  En la tabla siguiente se describen estos eventos.  
  
|Evento|Descripción|  
|------------|-----------------|  
|Click|Se produce al hacer clic en un control.|  
|TextChanged|Se produce cuando se cambia el texto de un cuadro de edición o cuadro combinado.|  
|ItemsLoading|Se produce cuando Office solicita la colección Items del control.  Office almacena la colección Items en memoria caché hasta que el código cambia las propiedades del control o se llama al método <xref:Microsoft.Office.Core.IRibbonUI.InvalidateControl%2A>.|  
|ButtonClick|Se produce al hacer clic en un botón de <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery> o <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown>.|  
|SelectionChanged|Se produce cuando cambia la selección de <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown> o <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery>.|  
|DialogLauncherClick|Se produce al hacer clic en el icono que inicia un cuadro de diálogo situado en la esquina inferior derecha de un grupo.|  
  
 Los controladores de estos eventos tienen los dos parámetros siguientes.  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|*sender*|Objeto <xref:System.Object> que representa el control que provocó el evento.|  
|*e*|Un objeto <xref:Microsoft.Office.Tools.Ribbon.RibbonControlEventArgs> que contiene un control <xref:Microsoft.Office.Core.IRibbonControl>.  Use este control para tener acceso a cualquier propiedad que no esté disponible en el modelo de objetos para la cinta de opciones que proporciona [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)].|  
  
## Vea también  
 [Obtener acceso a la cinta de opciones en tiempo de ejecución](../vsto/accessing-the-ribbon-at-run-time.md)   
 [Información general sobre la cinta de opciones](../vsto/ribbon-overview.md)   
 [Cómo: Iniciarse en la personalización de la cinta de opciones](../vsto/how-to-get-started-customizing-the-ribbon.md)   
 [Diseñador de la cinta de opciones](../vsto/ribbon-designer.md)   
 [Tutorial: Crear una pestaña personalizada usando el diseñador de la cinta de opciones](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)   
 [Tutorial: Actualizar los controles de una cinta de opciones en tiempo de ejecución](../vsto/walkthrough-updating-the-controls-on-a-ribbon-at-run-time.md)   
 [Personalizar una cinta de opciones para Outlook](../vsto/customizing-a-ribbon-for-outlook.md)   
 [Cómo: Personalizar una pestaña integrada](../vsto/how-to-customize-a-built-in-tab.md)   
 [Cómo: Agregar controles en la vista Backstage](../vsto/how-to-add-controls-to-the-backstage-view.md)   
 [Cómo: Exportar una cinta de opciones del diseñador de la cinta de opciones a XML de la cinta de opciones](../vsto/how-to-export-a-ribbon-from-the-ribbon-designer-to-ribbon-xml.md)   
 [Cómo: Mostrar errores de la interfaz de usuario](../vsto/how-to-show-add-in-user-interface-errors.md)  
  
  