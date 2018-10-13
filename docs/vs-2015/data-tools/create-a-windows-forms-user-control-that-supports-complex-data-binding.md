---
title: Crear un control de usuario de Windows Forms que admita el enlace de datos complejos | Documentos de Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- data binding, user controls
- data binding, complex
- user controls [Visual Studio], complex data binding
ms.assetid: c8f29c2b-b49b-4618-88aa-33b6105880b5
caps.latest.revision: 16
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: de22f93c6fd04f89360fdaf8a2f5d83bd373d93d
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49284263"
---
# <a name="create-a-windows-forms-user-control-that-supports-complex-data-binding"></a>Crear un control de usuario de Windows Forms que admita el enlace de datos complejos
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Cuando muestra datos en formularios de aplicaciones de Windows, puede elegir controles existentes en el **cuadro de herramientas**, o puede crear controles personalizados si la aplicación requiere funcionalidad que no está disponible en los controles estándar. En este tutorial se muestra cómo crear un control que implementa <xref:System.ComponentModel.ComplexBindingPropertiesAttribute>. Los controles que implementan <xref:System.ComponentModel.ComplexBindingPropertiesAttribute> contienen unas propiedades `DataSource` y `DataMember` que se pueden enlazar a datos. Tales controles son similares a <xref:System.Windows.Forms.DataGridView> o <xref:System.Windows.Forms.ListBox>.  
  
 Para obtener más información sobre la creación de controles, vea [desarrollar controles de Windows Forms en tiempo de diseño](http://msdn.microsoft.com/library/e5a8e088-7ec8-4fd9-bcb3-9078fd134829).  
  
 Al crear controles para su uso en escenarios de enlace de datos, necesita implementar uno de los siguientes atributos de enlace de datos:  
  
|Uso de atributos de enlace de datos|  
|-----------------------------------|  
|Implemente el <xref:System.ComponentModel.DefaultBindingPropertyAttribute> en controles sencillos, como un <xref:System.Windows.Forms.TextBox>, que muestra una única columna (o propiedad) de datos. Para obtener más información, consulte [crear un control de usuario de Windows Forms que admita el enlace de datos simple](../data-tools/create-a-windows-forms-user-control-that-supports-simple-data-binding.md).|  
|Implemente el <xref:System.ComponentModel.ComplexBindingPropertiesAttribute> en controles, como <xref:System.Windows.Forms.DataGridView>, que muestra listas (o tablas) de datos. (Este proceso se describe en esta página del tutorial.)|  
|Implemente el <xref:System.ComponentModel.LookupBindingPropertiesAttribute> en controles, como <xref:System.Windows.Forms.ComboBox>, que muestren listas (o tablas) de datos, pero que también necesiten presentar una única columna o propiedad. Para obtener más información, consulte [crear un control de usuario de Windows Forms que admita el enlace de datos de búsqueda](../data-tools/create-a-windows-forms-user-control-that-supports-lookup-data-binding.md).|  
  
 En este tutorial se crea un control complejo que muestra las filas de datos de una tabla. En este ejemplo se utiliza la tabla `Customers` de la base de datos de ejemplo Northwind. El control de usuario complejo mostrará la tabla de clientes en una <xref:System.Windows.Forms.DataGridView> del control personalizado.  
  
 Durante este tutorial aprenderá a:  
  
-   Cree un nuevo **aplicación Windows**.  
  
-   Agregue un nuevo **Control de usuario** al proyecto.  
  
-   Diseñe visualmente el control de usuario.  
  
-   Implemente el atributo `ComplexBindingProperty`.  
  
-   Crear un conjunto de datos con el [Asistente para configuración de origen de datos](http://msdn.microsoft.com/library/c4df7de5-5da0-4064-940c-761dd6d9e28f).  
  
-   Establecer el **clientes** de tabla en la [ventana Orígenes de datos](http://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992) para utilizar el nuevo control complejo.  
  
-   Agregue el nuevo control arrastrándolo desde la **ventana Orígenes de datos** en **Form1**.  
  
## <a name="prerequisites"></a>Requisitos previos  
 Para poder completar este tutorial, necesitará:  
  
-   Acceso a la base de datos de ejemplo Northwind. Para obtener más información, consulte [Cómo: instalar bases de datos de ejemplo](../data-tools/how-to-install-sample-databases.md).  
  
## <a name="create-a-windows-application"></a>Crear una aplicación de Windows  
 El primer paso es crear un **aplicación Windows**.  
  
#### <a name="to-create-the-new-windows-project"></a>Para crear el nuevo proyecto de Windows  
  
1.  En Visual Studio, desde el **archivo** menú, cree un nuevo **proyecto**.  
  
2.  Denomine el proyecto **Tutorialdecontrolcomplejo**.  
  
3.  Seleccione **aplicación Windows**y haga clic en **Aceptar**. Para obtener más información, consulte [las aplicaciones cliente](http://msdn.microsoft.com/library/2dfb50b7-5af2-4e12-9bbb-c5ade0e39a68).  
  
     El **Tutorialdecontrolcomplejo** se crea y agrega al proyecto **el Explorador de soluciones**.  
  
## <a name="add-a-user-control-to-the-project"></a>Agregue un control de usuario al proyecto  
 Dado que este tutorial crea un control complejo enlazable a datos desde un **Control de usuario**, debe agregar un **Control de usuario** al proyecto.  
  
#### <a name="to-add-a-user-control-to-the-project"></a>Para agregar un control de usuario al proyecto  
  
1.  Desde el **proyecto** menú, elija **agregar Control de usuario**.  
  
2.  Tipo **ComplexDataGridView** en el **nombre** área y, a continuación, haga clic en **agregar**.  
  
     El **ComplexDataGridView** se agrega al control **el Explorador de soluciones**y se abre en el diseñador.  
  
## <a name="design-the-complexdatagridview-control"></a>Diseñar el control ComplexDataGridView  
 En este paso se agrega un <xref:System.Windows.Forms.DataGridView> al control de usuario.  
  
#### <a name="to-design-the-complexdatagridview-control"></a>Para diseñar el control ComplexDataGridView  
  
-   Arrastre un <xref:System.Windows.Forms.DataGridView> desde el **cuadro de herramientas** hasta la superficie de diseño del control de usuario.  
  
## <a name="add-the-required-data-binding-attribute"></a>Agregue el atributo de enlace de datos requerido  
 En el caso de los controles complejos que admiten enlaces a datos, puede implementar el <xref:System.ComponentModel.ComplexBindingPropertiesAttribute>.  
  
#### <a name="to-implement-the-complexbindingproperties-attribute"></a>Para implementar el atributo ComplexBindingProperties  
  
1.  Cambiar el **ComplexDataGridView** control a la vista código. (En el **vista** menú, seleccione **código**.)  
  
2.  Reemplace el código de `ComplexDataGridView` por lo siguiente:  
  
     [!code-csharp[VbRaddataDisplaying#4](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataDisplaying/CS/ComplexDataGridView.cs#4)]
     [!code-vb[VbRaddataDisplaying#4](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataDisplaying/VB/ComplexDataGridView.vb#4)]  
  
3.  En el menú **Compilar** , elija **Compilar solución**.  
  
## <a name="creating-a-data-source-from-your-database"></a>Crear un origen de datos de la base de datos  
 Este paso se usa el **configuración origen de datos** Asistente para crear un origen de datos según la `Customers` tabla en la base de datos de ejemplo Northwind. Debe tener acceso a la base de datos de ejemplo Northwind para crear la conexión. Para obtener información acerca de cómo configurar la base de datos de ejemplo Northwind, vea [bases de datos de ejemplo de instalación de SQL Server](../data-tools/install-sql-server-sample-databases.md).  
  
#### <a name="to-create-the-data-source"></a>Para crear el origen de datos  
  
1.  En el menú **Datos** , haga clic en **Mostrar orígenes de datos**.  
  
2.  En el **orígenes de datos** ventana, seleccione **Agregar nuevo origen de datos** para iniciar el **configuración origen de datos** asistente.  
  
3.  Seleccione **Base de datos** en la página **Elegir un tipo de datos de origen** y luego haga clic en **Siguiente**.  
  
4.  En el **elegir la conexión de datos** realice página uno de los siguientes:  
  
    -   Si una conexión de datos a la base de datos de ejemplo Northwind está disponible en la lista desplegable, selecciónela.  
  
    -   Seleccione **nueva conexión** para iniciar el **agregar o modificar conexión** cuadro de diálogo.  
  
5.  Si la base de datos requiere una contraseña, seleccione la opción para incluir datos confidenciales y, a continuación, haga clic en **siguiente**.  
  
6.  En el **Guardar cadena de conexión en el archivo de configuración de la aplicación** página, haga clic en **siguiente**.  
  
7.  En el **elija los objetos de base de datos** , expanda el **tablas** nodo.  
  
8.  Seleccione el `Customers` de tabla y, a continuación, haga clic en **finalizar**.  
  
     El **NorthwindDataSet** se agrega al proyecto y el `Customers` tabla aparece en el **orígenes de datos** ventana.  
  
## <a name="set-the-customers-table-to-use-the-complexdatagridview-control"></a>Establecer la tabla Customers para utilizar el control ComplexDataGridView  
 Dentro de la **orígenes de datos** ventana, puede establecer el control que se creará antes de arrastrar elementos al formulario.  
  
#### <a name="to-set-the-customers-table-to-bind-to-the-complexdatagridview-control"></a>Para establecer la columna Customers para enlazarse al control ComplexDataGridView  
  
1.  Abra **Form1** en el diseñador.  
  
2.  Expanda el **clientes** nodo en el **orígenes de datos** ventana.  
  
3.  Haga clic en la flecha de lista desplegable el **clientes** nodo y elija **personalizar**.  
  
4.  Seleccione el **ComplexDataGridView** en la lista de **controles asociados** en el **opciones de personalización de la interfaz de usuario de datos** cuadro de diálogo.  
  
5.  Haga clic en la flecha de lista desplegable el `Customers` de tabla y elija **ComplexDataGridView** desde la lista de control.  
  
## <a name="addcontrols-to-the-form"></a>Addcontrols al formulario  
 Puede crear los controles enlazados a datos arrastrando elementos desde la **orígenes de datos** ventana hasta su formulario.  
  
#### <a name="to-create-data-bound-controls-on-the-form"></a>Para crear controles enlazados en el formulario  
  
-   Arrastre el método main **clientes** nodo desde el **orígenes de datos** ventana hasta el formulario. Compruebe que la **ComplexDataGridView** control se usa para mostrar los datos de la tabla.  
  
## <a name="running-the-application"></a>Ejecutar la aplicación  
  
#### <a name="to-run-the-application"></a>Para ejecutar la aplicación  
  
-   Presione F5 para ejecutar la aplicación.  
  
## <a name="next-steps"></a>Pasos siguientes  
 Según cuáles sean los requisitos de la aplicación, hay varios pasos que se pueden realizar después de crear un control que admite el enlace a datos. Entre los pasos más habituales están los siguientes:  
  
-   Colocar los controles personalizados en una biblioteca de controles para poder reutilizarlos en otras aplicaciones.  
  
-   Crear controles que admitan escenarios de búsqueda. Para obtener más información, consulte [crear un control de usuario de Windows Forms que admita el enlace de datos de búsqueda](../data-tools/create-a-windows-forms-user-control-that-supports-lookup-data-binding.md).  
  
## <a name="see-also"></a>Vea también  
 [Enlazar controles de Windows Forms a datos en Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [Establecer el control que se creará al arrastrar desde la ventana Orígenes de datos](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md)   
 [Controles de formularios Windows Forms](http://msdn.microsoft.com/library/f050de8f-4ebd-4042-94b8-edf9a1dbd52a)

