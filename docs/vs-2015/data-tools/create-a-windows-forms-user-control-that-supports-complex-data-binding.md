---
title: Crear un control de usuario de Windows Forms que admita el enlace de datos complejos | Documentos de Microsoft
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
- data binding, user controls
- data binding, complex
- user controls [Visual Studio], complex data binding
ms.assetid: c8f29c2b-b49b-4618-88aa-33b6105880b5
caps.latest.revision: 16
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 0c27ec5be48b37f95068a2be6c8605a97d122d21
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/15/2019
ms.locfileid: "65705000"
---
# <a name="create-a-windows-forms-user-control-that-supports-complex-data-binding"></a>Creación de un control de usuario de Windows Forms que admita el enlace de datos complejo
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Cuando muestra datos en formularios de las aplicaciones Windows, puede elegir controles existentes en el **Cuadro de herramientas** o crear controles personalizados si la aplicación requiere funcionalidad que no está disponible en los controles estándar. En este tutorial se muestra cómo crear un control que implementa <xref:System.ComponentModel.ComplexBindingPropertiesAttribute>. Los controles que implementan <xref:System.ComponentModel.ComplexBindingPropertiesAttribute> contienen unas propiedades `DataSource` y `DataMember` que se pueden enlazar a datos. Tales controles son similares a <xref:System.Windows.Forms.DataGridView> o <xref:System.Windows.Forms.ListBox>.  
  
 Para obtener más información sobre la creación de controles, vea [desarrollar controles de Windows Forms en tiempo de diseño](https://msdn.microsoft.com/library/e5a8e088-7ec8-4fd9-bcb3-9078fd134829).  
  
 Al crear controles para usarlos en escenarios de enlace de datos, es necesario implementar uno de los atributos de enlace de datos siguientes:  
  
|Uso de atributos de enlace de datos|  
|-----------------------------------|  
|Implemente el <xref:System.ComponentModel.DefaultBindingPropertyAttribute> en controles sencillos, como un <xref:System.Windows.Forms.TextBox>, que muestra una única columna (o propiedad) de datos. Para obtener más información, consulte [crear un control de usuario de Windows Forms que admita el enlace de datos simple](../data-tools/create-a-windows-forms-user-control-that-supports-simple-data-binding.md).|  
|Implemente el <xref:System.ComponentModel.ComplexBindingPropertiesAttribute> en controles, como <xref:System.Windows.Forms.DataGridView>, que muestra listas (o tablas) de datos. (Este proceso se describe en esta página del tutorial.)|  
|Implemente el <xref:System.ComponentModel.LookupBindingPropertiesAttribute> en controles, como <xref:System.Windows.Forms.ComboBox>, que muestren listas (o tablas) de datos, pero que también necesiten presentar una única columna o propiedad. Para obtener más información, consulte [crear un control de usuario de Windows Forms que admita el enlace de datos de búsqueda](../data-tools/create-a-windows-forms-user-control-that-supports-lookup-data-binding.md).|  
  
 En este tutorial se crea un control complejo que muestra las filas de datos de una tabla. En este ejemplo se utiliza la tabla `Customers` de la base de datos de ejemplo Northwind. El control de usuario complejo mostrará la tabla de clientes en una <xref:System.Windows.Forms.DataGridView> del control personalizado.  
  
 Durante este tutorial aprenderá a:  
  
- Cree un nuevo **aplicación Windows**.  
  
- Agregue un nuevo **Control de usuario** a su proyecto.  
  
- Diseñe visualmente el control de usuario.  
  
- Implemente el atributo `ComplexBindingProperty`.  
  
- Crear un conjunto de datos con el [Asistente para configuración de origen de datos](https://msdn.microsoft.com/library/c4df7de5-5da0-4064-940c-761dd6d9e28f).  
  
- Establecer el **clientes** de tabla en la [ventana Orígenes de datos](https://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992) para utilizar el nuevo control complejo.  
  
- Agregue el nuevo control arrastrándolo desde la **ventana Orígenes de datos** en **Form1**.  
  
## <a name="prerequisites"></a>Requisitos previos  
 Para poder completar este tutorial, necesitará:  
  
- Acceso a la base de datos de ejemplo Northwind.
  
## <a name="create-a-windows-application"></a>Crear una aplicación de Windows  
 El primer paso es crear un **aplicación Windows**.  
  
#### <a name="to-create-the-new-windows-project"></a>Para crear el nuevo proyecto de Windows  
  
1. En Visual Studio, desde el **archivo** menú, cree un nuevo **proyecto**.  
  
2. Asigne el nombre **TutorialDeControlComplejo al proyecto**.  
  
3. Seleccione **aplicación Windows**y haga clic en **Aceptar**. Para obtener más información, consulte [las aplicaciones cliente](https://msdn.microsoft.com/library/2dfb50b7-5af2-4e12-9bbb-c5ade0e39a68).  
  
     El proyecto **TutorialDeControlComplejo** se crea y se agrega al **Explorador de soluciones**.  
  
## <a name="add-a-user-control-to-the-project"></a>Agregar un control de usuario al proyecto  
 Dado que este tutorial crea un control complejo enlazable a datos desde un **Control de usuario**, debe agregar un **Control de usuario** al proyecto.  
  
#### <a name="to-add-a-user-control-to-the-project"></a>Para agregar un control de usuario al proyecto  
  
1. En el menú **Proyecto**, elija **Agregar control de usuario**.  
  
2. Escriba **ComplexDataGridView** en el área **Nombre** y haga clic en **Agregar**.  
  
     El control **ComplexDataGridView** se agrega al **Explorador de soluciones** y se abre en el diseñador.  
  
## <a name="design-the-complexdatagridview-control"></a>Diseñar el control ComplexDataGridView  
 En este paso se agrega un <xref:System.Windows.Forms.DataGridView> al control de usuario.  
  
#### <a name="to-design-the-complexdatagridview-control"></a>Para diseñar el control ComplexDataGridView  
  
- Arrastre un control <xref:System.Windows.Forms.DataGridView> del **Cuadro de herramientas** hasta la superficie de diseño del control del usuario.  
  
## <a name="add-the-required-data-binding-attribute"></a>Agregue el atributo de enlace de datos requerido  
 En el caso de los controles complejos que admiten enlaces a datos, puede implementar el <xref:System.ComponentModel.ComplexBindingPropertiesAttribute>.  
  
#### <a name="to-implement-the-complexbindingproperties-attribute"></a>Para implementar el atributo ComplexBindingProperties  
  
1. Cambie el control **ComplexDataGridView** a vista de código. En el menú **Ver**, seleccione **Código**.  
  
2. Reemplace el código de `ComplexDataGridView` por lo siguiente:  
  
     [!code-csharp[VbRaddataDisplaying#4](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataDisplaying/CS/ComplexDataGridView.cs#4)]
     [!code-vb[VbRaddataDisplaying#4](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataDisplaying/VB/ComplexDataGridView.vb#4)]  
  
3. En el menú **Compilar** , elija **Compilar solución**.  
  
## <a name="creating-a-data-source-from-your-database"></a>Crear un origen de datos de la base de datos  
 En este paso se usa el **Asistente para configuración de orígenes de datos** para crear un origen de datos basado en la tabla `Customers` de la base de datos de ejemplo Northwind. Debe tener acceso a la base de datos de ejemplo Northwind para crear la conexión. Para obtener información acerca de cómo configurar la base de datos de ejemplo Northwind, vea [bases de datos de ejemplo de instalación de SQL Server](../data-tools/install-sql-server-sample-databases.md).  
  
#### <a name="to-create-the-data-source"></a>Para crear el origen de datos  
  
1. En el menú **Datos** , haga clic en **Mostrar orígenes de datos**.  
  
2. En la ventana **Orígenes de datos**, seleccione **Agregar nuevo origen de datos** para iniciar el **Asistente para configuración de orígenes de datos**.  
  
3. Seleccione **Base de datos** en la página **Elegir un tipo de datos de origen** y luego haga clic en **Siguiente**.  
  
4. En la página **Elegir la conexión de datos** realice una de las siguientes operaciones:  
  
    - Si una conexión de datos a la base de datos de ejemplo Northwind está disponible en la lista desplegable, selecciónela.  
  
    - Seleccione **Nueva conexión** para iniciar el cuadro de diálogo **Agregar o modificar conexión**.  
  
5. Si su base de datos requiere una contraseña, seleccione la opción para incluir datos confidenciales y haga clic en **Siguiente**.  
  
6. Haga clic en **Siguiente** en la página **Guardar la cadena de conexión en el archivo de configuración de la aplicación**.  
  
7. Expanda el nodo **Tablas** en la página **Elija los objetos de base de datos**.  
  
8. Seleccione la tabla `Customers` y después haga clic en **Finalizar**.  
  
     **NorthwindDataSet** se agrega al proyecto y la tabla `Customers` aparece en la ventana **Orígenes de datos**.  
  
## <a name="set-the-customers-table-to-use-the-complexdatagridview-control"></a>Establecer la tabla Customers para utilizar el control ComplexDataGridView  
 Dentro de la ventana **Orígenes de datos** puede establecer el control que se va a crear antes de arrastrar elementos a un formulario.  
  
#### <a name="to-set-the-customers-table-to-bind-to-the-complexdatagridview-control"></a>Para establecer la columna Customers para enlazarse al control ComplexDataGridView  
  
1. Abra **Form1** en el diseñador.  
  
2. Expanda el nodo **Customers** en la ventana **Orígenes de datos**.  
  
3. Haga clic en la flecha de lista desplegable en la columna **Customers** y elija **Personalizar**.  
  
4. Seleccione **ComplexDataGridView** de la lista de **Controles asociados** en el cuadro de diálogo **Opciones de personalización de la interfaz de usuario de datos**.  
  
5. Haga clic en la flecha de lista desplegable en la tabla `Customers` y elija **ComplexDataGridView** de la lista de controles.  
  
## <a name="addcontrols-to-the-form"></a>Addcontrols al formulario  
 Puede crear los controles enlazados a datos arrastrando elementos desde la ventana **Orígenes de datos** al formulario.  
  
#### <a name="to-create-data-bound-controls-on-the-form"></a>Para crear controles enlazados en el formulario  
  
- Arrastre el método main **clientes** nodo desde el **orígenes de datos** ventana hasta el formulario. Compruebe que la **ComplexDataGridView** control se usa para mostrar los datos de la tabla.  
  
## <a name="running-the-application"></a>Ejecutar la aplicación  
  
#### <a name="to-run-the-application"></a>Para ejecutar la aplicación  
  
- Presione F5 para ejecutar la aplicación.  
  
## <a name="next-steps"></a>Pasos siguientes  
 Según cuáles sean los requisitos de la aplicación, hay varios pasos que se pueden realizar después de crear un control que admite el enlace a datos. Entre los pasos más habituales están los siguientes:  
  
- Colocar los controles personalizados en una biblioteca de controles para poder reutilizarlos en otras aplicaciones.  
  
- Crear controles que admitan escenarios de búsqueda. Para obtener más información, consulte [crear un control de usuario de Windows Forms que admita el enlace de datos de búsqueda](../data-tools/create-a-windows-forms-user-control-that-supports-lookup-data-binding.md).  
  
## <a name="see-also"></a>Vea también  
 [Enlazar controles de Windows Forms a datos en Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [Establecer el control que se creará al arrastrar desde la ventana Orígenes de datos](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md)   
 [Controles de formularios Windows Forms](https://msdn.microsoft.com/library/f050de8f-4ebd-4042-94b8-edf9a1dbd52a)
