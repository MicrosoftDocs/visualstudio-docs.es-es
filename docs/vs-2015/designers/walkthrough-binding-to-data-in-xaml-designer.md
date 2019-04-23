---
title: 'Tutorial: Enlazar a datos en el Diseñador XAML | Documentos de Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-designers
ms.topic: conceptual
f1_keywords:
- VS.XamlDesigner.DataBinding
ms.assetid: 1a99aeae-c3ef-407d-ba79-b8055489a43d
caps.latest.revision: 22
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: a7a27b2744247bba78575b0387a958bda5990d8c
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/22/2019
ms.locfileid: "60071621"
---
# <a name="walkthrough-binding-to-data-in-xaml-designer"></a>Tutorial: Enlazar a datos en el Diseñador XAML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

En el diseñador XAML, puedes establecer las propiedades de enlace de datos con la mesa de trabajo y la ventana Propiedades. En el ejemplo de este tutorial se muestra cómo enlazar datos a un control. En concreto, el tutorial muestra cómo crear una clase simple de carro de la compra que tenga una propiedad [DependencyProperty](http://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.dependencyproperty.aspx) denominada `ItemCount` y luego enlazar la propiedad `ItemCount` a la propiedad **Text** de un control [TextBlock](http://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.textblock.aspx).  
  
### <a name="to-create-a-class-to-use-as-a-data-source"></a>Para crear una clase con el fin de usarla como origen de datos  
  
1. En el menú **Archivo** , elija **Nuevo**, **Proyecto**.  
  
2. En el cuadro de diálogo **Nuevo proyecto**, elija el nodo de **Visual C#** o **Visual Basic**, expanda el nodo **Escritorio de Windows** y después elija la plantilla **Aplicación WPF**.  
  
3. Asigne un nombre al proyecto **BindingTest** y después elija el botón **Aceptar**.  
  
4. Abra el archivo MainWindow.xaml.cs (o MainWindow.xaml.vb) y agregue el código siguiente. En C#, agrega el código en el espacio de nombres `BindingTest` (antes del paréntesis de cierre final del archivo). En Visual Basic, simplemente agrega la nueva clase.  
  
    ```csharp  
    public class ShoppingCart : DependencyObject  
    {  
        public int ItemCount  
        {  
            get { return (int)GetValue(ItemCountProperty); }  
            set { SetValue(ItemCountProperty, value); }  
        }  
  
        public static readonly DependencyProperty ItemCountProperty =  
             DependencyProperty.Register("ItemCount", typeof(int),  
             typeof(ShoppingCart), new PropertyMetadata(0));  
    }  
  
    ```  
  
    ```vb  
    Public Class ShoppingCart  
        Inherits DependencyObject  
  
        Public Shared ReadOnly ItemCountProperty As DependencyProperty = DependencyProperty.Register(  
            "ItemCount", GetType(Integer), GetType(ShoppingCart), New PropertyMetadata(0))  
        Public Property ItemCount As Integer  
            Get  
                ItemCount = CType(GetValue(ItemCountProperty), Integer)  
            End Get  
            Set(value As Integer)  
                SetValue(ItemCountProperty, value)  
            End Set  
        End Property  
    End Class  
    ```  
  
     Este código establece un valor de 0 como el número predeterminado de elementos mediante el objeto [PropertyMetadata](http://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.propertymetadata.aspx).  
  
5. En el menú **Archivo**, elija **Compilar**, **Compilar solución**.  
  
### <a name="to-bind-the-itemcount-property-to-a-textblock-control"></a>Para enlazar la propiedad ItemCount a un control TextBlock  
  
1. En el Explorador de soluciones, abra el menú contextual de MainWindow.xaml y elija **Diseñador de vistas**.  
  
2. En el cuadro de herramientas, elija un control [Grid](http://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.grid.aspx) y agréguelo al formulario.  
  
3. Con el control `Grid` seleccionado, en la ventana Propiedades, elija el botón **Nuevo** situado junto a la propiedad **DataContext**.  
  
4. En el cuadro de diálogo **Seleccionar objeto**, asegúrese de que la casilla **Mostrar todos los ensamblados** está desactivada, elija **ShoppingCart** en el espacio de nombres **BindingTest** y después elija el botón **Aceptar**.  
  
     En la siguiente ilustración, se muestra el cuadro de diálogo **Seleccionar objeto** con **ShoppingCart** seleccionado.  
  
     ![Cuadro de diálogo Seleccionar objeto](../designers/media/blendselectobject.PNG "BlendSelectObject")  
  
5. En el **cuadro de herramientas**, elija un control `TextBlock` para agregar al formulario.  
  
6. Con el control `TextBlock` seleccionado, en la ventana Propiedades, elija el marcador de propiedad situado a la derecha de la propiedad **Text** y después elija **Crear enlace de datos**. (El marcador de propiedad tiene el aspecto de un cuadro pequeño).  
  
7. En el cuadro de diálogo Crear enlace de datos, en el cuadro **Ruta de acceso**, seleccione la propiedad **ItemCount: (int32)** y después elija el botón **Aceptar**.  
  
     En la siguiente ilustración, se muestra el cuadro de diálogo **Crear enlace de datos** con la propiedad **ItemCount** seleccionada.  
  
     ![Cuadro de diálogo Crear enlace de datos](../designers/media/xaml-create-data-binding.png "xaml_create_data_binding")  
  
8. Presione F5 para ejecutar la aplicación.  
  
     El control `TextBlock` debe mostrar el valor predeterminado de 0 como texto.  
  
## <a name="see-also"></a>Vea también  
 [Crear una IU con el Diseñador XAML](../designers/creating-a-ui-by-using-xaml-designer-in-visual-studio.md)   
 [NIB: Agregar cuadro de diálogo de convertidor de valores](http://msdn.microsoft.com/c5f3d110-a541-4b55-8bca-928f77778af8)
