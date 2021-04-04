---
title: Crear un control de usuario Windows Forms con enlace de datos
description: Aprenda a crear un control de usuario Windows Forms que admita el enlace de datos complejo mediante la implementación de la clase ComplexBindingPropertiesAttribute.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data binding, user controls
- data binding, complex
- user controls [Visual Studio], complex data binding
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- data-storage
ms.openlocfilehash: ff8c641cc0b817b5f2a145af49c5e0accdc295d0
ms.sourcegitcommit: 80fc9a72e9a1aba2d417dbfee997fab013fc36ac
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/02/2021
ms.locfileid: "106216337"
---
# <a name="create-a-windows-forms-user-control-that-supports-complex-data-binding"></a>Creación de un control de usuario de Windows Forms que admita el enlace de datos complejo

Al mostrar los datos en los formularios de las aplicaciones Windows, puede elegir los controles existentes en el **cuadro de herramientas**. O bien, puede crear controles personalizados si la aplicación requiere funcionalidad que no está disponible en los controles estándar. En este tutorial se muestra cómo crear un control que implementa <xref:System.ComponentModel.ComplexBindingPropertiesAttribute>. Los controles que implementan <xref:System.ComponentModel.ComplexBindingPropertiesAttribute> contienen unas propiedades `DataSource` y `DataMember` que se pueden enlazar a datos. Tales controles son similares a <xref:System.Windows.Forms.DataGridView> o <xref:System.Windows.Forms.ListBox>.

Para obtener más información sobre la creación de controles, vea [desarrollar controles de Windows Forms en tiempo de diseño](/dotnet/framework/winforms/controls/developing-windows-forms-controls-at-design-time).

Al crear controles para usarlos en escenarios de enlace de datos, es necesario implementar uno de los atributos de enlace de datos siguientes:

|Uso de atributos de enlace de datos|
| - |
|Implemente el <xref:System.ComponentModel.DefaultBindingPropertyAttribute> en controles sencillos, como un <xref:System.Windows.Forms.TextBox>, que muestra una única columna (o propiedad) de datos. Para obtener más información, vea [crear un control de usuario Windows Forms que admita el enlace de datos simple](../data-tools/create-a-windows-forms-user-control-that-supports-simple-data-binding.md).|
|Implemente el <xref:System.ComponentModel.ComplexBindingPropertiesAttribute> en controles, como <xref:System.Windows.Forms.DataGridView>, que muestra listas (o tablas) de datos. (Este proceso se describe en esta página del tutorial.)|
|Implemente el <xref:System.ComponentModel.LookupBindingPropertiesAttribute> en controles, como <xref:System.Windows.Forms.ComboBox>, que muestren listas (o tablas) de datos, pero que también necesiten presentar una única columna o propiedad. Para obtener más información, vea [crear un control de usuario Windows Forms que admita el enlace de datos de búsqueda](../data-tools/create-a-windows-forms-user-control-that-supports-lookup-data-binding.md).|

En este tutorial se crea un control complejo que muestra las filas de datos de una tabla. En este ejemplo se utiliza la tabla `Customers` de la base de datos de ejemplo Northwind. El control de usuario complejo mostrará la tabla de clientes en una <xref:System.Windows.Forms.DataGridView> del control personalizado.

Durante este tutorial, aprenderá a:

- Agregue un nuevo **Control de usuario** a su proyecto.

- Diseñe visualmente el control de usuario.

- Implemente el atributo `ComplexBindingProperty`.

- Cree un conjunto de datos con el [Asistente para la configuración de orígenes de datos](../data-tools/media/data-source-configuration-wizard.png).

- Establezca la tabla **Customers** en la [ventana orígenes de datos](add-new-data-sources.md#data-sources-window) para usar el nuevo control complejo.

- Agregue el nuevo control arrastrándolo desde la ventana **Orígenes de datos** hasta **Form1**.

## <a name="prerequisites"></a>Requisitos previos

En este tutorial se usa SQL Server Express LocalDB y la base de datos de ejemplo Northwind.

1. Si no tiene SQL Server Express LocalDB, instálelo desde la [Página de descarga de SQL Server Express](https://www.microsoft.com/sql-server/sql-server-editions-express)o a través de la **instalador de Visual Studio**. En el **instalador de Visual Studio**, puede instalar SQL Server Express LocalDB como parte de la carga de trabajo de **procesamiento y almacenamiento de datos** , o como un componente individual.

1. Instale la base de datos de ejemplo Northwind siguiendo estos pasos:

    1. En Visual Studio, abra la ventana **Explorador de objetos de SQL Server** . (Explorador de objetos de SQL Server se instala como parte de la carga de trabajo de **procesamiento y almacenamiento de datos** en el instalador de Visual Studio). Expanda el nodo **SQL Server** . Haga clic con el botón secundario en la instancia de LocalDB y seleccione **nueva consulta**.

       Se abre una ventana del editor de consultas.

    1. Copie el [script de Transact-SQL Northwind](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true) en el portapapeles. Este script T-SQL crea la base de datos Northwind desde cero y la rellena con datos.

    1. Pegue el script T-SQL en el editor de consultas y, a continuación, elija el botón **Ejecutar** .

       Tras un breve período de tiempo, la consulta termina de ejecutarse y se crea la base de datos Northwind.

## <a name="create-a-windows-forms-app-project"></a>Crear un proyecto de aplicación de Windows Forms

El primer paso es crear un proyecto de **aplicación de Windows Forms** para C# o Visual Basic. Asigne el nombre **TutorialDeControlComplejo al proyecto**.

## <a name="add-a-user-control-to-the-project"></a>Agregar un control de usuario al proyecto

Dado que en este tutorial se crea un control complejo enlazable a datos a partir de un **control de usuario**, agregue un elemento de **control de usuario** al proyecto:

1. En el menú **Proyecto**, elija **Agregar control de usuario**.

1. Escriba **ComplexDataGridView** en el área **Nombre** y haga clic en **Agregar**.

    El control **ComplexDataGridView** se agrega al **Explorador de soluciones** y se abre en el diseñador.

## <a name="design-the-complexdatagridview-control"></a>Diseñar el control ComplexDataGridView

Para agregar un <xref:System.Windows.Forms.DataGridView> al control de usuario, arrastre un <xref:System.Windows.Forms.DataGridView> desde el **cuadro de herramientas** hasta la superficie de diseño del control de usuario.

## <a name="add-the-required-data-binding-attribute"></a>Agregar el atributo de enlace de datos requerido

En el caso de los controles complejos que admiten enlaces a datos, puede implementar el <xref:System.ComponentModel.ComplexBindingPropertiesAttribute>:

1. Cambie el control **ComplexDataGridView** a vista de código. En el menú **Ver**, seleccione **Código**.

1. Reemplace el código de `ComplexDataGridView` por lo siguiente:

    :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataDisplaying/CS/ComplexDataGridView.cs" id="Snippet4":::
    :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataDisplaying/VB/ComplexDataGridView.vb" id="Snippet4":::

1. En el menú **Compilar** , elija **Compilar solución**.

## <a name="create-a-data-source-from-your-database"></a>Crear un origen de datos a partir de la base de datos

Use el Asistente para la **configuración de orígenes de datos** para crear un origen de datos basado en la `Customers` tabla de la base de datos de ejemplo Northwind:

1. Para abrir la ventana **orígenes de datos** , en el menú **datos** , haga clic en **Mostrar orígenes de datos**.

2. En la ventana **orígenes de datos** , seleccione **Agregar nuevo origen de datos** para iniciar el Asistente para la configuración de orígenes de **datos** .

3. Seleccione **Base de datos** en la página **Elegir un tipo de datos de origen** y luego haga clic en **Siguiente**.

4. En la página **Elegir la conexión de datos** realice una de las siguientes operaciones:

   - Si una conexión de datos a la base de datos de ejemplo Northwind está disponible en la lista desplegable, selecciónela.

   - Seleccione **Nueva conexión** para iniciar el cuadro de diálogo **Agregar o modificar conexión**.

5. Si su base de datos requiere una contraseña, seleccione la opción para incluir datos confidenciales y haga clic en **Siguiente**.

6. Haga clic en **Siguiente** en la página **Guardar la cadena de conexión en el archivo de configuración de la aplicación**.

7. Expanda el nodo **Tablas** en la página **Elija los objetos de base de datos**.

8. Seleccione la tabla `Customers` y después haga clic en **Finalizar**.

   **NorthwindDataSet** se agrega al proyecto y la `Customers` tabla aparece en la ventana orígenes de **datos** .

## <a name="set-the-customers-table-to-use-the-complexdatagridview-control"></a>Establecer la tabla Customers para usar el control ComplexDataGridView

Dentro de la ventana **orígenes de datos** , puede establecer el control que se va a crear antes de arrastrar elementos al formulario:

1. Abra **Form1** en el diseñador.

1. Expanda el nodo **Customers** en la ventana **Orígenes de datos**.

1. Haga clic en la flecha de lista desplegable en la columna **Customers** y elija **Personalizar**.

1. Seleccione **ComplexDataGridView** de la lista de **Controles asociados** en el cuadro de diálogo **Opciones de personalización de la interfaz de usuario de datos**.

1. Haga clic en la flecha de lista desplegable en la tabla `Customers` y elija **ComplexDataGridView** de la lista de controles.

## <a name="add-controls-to-the-form"></a>Adición de controles al formulario

Puede crear los controles enlazados a datos arrastrando elementos desde la ventana **orígenes de datos** hasta el formulario. Arrastre el nodo **Customers** principal desde la ventana **Orígenes de datos** hasta el formulario. Compruebe que el control **ComplexDataGridView** se usa para mostrar los datos de la tabla.

## <a name="run-the-application"></a>Ejecución de la aplicación

Presione **F5** para ejecutar la aplicación.

## <a name="next-steps"></a>Pasos siguientes

Según cuáles sean los requisitos de la aplicación, hay varios pasos que se pueden realizar después de crear un control que admite el enlace a datos. Entre los pasos más habituales están los siguientes:

- Colocar los controles personalizados en una biblioteca de controles para poder reutilizarlos en otras aplicaciones.

- Crear controles que admitan escenarios de búsqueda. Para obtener más información, vea [crear un control de usuario Windows Forms que admita el enlace de datos de búsqueda](../data-tools/create-a-windows-forms-user-control-that-supports-lookup-data-binding.md).

## <a name="see-also"></a>Consulte también

- [Enlazar controles de Windows Forms a datos en Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)
- [Establecer el control que se creará al arrastrar desde la ventana Orígenes de datos](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md)
- [Windows Forms controles](/dotnet/framework/winforms/controls/index)
