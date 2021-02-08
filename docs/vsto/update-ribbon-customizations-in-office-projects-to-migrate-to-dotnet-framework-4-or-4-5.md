---
title: Actualizar las personalizaciones de la cinta migradas a .NET Framework 4,5
description: Sepa que debe realizar cambios en el código del proyecto si la versión de .NET Framework de destino se cambia a la .NET Framework 4 o posterior.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office projects [Office development in Visual Studio], migrating to .NET Framework 4
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 684ec027f5e7615832a942edc93336bf91944b09
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99838313"
---
# <a name="update-ribbon-customizations-migrated-to-net-framework-45"></a>Actualizar las personalizaciones de la cinta migradas a .NET Framework 4,5

  Si el proyecto contiene una personalización de la cinta de opciones que se creó mediante el elemento de proyecto **cinta (diseñador visual)** , debe realizar los siguientes cambios en el código del proyecto si la versión de .NET Framework de destino se cambia a [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] o versiones posteriores.

- Modifique el código generado de la cinta.

- Modifique cualquier código que cree instancias de controles de la cinta de opciones en tiempo de ejecución, controle eventos de la cinta de opciones o establezca la posición de un componente de la cinta mediante programación.

## <a name="update-the-generated-ribbon-code"></a>Actualizar el código de cinta generado
 Si se cambia el marco de trabajo de destino del proyecto a [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] o una versión posterior, debe cambiar el código generado para el elemento de la cinta llevando a cabo los siguientes pasos. Los archivos de código que debe actualizar dependerán del lenguaje de programación y de cómo haya creado el proyecto:

- En proyectos de Visual Basic o en proyectos de Visual C# creados en [!INCLUDE[vs_dev11_long](../sharepoint/includes/vs-dev11-long-md.md)] o [!INCLUDE[vs_dev10_long](../sharepoint/includes/vs-dev10-long-md.md)] realice todos los pasos del archivo de código subyacente de la cinta de opciones (*suElementoDeCinta*. Designer.cs o *suElementoDeCinta*. Designer. VB). Para ver el archivo de código subyacente en proyectos de Visual Basic, haga clic en el botón **Mostrar todos los archivos** en **Explorador de soluciones**.

- En los proyectos de Visual C# creados en Visual Studio 2008 y después actualizados a [!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)] , realice los dos primeros pasos en el archivo de código de la cinta de opciones (*suElementoDeCinta*. cs o *suElementoDeCinta*. VB) y realice los pasos restantes en el archivo de código subyacente de la cinta de opciones.

### <a name="to-change-the-generated-ribbon-code"></a>Para cambiar el código generado de la cinta

1. Modifique la declaración de la clase Ribbon para que se derive a partir de <xref:Microsoft.Office.Tools.Ribbon.RibbonBase> en lugar de a partir de `Microsoft.Office.Tools.Ribbon.OfficeRibbon`.

2. Modifique el constructor de la clase Ribbon tal como se muestra a continuación. Si ha agregado código propio al constructor, no cambie el código. En los proyectos de Visual Basic, modifique únicamente el constructor sin parámetros. Ignore el otro constructor.

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

3. En el método `InitializeComponent`, modifique cualquier código que construya un control de la cinta para que el código use en su lugar uno de los métodos del asistente del objeto <xref:Microsoft.Office.Tools.Ribbon.RibbonFactory>.

    > [!NOTE]
    > En los proyectos de Visual C#, debe expandir el área denominada `Component Designer generated code` para ver el método `InitializeComponent`.

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

     Para obtener una lista completa de los métodos auxiliares para los controles de la cinta de opciones, vea [crear instancias de controles](#ribboncontrols)de la cinta de opciones.

4. En los proyectos de Visual C#, modifique cualquier línea de código en el método `InitializeComponent` que use un delegado de <xref:System.EventHandler%601> para que use un delegado de la cinta concreto en su lugar.

     Por ejemplo, suponga que su archivo contiene la siguiente línea de código que controla el evento <xref:Microsoft.Office.Tools.Ribbon.RibbonButton.Click> en un proyecto que tenga como destino .NET Framework 3.5.

    \<CodeContentPlaceHolder>8 </CodeContentPlaceHolder> en un proyecto que tiene como destino [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] o una versión posterior, debe usar el código siguiente en su lugar.

    \<CodeContentPlaceHolder>9 </CodeContentPlaceHolder> para obtener una lista completa de los delegados de la cinta, consulte [controlar eventos de cinta](#ribbonevents).

5. En los proyectos de Visual Basic, busque la clase `ThisRibbonCollection` al final del archivo. Modifique la declaración de esta clase para que deje de heredar de `Microsoft.Office.Tools.Ribbon.RibbonReadOnlyCollection`.

## <a name="instantiate-ribbon-controls"></a><a name="ribboncontrols"></a> Crear instancias de controles de la cinta
 Debe modificar todo el código que cree instancias de forma dinámica de controles de la cinta. En proyectos que tengan como destino .NET Framework 3.5, los controles de la cinta son clases de las que se pueden crear instancias directamente en determinados escenarios. En los proyectos que tengan como destino [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] o una versión posterior, estas clases son interfaces de las que no se pueden crear instancias directamente. Debe crear los controles mediante métodos proporcionados por el objeto <xref:Microsoft.Office.Tools.Ribbon.RibbonFactory>.

 Hay dos maneras de acceder al objeto <xref:Microsoft.Office.Tools.Ribbon.RibbonFactory>:

- Mediante el uso de la propiedad Factory de la clase Ribbon. Use este enfoque desde el código en la clase Ribbon.

- Usando el método `Globals.Factory.GetRibbonFactory`. Use este enfoque desde el código externo a la clase Ribbon. Para obtener más información sobre la clase Globals, consulte [acceso global a objetos en proyectos de Office](../vsto/global-access-to-objects-in-office-projects.md).

  En el siguiente ejemplo de código se muestra cómo crear un [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] en una clase Ribbon en un proyecto que tiene como destino <xref:Microsoft.Office.Tools.Ribbon.RibbonButton> o una versión posterior.

\<CodeContentPlaceHolder>10 </CodeContentPlaceHolder> 
 \<CodeContentPlaceHolder> 11 en </CodeContentPlaceHolder> la tabla siguiente se enumeran los controles que se pueden crear mediante programación y el método que se va a usar para crear los controles en proyectos que tienen como destino [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] o una versión posterior.

|Control|El método RibbonFactory a usar en proyectos de la versión [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] y versiones posteriores|
|-------------| - |
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

## <a name="handle-ribbon-events"></a><a name="ribbonevents"></a> Controlar eventos de la cinta
 Debe modificar cualquier código que controle los eventos de los controles Ribbon. En los proyectos que tengan como destino la versión .NET Framework 3.5, el delegado de <xref:System.EventHandler%601> genérico controla estos eventos. Ahora, en los proyectos que tengan como destino [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] o una versión posterior, otros delegados controlan estos eventos.

 En la siguiente tabla se enumeran los eventos de Ribbon y los delegados que se asocian a ellos en proyectos que tengan como destino [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] o una versión posterior.

|Evento|Delegado a usar en proyectos de la versión [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] y posterior|
|-----------| - |
|Evento <xref:Microsoft.Office.Tools.Ribbon.OfficeRibbon.LoadImage> en una clase Ribbon generada|<xref:Microsoft.Office.Tools.Ribbon.RibbonLoadImageEventHandler>|
|<xref:Microsoft.Office.Tools.Ribbon.OfficeRibbon.Load>|<xref:Microsoft.Office.Tools.Ribbon.RibbonUIEventHandler>|
|<xref:Microsoft.Office.Tools.Ribbon.RibbonButton.Click><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonCheckBox.Click><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox.ItemsLoading><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox.TextChanged><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown.ButtonClick><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown.ItemsLoading><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown.SelectionChanged><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonEditBox.TextChanged><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery.ButtonClick><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery.Click><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery.ItemsLoading><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonGroup.DialogLauncherClick><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonMenu.ItemsLoading><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonSplitButton.Click><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonToggleButton.Click>|<xref:Microsoft.Office.Tools.Ribbon.RibbonControlEventHandler>|

## <a name="set-the-position-of-a-ribbon-component-programmatically"></a>Establecer la posición de un componente de la cinta mediante programación
 Debe modificar cualquier código que establezca la posición de los grupos, pestañas o controles de la cinta. En los proyectos que tengan como destino .NET Framework 3.5, puede usar los métodos `AfterOfficeId` y `BeforeOfficeId` de la clase estática `Microsoft.Office.Tools.Ribbon.RibbonPosition` para asignar la propiedad `Position` de un grupo, pestaña o control. En los proyectos que tengan como destino [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] o una versión posterior, debe acceder a estos métodos mediante la propiedad <xref:Microsoft.Office.Tools.Ribbon.RibbonFactory.RibbonPosition%2A> proporcionada por el objeto <xref:Microsoft.Office.Tools.Ribbon.RibbonFactory>.

 Hay dos maneras de acceder al objeto <xref:Microsoft.Office.Tools.Ribbon.RibbonFactory>:

- Mediante el uso de la propiedad `Factory` de la clase Ribbon. Use este enfoque desde el código en la clase Ribbon.

- Usando el método `Globals.Factory.GetRibbonFactory`. Use este enfoque desde el código externo a la clase Ribbon. Para obtener más información sobre la clase Globals, consulte [acceso global a objetos en proyectos de Office](../vsto/global-access-to-objects-in-office-projects.md).

  En el siguiente ejemplo de código se muestra cómo establecer la propiedad `Position` en una clase Ribbon en un proyecto que tenga como destino NET Framework 3.5.

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
- [Migrar soluciones de Office al .NET Framework 4 o posterior](../vsto/migrating-office-solutions-to-the-dotnet-framework-4-or-later.md)
- [Diseñador de la cinta de opciones](../vsto/ribbon-designer.md)
