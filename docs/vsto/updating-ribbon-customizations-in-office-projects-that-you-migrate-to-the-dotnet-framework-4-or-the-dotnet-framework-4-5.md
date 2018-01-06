---
title: Actualizar las personalizaciones de la cinta de opciones en proyectos de Office migrados a .NET Framework 4 o .NET Framework 4.5 | Documentos de Microsoft
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords: Office projects [Office development in Visual Studio], migrating to .NET Framework 4
ms.assetid: 3b7c8ad4-a616-4b42-9d62-9658fdefe6a3
caps.latest.revision: "18"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: d2c7dfef925ff61255e57315a3980fa6a145c235
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="updating-ribbon-customizations-in-office-projects-that-you-migrate-to-the-net-framework-4-or-the-net-framework-45"></a>Actualizar las personalizaciones de la Cinta en los proyectos de Office migrados a .NET Framework 4 o .NET Framework 4.5
  Si el proyecto contiene una personalización de cinta que se creó mediante la **cinta (diseñador Visual)** de elementos de proyecto, debe realizar los siguientes cambios en el código del proyecto si se cambia la plataforma de destino a la [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] o más adelante.  
  
-   Modifique el código generado de la cinta.  
  
-   Modifique cualquier código que cree instancias de controles de la cinta en tiempo de ejecución, controle eventos de la cinta o establezca la posición de un componente de la cinta mediante programación.  
  
## <a name="updating-the-generated-ribbon-code"></a>Actualizar el código generado de la cinta  
 Si se cambia el marco de trabajo de destino del proyecto a [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] o una versión posterior, debe cambiar el código generado para el elemento de la cinta llevando a cabo los siguientes pasos. Los archivos de código que debe actualizar dependerán del lenguaje de programación y de cómo haya creado el proyecto:  
  
-   En proyectos de Visual Basic o en proyectos de Visual C# que haya creado en [!INCLUDE[vs_dev11_long](../sharepoint/includes/vs-dev11-long-md.md)] o [!INCLUDE[vs_dev10_long](../sharepoint/includes/vs-dev10-long-md.md)] realizar todos los pasos en el archivo de código subyacente de la cinta de opciones (*suElementoDeCinta*. Designer.cs o *suElementoDeCinta*. Designer.vb). Para ver el archivo de código subyacente en proyectos de Visual Basic, haga clic en el **mostrar todos los archivos** botón en **el Explorador de soluciones**.  
  
-   En proyectos de Visual C# que ha creado en Visual Studio 2008 y, a continuación, actualiza a [!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)], realice los dos primeros pasos en el archivo de código de la cinta de opciones (*suElementoDeCinta*.cs o *suElementoDeCinta*.vb), y Realice los pasos restantes en el archivo de código subyacente de la cinta de opciones.  
  
#### <a name="to-change-the-generated-ribbon-code"></a>Para cambiar el código generado de la cinta  
  
1.  Modifique la declaración de la clase Ribbon para que se derive de <xref:Microsoft.Office.Tools.Ribbon.RibbonBase> en lugar de Microsoft.Office.Tools.Ribbon.OfficeRibbon.  
  
2.  Modifique el constructor de la clase Ribbon tal como se muestra a continuación. Si ha agregado código propio al constructor, no cambie el código. En los proyectos de Visual Basic, modifique únicamente el constructor sin parámetros. Ignore el otro constructor.  
  
     En el siguiente ejemplo de código se muestra el constructor predeterminado de una clase Ribbon en un proyecto que tiene como destino .NET Framework 3.5.  
  
    ```vb  
    Public Sub New()  
        MyBase.New()  
        InitializeComponent()  
    End Sub  
    ```  
  
    ```csharp  
    public Ribbon1()  
    {  
        InitializeComponent();  
    }  
    ```  
  
     En el siguiente ejemplo de código se muestra el constructor predeterminado de una clase Ribbon en un proyecto que tiene como destino [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] o una versión posterior.  
  
    ```vb  
    Public Sub New()  
        MyBase.New(Globals.Factory.GetRibbonFactory())  
        InitializeComponent()  
    End Sub  
    ```  
  
    ```csharp  
    public Ribbon1()  
        : base(Globals.Factory.GetRibbonFactory())  
    {  
        InitializeComponent();  
    }  
    ```  
  
3.  En el método `InitializeComponent`, modifique cualquier código que construya un control de la cinta para que el código use en su lugar uno de los métodos de aplicación auxiliar del objeto <xref:Microsoft.Office.Tools.Ribbon.RibbonFactory>.  
  
    > [!NOTE]  
    >  En los proyectos de Visual C#, debe expandir el área denominada `Component Designer generated code` para ver el método `InitializeComponent`.  
  
     Por ejemplo, suponga que su archivo contiene la siguiente línea de código que crea una instancia de un <xref:Microsoft.Office.Tools.Ribbon.RibbonButton> denominado `button1` en un proyecto que tenga como destino .NET Framework 3.5.  
  
    ```vb  
    Me.button1 = New Microsoft.Office.Tools.Ribbon.RibbonButton()  
    ```  
  
    ```csharp  
    this.button1 = new Microsoft.Office.Tools.Ribbon.RibbonButton();  
    ```  
  
     En un proyecto que tenga como destino [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] o una versión posterior, debe usar el siguiente código en su lugar.  
  
    ```vb  
    Me.button1 = Me.Factory.CreateRibbonButton()  
    ```  
  
    ```csharp  
    this.button1 = this.Factory.CreateRibbonButton();  
    ```  
  
     Para obtener una lista completa de los métodos auxiliares para los controles de la cinta de opciones, vea [crear instancias de controles de cinta de opciones](#ribboncontrols).  
  
4.  En los proyectos de Visual C#, modifique cualquier línea de código en el método `InitializeComponent` que use un delegado de <xref:System.EventHandler%601> para que use un delegado de la cinta concreto en su lugar.  
  
     Por ejemplo, suponga que su archivo contiene la siguiente línea de código que controla el evento <xref:Microsoft.Office.Tools.Ribbon.RibbonButton.Click> en un proyecto que tenga como destino .NET Framework 3.5.  
  
<CodeContentPlaceHolder>8</CodeContentPlaceHolder>  
     En un proyecto que tenga como destino [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] o una versión posterior, debe usar el siguiente código en su lugar.  
  
<CodeContentPlaceHolder>9</CodeContentPlaceHolder>  
     Para obtener una lista completa de los delegados de la cinta de opciones, vea [controlar los eventos de Ribbon](#ribbonevents).  
  
5.  En los proyectos de Visual Basic, busque la clase `ThisRibbonCollection` al final del archivo. Modifique la declaración de esta clase para que deje de heredar de Microsoft.Office.Tools.Ribbon.RibbonReadOnlyCollection.  
  
##  <a name="ribboncontrols"></a>Crear instancias de controles de cinta de opciones  
 Debe modificar todo el código que cree instancias de forma dinámica de controles de la cinta. En proyectos que tengan como destino .NET Framework 3.5, los controles de la cinta son clases de las que se pueden crear instancias directamente en determinados escenarios. En los proyectos que tengan como destino [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] o una versión posterior, estas clases son interfaces de las que no se pueden crear instancias directamente. Debe crear los controles mediante métodos proporcionados por el objeto <xref:Microsoft.Office.Tools.Ribbon.RibbonFactory>.  
  
 Hay dos maneras de acceder al objeto <xref:Microsoft.Office.Tools.Ribbon.RibbonFactory>:  
  
-   Mediante el uso de la propiedad de fábrica de la clase Ribbon. Use este enfoque desde el código en la clase Ribbon.  
  
-   Mediante el método de Globals.Factory.GetRibbonFactory. Use este enfoque desde el código externo a la clase Ribbon. Para obtener más información acerca de la clase Globals, consulte [acceso Global a objetos en los proyectos de Office](../vsto/global-access-to-objects-in-office-projects.md).  
  
 En el siguiente ejemplo de código se muestra cómo crear un [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] en una clase Ribbon en un proyecto que tiene como destino <xref:Microsoft.Office.Tools.Ribbon.RibbonButton> o una versión posterior.  
  
<CodeContentPlaceHolder>10</CodeContentPlaceHolder>  
<CodeContentPlaceHolder>11</CodeContentPlaceHolder>  
 La siguiente tabla enumera los controles que puede crear mediante programación y el método a usar para crear los controles en proyectos que tengan como destino [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] o una versión posterior.  
  
|Control|El método RibbonFactory a usar en proyectos de la versión [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] y versiones posteriores|  
|-------------|---------------------------------------------------------------------------------------------------------------|  
|<xref:Microsoft.Office.Tools.Ribbon.RibbonButton>|<xref:Microsoft.Office.Tools.Ribbon.RibbonFactory.CreateRibbonButton%2A>|  
|<xref:Microsoft.Office.Tools.Ribbon.RibbonButtonGroup>|<xref:Microsoft.Office.Tools.Ribbon.RibbonFactory.CreateRibbonButtonGroup%2A>|  
|<xref:Microsoft.Office.Tools.Ribbon.RibbonCheckBox>|<xref:Microsoft.Office.Tools.Ribbon.RibbonFactory.CreateRibbonCheckBox%2A>|  
|<xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox>|<xref:Microsoft.Office.Tools.Ribbon.RibbonFactory.CreateRibbonComboBox%2A>|  
|<xref:Microsoft.Office.Tools.Ribbon.RibbonDialogLauncher>|<xref:Microsoft.Office.Tools.Ribbon.RibbonFactory.CreateRibbonDialogLauncher%2A>|  
|<xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown>:|<xref:Microsoft.Office.Tools.Ribbon.RibbonFactory.CreateRibbonDropDown%2A>|  
|<xref:Microsoft.Office.Tools.Ribbon.RibbonDropDownItem>|<xref:Microsoft.Office.Tools.Ribbon.RibbonFactory.CreateRibbonDropDownItem%2A>|  
|<xref:Microsoft.Office.Tools.Ribbon.RibbonEditBox>|<xref:Microsoft.Office.Tools.Ribbon.RibbonFactory.CreateRibbonEditBox%2A>|  
|<xref:Microsoft.Office.Tools.Ribbon.RibbonGallery>|<xref:Microsoft.Office.Tools.Ribbon.RibbonFactory.CreateRibbonGallery%2A>|  
|<xref:Microsoft.Office.Tools.Ribbon.RibbonGroup>|<xref:Microsoft.Office.Tools.Ribbon.RibbonFactory.CreateRibbonGroup%2A>|  
|<xref:Microsoft.Office.Tools.Ribbon.RibbonLabel>|<xref:Microsoft.Office.Tools.Ribbon.RibbonFactory.CreateRibbonLabel%2A>|  
|<xref:Microsoft.Office.Tools.Ribbon.RibbonManager>|<xref:Microsoft.Office.Tools.Ribbon.RibbonFactory.CreateRibbonManager%2A>|  
|<xref:Microsoft.Office.Tools.Ribbon.RibbonMenu>|<xref:Microsoft.Office.Tools.Ribbon.RibbonFactory.CreateRibbonMenu%2A>|  
|<xref:Microsoft.Office.Tools.Ribbon.RibbonSeparator>|<xref:Microsoft.Office.Tools.Ribbon.RibbonFactory.CreateRibbonSeparator%2A>|  
|<xref:Microsoft.Office.Tools.Ribbon.RibbonSplitButton>|<xref:Microsoft.Office.Tools.Ribbon.RibbonFactory.CreateRibbonSplitButton%2A>|  
|<xref:Microsoft.Office.Tools.Ribbon.RibbonTab>|<xref:Microsoft.Office.Tools.Ribbon.RibbonFactory.CreateRibbonTab%2A>|  
|<xref:Microsoft.Office.Tools.Ribbon.RibbonToggleButton>|<xref:Microsoft.Office.Tools.Ribbon.RibbonFactory.CreateRibbonToggleButton%2A>|  
  
##  <a name="ribbonevents"></a>Control de eventos de la cinta de opciones  
 Debe modificar cualquier código que controle los eventos de los controles Ribbon. En los proyectos que tengan como destino la versión .NET Framework 3.5, el delegado de <xref:System.EventHandler%601> genérico controla estos eventos. Ahora, en los proyectos que tengan como destino [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] o una versión posterior, otros delegados controlan estos eventos.  
  
 En la siguiente tabla se enumeran los eventos de Ribbon y los delegados que se asocian a ellos en proyectos que tengan como destino [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] o una versión posterior.  
  
|evento|Delegado a usar en proyectos de la versión [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] y posterior|  
|-----------|---------------------------------------------------------------------------------------------------|  
|Evento <xref:Microsoft.Office.Tools.Ribbon.OfficeRibbon.LoadImage> en una clase Ribbon generada|<xref:Microsoft.Office.Tools.Ribbon.RibbonLoadImageEventHandler>|  
|<xref:Microsoft.Office.Tools.Ribbon.OfficeRibbon.Load>|<xref:Microsoft.Office.Tools.Ribbon.RibbonUIEventHandler>|  
|<xref:Microsoft.Office.Tools.Ribbon.RibbonButton.Click><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonCheckBox.Click><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox.ItemsLoading><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox.TextChanged><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown.ButtonClick><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown.ItemsLoading><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown.SelectionChanged><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonEditBox.TextChanged><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery.ButtonClick><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery.Click><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery.ItemsLoading><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonGroup.DialogLauncherClick><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonMenu.ItemsLoading><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonSplitButton.Click><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonToggleButton.Click>|<xref:Microsoft.Office.Tools.Ribbon.RibbonControlEventHandler>|  
  
## <a name="setting-the-position-of-a-ribbon-component-programmatically"></a>Establecer mediante programación la posición de un componente de la cinta  
 Debe modificar cualquier código que establezca la posición de los grupos, pestañas o controles de la cinta. En los proyectos que tienen como destino .NET Framework 3.5, puede usar los métodos de la clase estática a Microsoft.Office.Tools.Ribbon.RibbonPosition AfterOfficeId y BeforeOfficeId para asignar la propiedad de posición de un grupo, la ficha o el control. En los proyectos que tengan como destino [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] o una versión posterior, debe acceder a estos métodos mediante la propiedad <xref:Microsoft.Office.Tools.Ribbon.RibbonFactory.RibbonPosition%2A> proporcionada por el objeto <xref:Microsoft.Office.Tools.Ribbon.RibbonFactory>.  
  
 Hay dos maneras de acceder al objeto <xref:Microsoft.Office.Tools.Ribbon.RibbonFactory>:  
  
-   Mediante el uso de la propiedad de fábrica de la clase Ribbon. Use este enfoque desde el código en la clase Ribbon.  
  
-   Mediante el método de Globals.Factory.GetRibbonFactory. Use este enfoque desde el código externo a la clase Ribbon. Para obtener más información acerca de la clase Globals, consulte [acceso Global a objetos en los proyectos de Office](../vsto/global-access-to-objects-in-office-projects.md).  
  
 En el ejemplo de código siguiente se muestra cómo establecer la propiedad de posición de una ficha en una clase Ribbon en un proyecto destinado a .NET Framework 3.5.  
  
```vb  
Me.tab1.Position = RibbonPosition.AfterOfficeId("TabHome")  
```  
  
```csharp  
this.tab1.Position = RibbonPosition.AfterOfficeId("TabHome");  
```  
  
 En el siguiente ejemplo de código se muestra la misma tarea en un proyecto que tenga como destino [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)].  
  
```vb  
Me.tab1.Position = Me.Factory.RibbonPosition.AfterOfficeId("TabHome")  
```  
  
```csharp  
this.tab1.Position = this.Factory.RibbonPosition.AfterOfficeId("TabHome");  
```  
  
## <a name="see-also"></a>Vea también  
 [Migrating Office Solutions to the .NET Framework 4 or later](../vsto/migrating-office-solutions-to-the-dotnet-framework-4-or-later.md)   
 [Diseñador de la cinta](../vsto/ribbon-designer.md)  
  
  