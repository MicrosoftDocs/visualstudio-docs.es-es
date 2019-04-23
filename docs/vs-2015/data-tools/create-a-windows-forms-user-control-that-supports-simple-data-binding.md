---
title: Crear un control de usuario de Windows Forms que admita el enlace de datos simple | Documentos de Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- custom controls [Visual Studio], Data Sources Window
- Data Sources Window, controls
ms.assetid: b1488366-6dfb-454e-9751-f42fd3f3ddfb
caps.latest.revision: 17
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: dc14e8751e11c53bb43041228a6556604d0d9641
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/17/2019
ms.locfileid: "59664766"
---
# <a name="create-a-windows-forms-user-control-that-supports-simple-data-binding"></a>Crear un control de usuario de Windows Forms que admita el enlace de datos simple
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Cuando muestra datos en formularios de las aplicaciones Windows, puede elegir controles existentes en el **Cuadro de herramientas** o crear controles personalizados si la aplicación requiere funcionalidad que no está disponible en los controles estándar. En este tutorial se muestra cómo crear un control que implementa <xref:System.ComponentModel.DefaultBindingPropertyAttribute>. Los controles que implementan <xref:System.ComponentModel.DefaultBindingPropertyAttribute> pueden contener una propiedad que se puede enlazar a datos. Tales controles son similares a <xref:System.Windows.Forms.TextBox> o <xref:System.Windows.Forms.CheckBox>.  
  
 Para obtener más información sobre la creación de controles, vea [desarrollar controles de Windows Forms en tiempo de diseño](http://msdn.microsoft.com/library/e5a8e088-7ec8-4fd9-bcb3-9078fd134829).  
  
 Al crear controles para su uso en escenarios de enlace de datos, debe implementar uno de los atributos de enlace de datos siguientes:  
  
|Uso de atributos de enlace de datos|  
|-----------------------------------|  
|Implemente el <xref:System.ComponentModel.DefaultBindingPropertyAttribute> en controles sencillos, como un <xref:System.Windows.Forms.TextBox>, que muestra una única columna (o propiedad) de datos. (Este proceso se describe en esta página del tutorial.)|  
|Implemente el <xref:System.ComponentModel.ComplexBindingPropertiesAttribute> en controles, como <xref:System.Windows.Forms.DataGridView>, que muestra listas (o tablas) de datos. Para obtener más información, consulte [crear un control de usuario de Windows Forms que admita el enlace de datos complejos](../data-tools/create-a-windows-forms-user-control-that-supports-complex-data-binding.md).|  
|Implemente el <xref:System.ComponentModel.LookupBindingPropertiesAttribute> en controles, como <xref:System.Windows.Forms.ComboBox>, que muestren listas (o tablas) de datos, pero que también necesiten presentar una única columna o propiedad. Para obtener más información, consulte [crear un control de usuario de Windows Forms que admita el enlace de datos de búsqueda](../data-tools/create-a-windows-forms-user-control-that-supports-lookup-data-binding.md).|  
  
 En este tutorial se crea un control simple que muestra los datos de una sola columna en una tabla. En este ejemplo se usa la columna `Phone` de la tabla `Customers` de la base de datos de ejemplo Northwind. El control de usuario simple mostrará los números de teléfono de clientes en un formato de número de teléfono estándar, mediante el uso de un <xref:System.Windows.Forms.MaskedTextBox> y estableciendo la máscara en un número de teléfono.  
  
 Durante este tutorial aprenderá a:  
  
-   Cree un nuevo **aplicación Windows**.  
  
-   Agregue un nuevo **Control de usuario** a su proyecto.  
  
-   Diseñe visualmente el control de usuario.  
  
-   Implemente el atributo `DefaultBindingProperty`.  
  
-   Crear un conjunto de datos con el **configuración origen de datos** asistente.  
  
-   Establezca la columna **Phone** de la ventana **Orígenes de datos** de forma que se use el nuevo control.  
  
-   Cree un formulario para mostrar los datos en el nuevo control.  
  
## <a name="prerequisites"></a>Requisitos previos  
 Para poder completar este tutorial, necesitará:  
  
-   Acceso a la base de datos de ejemplo Northwind.
  
## <a name="create-a-windows-application"></a>Crear una aplicación de Windows  
 El primer paso es crear un **aplicación Windows**.  
  
#### <a name="to-create-the-new-windows-project"></a>Para crear el nuevo proyecto de Windows  
  
1.  En Visual Studio, desde el **archivo** menú, cree un nuevo **proyecto**.  
  
2.  Denomine el proyecto **Tutorialdecontrolsimple**.  
  
3.  Seleccione **aplicación Windows** y haga clic en **Aceptar**. Para obtener más información, consulte [las aplicaciones cliente](http://msdn.microsoft.com/library/2dfb50b7-5af2-4e12-9bbb-c5ade0e39a68).  
  
     El proyecto **TutorialDeControlSimple** se crea y se agrega al **Explorador de soluciones**.  
  
## <a name="add-a-user-control-to-the-project"></a>Agregar un control de usuario al proyecto  
 Este tutorial crea un control simple enlazable a datos desde un **Control de usuario**, por tanto, agregue un **Control de usuario** elemento a la **Tutorialdecontrolsimple** proyecto.  
  
#### <a name="to-add-a-user-control-to-the-project"></a>Para agregar un control de usuario al proyecto  
  
1.  En el menú **Proyecto**, elija **Agregar control de usuario**.  
  
2.  Tipo `PhoneNumberBox` en el área nombre y haga clic en **agregar**.  
  
     El control **PhoneNumberBox** se agrega al **Explorador de soluciones** y se abre en el diseñador.  
  
## <a name="design-the-phonenumberbox-control"></a>Diseñar el control PhoneNumberBox  
 Este tutorial se basa en el <xref:System.Windows.Forms.MaskedTextBox> existente y lo amplía para crear el control `PhoneNumberBox`.  
  
#### <a name="to-design-the-phonenumberbox-control"></a>Para diseñar el control PhoneNumberBox  
  
1.  Arrastre un control <xref:System.Windows.Forms.MaskedTextBox> del **Cuadro de herramientas** hasta la superficie de diseño del control del usuario.  
  
2.  Seleccione la etiqueta inteligente en el <xref:System.Windows.Forms.MaskedTextBox> que acaba de arrastrar y elija **Establecer máscara**.  
  
3.  Seleccione **Número de teléfono** en el cuadro de diálogo **Máscara de entrada** y haga clic en **Aceptar** para establecer la máscara.  
  
## <a name="add-the-required-data-binding-attribute"></a>Agregue el atributo de enlace de datos requerido  
 En el caso de los controles simples que admiten enlaces de datos, implemente el <xref:System.ComponentModel.DefaultBindingPropertyAttribute>.  
  
#### <a name="to-implement-the-defaultbindingproperty-attribute"></a>Para implementar el atributo DefaultBindingProperty  
  
1.  Cambie el control `PhoneNumberBox` a la vista de código. (En el menú **Ver**, elija **Código**.)  
  
2.  Reemplace el código de `PhoneNumberBox` por lo siguiente:  
  
     [!code-csharp[VbRaddataDisplaying#3](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataDisplaying/CS/PhoneNumberBox.cs#3)]
     [!code-vb[VbRaddataDisplaying#3](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataDisplaying/VB/PhoneNumberBox.vb#3)]  
  
3.  En el menú **Compilar** , elija **Compilar solución**.  
  
## <a name="create-a-data-source-from-your-database"></a>Crear un origen de datos de la base de datos  
 En este paso se usa el **Asistente para configuración de orígenes de datos** para crear un origen de datos basado en la tabla `Customers` de la base de datos de ejemplo Northwind. Debe tener acceso a la base de datos de ejemplo Northwind para crear la conexión.
  
#### <a name="to-create-the-data-source"></a>Para crear el origen de datos  
  
1.  En el menú **Datos** , haga clic en **Mostrar orígenes de datos**.  
  
2.  En la ventana **Orígenes de datos**, seleccione **Agregar nuevo origen de datos** para iniciar el **Asistente para configuración de orígenes de datos**.  
  
3.  En la página **Elegir un tipo de origen de datos**, seleccione **Base de datos** y después haga clic en **Siguiente**.  
  
4.  En la página **Elegir la conexión de datos** realice una de las siguientes operaciones:  
  
    -   Si una conexión de datos a la base de datos de ejemplo Northwind está disponible en la lista desplegable, selecciónela.  
  
    -   Seleccione **Nueva conexión** para iniciar el cuadro de diálogo **Agregar o modificar conexión**.  
  
5.  Si su base de datos requiere una contraseña, seleccione la opción para incluir datos confidenciales y haga clic en **Siguiente**.  
  
6.  Haga clic en **Siguiente** en la página **Guardar la cadena de conexión en el archivo de configuración de la aplicación**.  
  
7.  Expanda el nodo **Tablas** en la página **Elija los objetos de base de datos**.  
  
8.  Seleccione la tabla `Customers` y después haga clic en **Finalizar**.  
  
     **NorthwindDataSet** se agrega al proyecto y la tabla `Customers` aparece en la ventana **Orígenes de datos**.  
  
## <a name="set-the-phone-column-to-use-the-phonenumberbox-control"></a>Establecer la columna phone para utilizar el control PhoneNumberBox  
 Dentro de la ventana **Orígenes de datos** puede establecer el control que se va a crear antes de arrastrar elementos a un formulario.  
  
#### <a name="to-set-the-phone-column-to-bind-to-the-phonenumberbox-control"></a>Para establecer la columna Phone para enlazarse al control PhoneNumberBox  
  
1.  Abra **Form1** en el diseñador.  
  
2.  Expanda el nodo **Customers** en la ventana **Orígenes de datos**.  
  
3.  Haga clic en la flecha de lista desplegable en el nodo **Customers** y elija **Detalles** de la lista de control.  
  
4.  Haga clic en la flecha de lista desplegable en la columna **Phone** y elija **Personalizar**.  
  
5.  Seleccione **PhoneNumberBox** de la lista de **Controles asociados** en el cuadro de diálogo **Opciones de personalización de la interfaz de usuario de datos**.  
  
6.  Haga clic en la flecha de lista desplegable en la columna **Phone** y elija **PhoneNumberBox**.  
  
## <a name="addcontrols-to-the-form"></a>Addcontrols al formulario  
 Puede crear los controles enlazados a datos arrastrando elementos desde la ventana **Orígenes de datos** al formulario.  
  
#### <a name="to-create-data-bound-controls-on-the-form"></a>Para crear controles enlazados en el formulario  
  
-   Arrastre los principales **clientes** nodo desde el **orígenes de datos** ventana hasta el formulario y compruebe que la `PhoneNumberBox` control se usa para mostrar los datos en el `Phone` columna.  
  
     Los controles enlazados a datos con etiquetas descriptivas aparecen en el formulario, junto con una barra de herramientas (<xref:System.Windows.Forms.BindingNavigator>) para navegar por los registros. En la bandeja de componentes aparecen [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md), CustomersTableAdapter, <xref:System.Windows.Forms.BindingSource> y <xref:System.Windows.Forms.BindingNavigator>.  
  
## <a name="run-the-application"></a>Ejecutar la aplicación  
  
#### <a name="to-run-the-application"></a>Para ejecutar la aplicación  
  
-   Presione F5 para ejecutar la aplicación.  
  
## <a name="next-steps"></a>Pasos siguientes  
 Según cuáles sean los requisitos de la aplicación, hay varios pasos que se pueden realizar después de crear un control que admite el enlace a datos. Entre los pasos más habituales están los siguientes:  
  
-   Colocar los controles personalizados en una biblioteca de controles para poder reutilizarlos en otras aplicaciones.  
  
-   Crear controles que admitan escenarios de enlace a datos más complejos. Para obtener más información, consulte [crear un control de usuario de Windows Forms que admita el enlace de datos complejos](../data-tools/create-a-windows-forms-user-control-that-supports-complex-data-binding.md) y [crear un control de usuario de Windows Forms que admita el enlace de datos de búsqueda](../data-tools/create-a-windows-forms-user-control-that-supports-lookup-data-binding.md).  
  
## <a name="see-also"></a>Vea también  
 [Enlazar controles de Windows Forms a datos en Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [Establecer el control que se creará al arrastrar desde la ventana Orígenes de datos](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md)
