---
title: Crear un control de usuario de formularios Windows Forms con enlace de datos | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data binding, user controls
- data binding, complex
- user controls [Visual Studio], complex data binding
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.workload: data-storage
ms.openlocfilehash: c5e59b34a1093b90320bfdd05989913e72600a8b
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="create-a-windows-forms-user-control-that-supports-complex-data-binding"></a>Crear un control de usuario de formularios Windows Forms que admita el enlace de datos complejo

Para mostrar datos en formularios de aplicaciones de Windows, puede elegir controles existentes en el **cuadro de herramientas**, o puede crear controles personalizados si la aplicación requiere funcionalidad que no está disponible en los controles estándar. En este tutorial se muestra cómo crear un control que implementa <xref:System.ComponentModel.ComplexBindingPropertiesAttribute>. Los controles que implementan <xref:System.ComponentModel.ComplexBindingPropertiesAttribute> contienen unas propiedades `DataSource` y `DataMember` que se pueden enlazar a datos. Tales controles son similares a <xref:System.Windows.Forms.DataGridView> o <xref:System.Windows.Forms.ListBox>.

Para obtener más información sobre la creación de control, vea [desarrollar controles de Windows Forms en tiempo de diseño](/dotnet/framework/winforms/controls/developing-windows-forms-controls-at-design-time).

Al crear controles para su uso en escenarios de enlace de datos, necesita implementar uno de los siguientes atributos de enlace de datos:

|Uso de atributos de enlace de datos|
|-----------------------------------|
|Implemente el <xref:System.ComponentModel.DefaultBindingPropertyAttribute> en controles sencillos, como un <xref:System.Windows.Forms.TextBox>, que muestra una única columna (o propiedad) de datos. Para obtener más información, consulte [crear un control de usuario de formularios Windows Forms que admita el enlace de datos simple](../data-tools/create-a-windows-forms-user-control-that-supports-simple-data-binding.md).|
|Implemente el <xref:System.ComponentModel.ComplexBindingPropertiesAttribute> en controles, como <xref:System.Windows.Forms.DataGridView>, que muestra listas (o tablas) de datos. (Este proceso se describe en esta página del tutorial.)|
|Implemente el <xref:System.ComponentModel.LookupBindingPropertiesAttribute> en controles, como <xref:System.Windows.Forms.ComboBox>, que muestren listas (o tablas) de datos, pero que también necesiten presentar una única columna o propiedad. Para obtener más información, consulte [crear un control de usuario de formularios Windows Forms que admita el enlace de datos de búsqueda](../data-tools/create-a-windows-forms-user-control-that-supports-lookup-data-binding.md).|

 En este tutorial se crea un control complejo que muestra las filas de datos de una tabla. En este ejemplo se utiliza la tabla `Customers` de la base de datos de ejemplo Northwind. El control de usuario complejo mostrará la tabla de clientes en una <xref:System.Windows.Forms.DataGridView> del control personalizado.

Durante este tutorial aprenderá a:

- Crear un nuevo **aplicación de Windows Forms**.

- Agregue un nuevo **Control de usuario** al proyecto.

- Diseñe visualmente el control de usuario.

- Implemente el atributo `ComplexBindingProperty`.

- Crear un conjunto de datos con la [Asistente para configuración de orígenes de datos](../data-tools/media/data-source-configuration-wizard.png).

- Establecer el **clientes** tabla el [ventana Orígenes de datos](add-new-data-sources.md) para utilizar el nuevo control complejo.

- Agregue el nuevo control arrastrándolo desde la **ventana Orígenes de datos** en **Form1**.

## <a name="prerequisites"></a>Requisitos previos

Este tutorial usa SQL Server Express LocalDB y la base de datos de ejemplo Northwind.

1. Si no tiene SQL Server Express LocalDB, puede instalarlo desde el [página de descarga de ediciones de SQL Server](https://www.microsoft.com/en-us/server-cloud/Products/sql-server-editions/sql-server-express.aspx), o a través del **instalador de Visual Studio**. El instalador de Visual Studio, se puede instalar SQL Server Express LocalDB como parte de la **almacenamiento de datos y el procesamiento** carga de trabajo, o como un componente individual.

1. Instalar la base de datos de ejemplo Northwind, siga estos pasos:

    1. En Visual Studio, abra el **Explorador de objetos de SQL Server** ventana. (Explorador de objetos de SQL Server se instala como parte de la **almacenamiento de datos y el procesamiento** carga de trabajo en el instalador de Visual Studio.) Expanda el **SQL Server** nodo. Haga doble clic en la instancia de LocalDB y seleccione **nueva consulta...** .

       Se abre una ventana del editor de consultas.

    2. Copia la [script Transact-SQL de Northwind](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true) en el Portapapeles. Este script de T-SQL crea la base de datos Northwind desde el principio y lo rellena con datos.

    3. Pegue el script de T-SQL en el editor de consultas y, a continuación, elija la **Execute** botón.

       Después de unos minutos, finaliza la ejecución de la consulta y se crea la base de datos Northwind.

## <a name="create-a-windows-forms-application"></a>Crear una aplicación de formularios Windows Forms

 El primer paso es crear un **aplicación de Windows Forms**.

### <a name="to-create-the-new-windows-project"></a>Para crear el nuevo proyecto de Windows

1. En Visual Studio, en el **archivo** menú, seleccione **New**, **proyecto...** .

1. Expanda **Visual C#** o **Visual Basic** en el panel izquierdo, seleccione **escritorio clásico de Windows**.

1. En el panel central, seleccione la **aplicación de Windows Forms** tipo de proyecto.

1. Denomine el proyecto **Tutorialdecontrolcomplejo**y, a continuación, elija **Aceptar**.

    El **Tutorialdecontrolcomplejo** proyecto se crea y se agrega a **el Explorador de soluciones**.

## <a name="add-a-user-control-to-the-project"></a>Agregue un control de usuario al proyecto

Dado que este tutorial crea un control complejo enlazable a datos de un **Control de usuario**, debe agregar una **Control de usuario** elemento al proyecto.

### <a name="to-add-a-user-control-to-the-project"></a>Para agregar un control de usuario al proyecto

1. Desde el **proyecto** menú, elija **agregar Control de usuario**.

1. Tipo de **ComplexDataGridView** en el **nombre** área y, a continuación, haga clic en **agregar**.

    El **ComplexDataGridView** se agrega al control **el Explorador de soluciones**y se abre en el diseñador.

## <a name="design-the-complexdatagridview-control"></a>Diseñar el control ComplexDataGridView

En este paso se agrega un <xref:System.Windows.Forms.DataGridView> al control de usuario.

### <a name="to-design-the-complexdatagridview-control"></a>Para diseñar el control ComplexDataGridView

- Arrastre un <xref:System.Windows.Forms.DataGridView> desde el **cuadro de herramientas** en la superficie de diseño del control de usuario.

## <a name="add-the-required-data-binding-attribute"></a>Agregue el atributo de enlace de datos requerido

En el caso de los controles complejos que admiten enlaces a datos, puede implementar el <xref:System.ComponentModel.ComplexBindingPropertiesAttribute>.
  
### <a name="to-implement-the-complexbindingproperties-attribute"></a>Para implementar el atributo ComplexBindingProperties

1. Cambiar el **ComplexDataGridView** control a la vista código. (En el **vista** menú, seleccione **código**.)

1. Reemplace el código de `ComplexDataGridView` por lo siguiente:

    [!code-csharp[VbRaddataDisplaying#4](../data-tools/codesnippet/CSharp/create-a-windows-forms-user-control-that-supports-complex-data-binding_1.cs)]
    [!code-vb[VbRaddataDisplaying#4](../data-tools/codesnippet/VisualBasic/create-a-windows-forms-user-control-that-supports-complex-data-binding_1.vb)]

1. En el menú **Compilar** , elija **Compilar solución**.

## <a name="creating-a-data-source-from-your-database"></a>Crear un origen de datos de la base de datos

Este paso se utiliza el **configuración del origen de datos** Asistente para crear un origen de datos en función de la `Customers` tabla en la base de datos de ejemplo Northwind.

### <a name="to-create-the-data-source"></a>Para crear el origen de datos

1.  En el menú **Datos** , haga clic en **Mostrar orígenes de datos**.

2.  En el **orígenes de datos** ventana, seleccione **Agregar nuevo origen de datos** para iniciar el **configuración del origen de datos** asistente.

3.  Seleccione **Base de datos** en la página **Elegir un tipo de datos de origen** y luego haga clic en **Siguiente**.

4.  En el **elegir la conexión de datos** realice de página una de las siguientes acciones:

    - Si una conexión de datos a la base de datos de ejemplo Northwind está disponible en la lista desplegable, selecciónela.

    - Seleccione **nueva conexión** para iniciar el **agregar o modificar conexión** cuadro de diálogo.

5.  Si la base de datos requiere una contraseña, seleccione la opción para incluir datos confidenciales y, a continuación, haga clic en **siguiente**.

6.  En el **Guardar cadena de conexión en el archivo de configuración de la aplicación** página, haga clic en **siguiente**.

7.  En el **elija los objetos de base de datos** página, expanda la **tablas** nodo.

8.  Seleccione el `Customers` de tabla y, a continuación, haga clic en **finalizar**.

    El **NorthwindDataSet** se agrega al proyecto y el `Customers` tabla aparece en la **orígenes de datos** ventana.

## <a name="set-the-customers-table-to-use-the-complexdatagridview-control"></a>Establecer la tabla Customers para utilizar el control ComplexDataGridView

En el **orígenes de datos** ventana, puede establecer el control que se creará antes de arrastrar elementos a un formulario.

### <a name="to-set-the-customers-table-to-bind-to-the-complexdatagridview-control"></a>Para establecer la columna Customers para enlazarse al control ComplexDataGridView

1. Abra **Form1** en el diseñador.

1. Expanda el **clientes** nodo en el **orígenes de datos** ventana.

1. Haga clic en la flecha de lista desplegable en el **clientes** nodo y elija **personalizar**.

1. Seleccione el **ComplexDataGridView** en la lista de **controles asociados** en el **opciones de personalización de interfaz de usuario de datos** cuadro de diálogo.

1. Haga clic en la flecha de lista desplegable en el `Customers` de tabla y elija **ComplexDataGridView** desde la lista de control.

## <a name="add-controls-to-the-form"></a>Agregar controles al formulario

Puede crear los controles enlazados a datos arrastrando elementos desde la **orígenes de datos** ventana hasta el formulario.

### <a name="to-create-data-bound-controls-on-the-form"></a>Para crear controles enlazados en el formulario

Arrastre el método main **clientes** nodo desde el **orígenes de datos** ventana hasta el formulario. Compruebe que la **ComplexDataGridView** control se usa para mostrar datos de la tabla.  

## <a name="running-the-application"></a>Ejecutar la aplicación

### <a name="to-run-the-application"></a>Para ejecutar la aplicación

Presione F5 para ejecutar la aplicación.

## <a name="next-steps"></a>Pasos siguientes

Según cuáles sean los requisitos de la aplicación, hay varios pasos que se pueden realizar después de crear un control que admite el enlace a datos. Entre los pasos más habituales están los siguientes:

- Colocar los controles personalizados en una biblioteca de controles para poder reutilizarlos en otras aplicaciones.

- Crear controles que admitan escenarios de búsqueda. Para obtener más información, consulte [crear un control de usuario de formularios Windows Forms que admita el enlace de datos de búsqueda](../data-tools/create-a-windows-forms-user-control-that-supports-lookup-data-binding.md).

## <a name="see-also"></a>Vea también

[Enlazar controles de Windows Forms a datos en Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)  
[Establecer el control que se creará al arrastrar desde la ventana Orígenes de datos](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md)  
[Controles de formularios Windows Forms](/dotnet/framework/winforms/controls/index)
