---
title: "Código fuente de L2DBForm.xaml | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-designers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 624e96d4-6d27-4195-8ac2-2f3835f6c57e
caps.latest.revision: "2"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: c3ccc6fcfa8471d767356f1e30d1e5f8b0ed15d0
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="l2dbformxaml-source-code"></a>Código fuente de L2DBForm.xaml
Este tema contiene y describe el archivo de origen XAML para el [WPF Data Binding Using LINQ to XML Example](../designers/wpf-data-binding-using-linq-to-xml-example.md), L2DBForm.xaml.  
  
## <a name="overall-ui-structure"></a>Estructura de IU general  
 Tal y como es típico para un proyecto de WPF, este archivo contiene un elemento primario, un elemento XML <xref:System.Windows.Window> XML asociada con la clase derivada `L2XDBFrom` del espacio de nombres `LinqToXmlDataBinding` .  
  
 El área del cliente está contenida en <xref:System.Windows.Controls.StackPanel> , que recibe un fondo de color azul claro. Este panel contiene cuatro secciones de IU <xref:System.Windows.Controls.DockPanel> separadas por barras <xref:System.Windows.Controls.Separator> . La finalidad de esas secciones se describe en las **Notas** del [tema anterior](../designers/walkthrough-linqtoxmldatabinding-example.md).  
  
 Cada sección contiene una etiqueta que la identifica. En las primeras dos secciones, esta etiqueta se gira 90 grados mediante <xref:System.Windows.FrameworkElement.LayoutTransform%2A>. El resto de la sección contiene elementos de IU apropiados para la finalidad de esa sección: bloques de texto, cuadros de texto, botones, etc. A veces se utiliza un <xref:System.Windows.Controls.StackPanel> secundario para alinear esos controles secundarios.  
  
## <a name="window-resource-section"></a>Sección de recursos de la ventana  
 La etiqueta de apertura `<Window.Resources>` de la línea 9 indica el inicio de la sección de recursos de la ventana. Acaba con la etiqueta de cierre de la línea 35.  
  
 La etiqueta `<ObjectDataProvider>` que se extiende por las líneas 11 a 25, declara un <xref:System.Windows.Data.ObjectDataProvider>, con el nombre `LoadedBooks`, que utiliza <xref:System.Xml.Linq.XElement> como el origen. Este <xref:System.Xml.Linq.XElement> se inicializa analizando un documento XML incrustado (un elemento `CDATA` ). Tenga en cuenta que el espacio en blanco se conserva cuando se declara el documento XML incrustado y también cuando se analiza. Esto se ha hecho porque el control <xref:System.Windows.Controls.TextBlock> , que se utiliza para visualizar XML sin formato, no tiene capacidades de formato XML especiales.  
  
 Por último, u <xref:System.Windows.DataTemplate> con el nombre `BookTemplate` se define en las líneas 28 a 34. Esta plantilla se utilizará para mostrar las entradas de la sección **Lista de libros** . Utiliza el enlace de datos y las propiedades dinámicas de LINQ to XML para recuperar el Id. y el nombre de libro a través de las siguientes asignaciones:  
  
```  
Text="{Binding Path=Attribute[id].Value}"Text="{Binding Path=Value}"  
```  
  
## <a name="data-binding-code"></a>Código de enlace de datos.  
 Además del elemento <xref:System.Windows.DataTemplate> , se utiliza el enlace datos en otros sitios de este archivo.  
  
 En la etiqueta de apertura `<StackPanel>` de la línea 38, la propiedad <xref:System.Windows.FrameworkElement.DataContext%2A> de este panel se establece en el proveedor de datos `LoadedBooks` .  
  
```  
DataContext="{Binding Source={StaticResource LoadedBooks}}  
```  
  
 Esto posibilita (en la línea 46) que el <xref:System.Windows.Controls.TextBlock> con el nombre `tbRawXml` muestre el XML sin formato enlazando con la propiedad `Xml` de este proveedor de datos:  
  
```  
Text="{Binding Path=Xml}"   
```  
  
 <xref:System.Windows.Controls.ListBox> en la sección de IU **Lista de libros** , en las líneas 58 a 62, establece la plantilla para sus elementos de visualización en la `BookTemplate` definida en la sección de recursos de la ventana:  
  
```  
ItemTemplate ="{StaticResource BookTemplate}"   
```  
  
 A continuación, en las líneas 59 a 62, los valores reales de los libros se enlazan con este cuadro de lista:  
  
```  
<ListBox.ItemsSource>  
    <Binding Path="Elements[{http://www.mybooks.com}book]"/>  
</ListBox.ItemsSource>  
```  
  
 La tercera sección de IU, **Editar el libro seleccionado**, primero enlaza el <xref:System.Windows.FrameworkElement.DataContext%2A> del <xref:System.Windows.Controls.StackPanel> primario con el elemento seleccionado actualmente de la sección de IU **Lista de libros** (línea 82):  
  
```  
DataContext="{Binding ElementName=lbBooks, Path=SelectedItem}"  
```  
  
 A continuación usa el enlace de datos bidireccional, de forma que los valores actuales de los elementos del libro se muestran y se actualizan desde los dos cuadros de texto de este panel. El enlace de datos con propiedades dinámicas es similar al utilizado en la plantilla de datos `BookTemplate` :  
  
```  
Text="{Binding Path=Attribute[id].Value}"...Text="{Binding Path=Value}"  
```  
  
 La última sección de la IU, **Agregar nuevo libro**, no utiliza el enlace de datos en su código XAML; en su lugar, ese código se puede encontrar en su código de control de errores del archivo L2DBForm.xaml.cs.  
  
## <a name="example"></a>Ejemplo  
  
### <a name="description"></a>Descripción  
  
> [!NOTE]
>  Se recomienda copiar el código siguiente en un editor de código, como el editor de código fuente de C# de Visual Studio, de forma que sea más sencillo realizar un seguimiento de los números de línea.  
  
### <a name="code"></a>Código  
  
```xml  
<Window x:Class="LinqToXmlDataBinding.L2XDBForm"  
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"  
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"  
    xmlns:system="clr-namespace:System;assembly=mscorlib"  
    xmlns:xlinq="clr-namespace:System.Xml.Linq;assembly=System.Xml.Linq"  
    xmlns:local="clr-namespace:LinqToXmlDataBinding"  
    Title="WPF Data Binding using LINQ-to-XML" Height="665" Width="500" ResizeMode="NoResize">  
  
    <Window.Resources>  
        <!-- Books provider and inline data -->  
        <ObjectDataProvider x:Key="LoadedBooks" ObjectType="{x:Type xlinq:XElement}" MethodName="Parse">  
            <ObjectDataProvider.MethodParameters>  
                <system:String xml:space="preserve">  
<![CDATA[  
<books xmlns="http://www.mybooks.com">  
  <book id="0">book zero</book>  
  <book id="1">book one</book>  
  <book id="2">book two</book>  
  <book id="3">book three</book>  
</books>  
]]>                  
                </system:String>  
                <xlinq:LoadOptions>PreserveWhitespace</xlinq:LoadOptions>  
            </ObjectDataProvider.MethodParameters>  
        </ObjectDataProvider>  
  
        <!-- Template for use in Books List listbox. -->  
        <DataTemplate x:Key="BookTemplate">  
            <StackPanel Orientation="Horizontal">  
                <TextBlock Margin="3" Text="{Binding Path=Attribute[id].Value}"/>  
                <TextBlock Margin="3" Text="-"/>  
                <TextBlock Margin="3" Text="{Binding Path=Value}"/>  
            </StackPanel>  
        </DataTemplate>  
    </Window.Resources>  
  
    <!-- Main visual content container -->  
    <StackPanel Background="lightblue" DataContext="{Binding Source={StaticResource LoadedBooks}}">  
        <!-- Raw XML display section -->  
        <DockPanel Margin="5">  
            <Label  Background="Gray" FontSize="12" BorderBrush="Black" BorderThickness="1" FontWeight="Bold">XML  
            <Label.LayoutTransform>  
                <RotateTransform Angle="90"/>  
            </Label.LayoutTransform>  
            </Label>  
            <TextBlock Name="tbRawXml" Height="200" Background="LightGray" Text="{Binding Path=Xml}" TextTrimming="CharacterEllipsis" />  
        </DockPanel>  
  
        <Separator Height="4" Margin="5" />  
  
        <!-- List box to display all books section -->  
        <DockPanel Margin="5">  
            <Label  Background="Gray" FontSize="12" BorderBrush="Black" BorderThickness="1" FontWeight="Bold">Book List  
                <Label.LayoutTransform>  
                    <RotateTransform Angle="90"/>  
                </Label.LayoutTransform>  
            </Label>  
            <ListBox Name="lbBooks" Height="200" Width="415" ItemTemplate ="{StaticResource BookTemplate}">  
                <ListBox.ItemsSource>  
                    <Binding Path="Elements[{http://www.mybooks.com}book]"/>  
                </ListBox.ItemsSource>  
            </ListBox>  
            <Button Margin="5" DockPanel.Dock="Right" Height="30" Width ="130" Content="Remove Selected Book" Click="OnRemoveBook">      
            <Button.LayoutTransform>  
                <RotateTransform Angle="90"/>  
            </Button.LayoutTransform>  
            </Button>  
        </DockPanel>  
  
        <Separator Height="4" Margin="5" />  
  
        <!-- Edit current selection section -->  
        <DockPanel Margin="5">  
            <TextBlock Margin="5" Height="30" Width="65" DockPanel.Dock="Right" Background="LightGray" TextWrapping="Wrap" TextAlignment="Center">  
                    Changes are live!  
                <TextBlock.LayoutTransform>  
                    <RotateTransform Angle="90"/>  
                </TextBlock.LayoutTransform>  
            </TextBlock>  
            <StackPanel>  
                <Label Width="450" Background="Gray" FontSize="12" BorderBrush="Black" BorderThickness="1" HorizontalAlignment="Left" FontWeight="Bold">Edit Selected Book</Label>      
                <StackPanel Margin="1" DataContext="{Binding ElementName=lbBooks, Path=SelectedItem}">  
                    <StackPanel Orientation="Horizontal">  
                        <Label Width="40">ID:</Label>  
                        <TextBox Name="editAttributeTextBox" Width="410" Text="{Binding Path=Attribute[id].Value}">  
                            <TextBox.ToolTip>  
                                <TextBlock FontWeight="Bold" TextAlignment="Center">  
                                    <Label>Edit the selected book ID and see it changed.</Label>  
                                </TextBlock>  
                            </TextBox.ToolTip>  
                        </TextBox>  
                    </StackPanel>  
                    <StackPanel Orientation="Horizontal">  
                        <Label Width="40">Value:</Label>  
                        <TextBox Name="editValueTextBox" Width="410" Text="{Binding Path=Value}" Height="25">  
                            <TextBox.ToolTip>  
                                <TextBlock FontWeight="Bold" TextAlignment="Center">  
                                    <Label>Edit the selected book Value and see it changed.</Label>  
                                </TextBlock>  
                            </TextBox.ToolTip>  
                        </TextBox>  
                    </StackPanel>  
                </StackPanel>  
            </StackPanel>  
        </DockPanel>  
  
        <Separator Height="4" Margin="5" />  
  
        <!-- Add new book section -->  
        <DockPanel Margin="5">  
            <Button Margin="5" Height="30" DockPanel.Dock="Right" Click ="OnAddBook">Add Book  
                <Button.LayoutTransform>  
                    <RotateTransform Angle="90"/>  
                </Button.LayoutTransform>  
            </Button>  
            <StackPanel>  
                <Label Width="450" Background="Gray" FontSize="12" BorderBrush="Black" BorderThickness="1" HorizontalAlignment="Left" FontWeight="Bold">Add New Book</Label>  
                <StackPanel Margin="1">  
                    <StackPanel Orientation="Horizontal">  
                        <Label Width="40">ID:</Label>  
                        <TextBox Name="tbAddID" Width="410">  
                            <TextBox.ToolTip>  
                                <TextBlock FontWeight="Bold" TextAlignment="Center">  
                                    <Label>Enter a book ID and Value pair, then click Add Book.</Label>  
                                </TextBlock>  
                            </TextBox.ToolTip>  
                        </TextBox>  
                    </StackPanel>  
                    <StackPanel Orientation="Horizontal">  
                        <Label Width="40">Value:</Label>  
                        <TextBox Name="tbAddValue" Width="410" Height="25">  
                            <TextBox.ToolTip>  
                                <TextBlock FontWeight="UltraBold" TextAlignment="Center">  
                                    <Label>Enter a book ID and Value pair, then click Add Book.</Label>  
                                </TextBlock>  
                            </TextBox.ToolTip>  
                        </TextBox>  
                    </StackPanel>  
                </StackPanel>  
            </StackPanel>  
        </DockPanel>  
    </StackPanel>  
</Window>  
  
```  
  
### <a name="comments"></a>Comentarios  
 Para conocer el código fuente de C# de los controladores de eventos asociados con los elementos de IU de WPF, consulte [L2DBForm.xaml.cs Source Code](../designers/l2dbform-xaml-cs-source-code.md).  
  
## <a name="see-also"></a>Vea también  
 [Tutorial: LinqToXmlDataBinding Example](../designers/walkthrough-linqtoxmldatabinding-example.md)   
 [Código fuente de L2DBForm.xaml.cs](../designers/l2dbform-xaml-cs-source-code.md)