---
title: Usar tablas de búsqueda en el enlace de datos Windows Forms
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data binding, user controls
- LookupBindingPropertiesAttribute class, examples
- user controls [Visual Basic], creating
ms.assetid: c48b4d75-ccfc-4950-8b14-ff8adbfe4208
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: fe2289a54dba0c3b3e34de54991e9b7cfbee4c93
ms.sourcegitcommit: 4ae5e9817ad13edd05425febb322b5be6d3c3425
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/11/2020
ms.locfileid: "90037398"
---
# <a name="create-a-windows-forms-user-control-that-supports-lookup-data-binding"></a>Crear un control de usuario de Windows Forms que admita el enlace de datos de búsqueda

Cuando muestra datos en formularios Windows Forms, puede elegir controles existentes en el **Cuadro de herramientas** o puede crear controles personalizados si la aplicación requiere funcionalidad que no está disponible en los controles estándar. En este tutorial se muestra cómo crear un control que implementa <xref:System.ComponentModel.LookupBindingPropertiesAttribute>. Los controles que implementan <xref:System.ComponentModel.LookupBindingPropertiesAttribute> pueden contener tres propiedades que se pueden enlazar a los datos. Tales controles son similares a <xref:System.Windows.Forms.ComboBox>.

Para obtener más información sobre la creación de controles, vea [desarrollar controles de Windows Forms en tiempo de diseño](/dotnet/framework/winforms/controls/developing-windows-forms-controls-at-design-time).

Al crear controles para usarlos en escenarios de enlace de datos, es necesario implementar uno de los atributos de enlace de datos siguientes:

|Uso de atributos de enlace de datos|
| - |
|Implemente el <xref:System.ComponentModel.DefaultBindingPropertyAttribute> en controles sencillos, como un <xref:System.Windows.Forms.TextBox>, que muestra una única columna (o propiedad) de datos. Para obtener más información, vea [crear un control de usuario Windows Forms que admita el enlace de datos simple](../data-tools/create-a-windows-forms-user-control-that-supports-simple-data-binding.md).|
|Implemente el <xref:System.ComponentModel.ComplexBindingPropertiesAttribute> en controles, como <xref:System.Windows.Forms.DataGridView>, que muestra listas (o tablas) de datos. Para obtener más información, vea [crear un control de usuario Windows Forms que admita el enlace de datos complejo](../data-tools/create-a-windows-forms-user-control-that-supports-complex-data-binding.md).|
|Implemente el <xref:System.ComponentModel.LookupBindingPropertiesAttribute> en controles, como <xref:System.Windows.Forms.ComboBox>, que muestren listas (o tablas) de datos pero que también necesiten presentar una única columna o propiedad. (Este proceso se describe en esta página del tutorial.)|

Este tutorial crea un control de búsqueda que se enlaza a los datos de dos tablas. En este ejemplo se utilizan las tablas `Customers` y `Orders` de la base de datos de ejemplo Northwind. El control de búsqueda se enlaza al `CustomerID` campo de la `Orders` tabla. Utiliza este valor para buscar `CompanyName` en la `Customers` tabla.

Durante este tutorial, aprenderá a:

- Cree una nueva **aplicación Windows Forms**.

- Agregue un nuevo **Control de usuario** a su proyecto.

- Diseñe visualmente el control de usuario.

- Implemente el atributo `LookupBindingProperty`.

- Cree un conjunto de datos con el Asistente para la **configuración de orígenes de datos** .

- Establezca la columna **CustomerID** de la tabla **Pedidos** en la ventana **Orígenes de datos** para utilizar el nuevo control.

- Cree un formulario para mostrar los datos en el nuevo control.

## <a name="prerequisites"></a>Requisitos previos

En este tutorial se usa SQL Server Express LocalDB y la base de datos de ejemplo Northwind.

1. Si no tiene SQL Server Express LocalDB, instálelo desde la [Página de descarga de SQL Server Express](https://www.microsoft.com/sql-server/sql-server-editions-express)o a través de la **instalador de Visual Studio**. En el **instalador de Visual Studio**, puede instalar SQL Server Express LocalDB como parte de la carga de trabajo de **procesamiento y almacenamiento de datos** , o como un componente individual.

2. Instale la base de datos de ejemplo Northwind siguiendo estos pasos:

    1. En Visual Studio, abra la ventana **Explorador de objetos de SQL Server** . (Explorador de objetos de SQL Server se instala como parte de la carga de trabajo de **procesamiento y almacenamiento de datos** en el instalador de Visual Studio). Expanda el nodo **SQL Server** . Haga clic con el botón secundario en la instancia de LocalDB y seleccione **nueva consulta**.

       Se abre una ventana del editor de consultas.

    2. Copie el [script de Transact-SQL Northwind](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true) en el portapapeles. Este script T-SQL crea la base de datos Northwind desde cero y la rellena con datos.

    3. Pegue el script T-SQL en el editor de consultas y, a continuación, elija el botón **Ejecutar** .

       Tras un breve período de tiempo, la consulta termina de ejecutarse y se crea la base de datos Northwind.

## <a name="create-a-windows-forms-app-project"></a>Crear un proyecto de aplicación de Windows Forms

El primer paso es crear un proyecto de **aplicación de Windows Forms** .

1. En Visual Studio, en el menú **Archivo**, seleccione **Nuevo** > **Proyecto**.

2. Expanda **Visual C#** o **Visual Basic** en el panel izquierdo y, a continuación, seleccione **escritorio de Windows**.

3. En el panel central, seleccione el tipo de proyecto **Windows Forms aplicación** .

4. Asigne al proyecto el nombre **LookupControlWalkthrough**y, a continuación, elija **Aceptar**.

     El proyecto **LookupControlWalkthrough** se crea y se agrega al **Explorador de soluciones**.

## <a name="add-a-user-control-to-the-project"></a>Agregar un control de usuario al proyecto

Este tutorial crea un control de búsqueda a partir de un **Control de usuario**, por lo que debe agregar un elemento **Control de usuario** al proyecto **LookupControlWalkthrough**.

1. En el menú **Proyecto**, elija **Agregar control de usuario**.

2. Escriba `LookupBox` en el área **nombre** y, a continuación, haga clic en **Agregar**.

     El control **LookupBox** se agrega al **Explorador de soluciones** y se abre en el diseñador.

## <a name="design-the-lookupbox-control"></a>Diseñar el control LookupBox

Para diseñar el control LookupBox, arrastre un control <xref:System.Windows.Forms.ComboBox> desde el **cuadro de herramientas** hasta la superficie de diseño del control de usuario.

## <a name="add-the-required-data-binding-attribute"></a>Agregar el atributo de enlace de datos requerido

Para controles de búsqueda que admiten el enlace de datos, puede implementar <xref:System.ComponentModel.LookupBindingPropertiesAttribute>.

1. Cambie el control **LookupBox** a vista de código. (En el menú **Ver**, elija **Código**.)

2. Reemplace el código de `LookupBox` por lo siguiente:

     [!code-vb[VbRaddataDisplaying#5](../data-tools/codesnippet/VisualBasic/create-a-windows-forms-user-control-that-supports-lookup-data-binding_1.vb)]
     [!code-csharp[VbRaddataDisplaying#5](../data-tools/codesnippet/CSharp/create-a-windows-forms-user-control-that-supports-lookup-data-binding_1.cs)]

3. En el menú **Compilar** , elija **Compilar solución**.

## <a name="create-a-data-source-from-your-database"></a>Crear un origen de datos a partir de la base de datos

En este paso se crea un origen de datos utilizando el **Asistente para configuración de orígenes de datos** basado en las tablas `Customers` y `Orders` de la base de datos de ejemplo Northwind.

1. Para abrir la ventana **orígenes de datos** , en el menú **datos** , haga clic en **Mostrar orígenes de datos**.

2. En la ventana **orígenes de datos** , seleccione **Agregar nuevo origen de datos** para iniciar el Asistente para la configuración de orígenes de **datos** .

3. Seleccione **Base de datos** en la página **Elegir un tipo de datos de origen** y luego haga clic en **Siguiente**.

4. En la página **Elegir la conexión de datos** realice una de las siguientes operaciones:

    - Si una conexión de datos a la base de datos de ejemplo Northwind está disponible en la lista desplegable, selecciónela.

    - Seleccione **Nueva conexión** para iniciar el cuadro de diálogo **Agregar o modificar conexión**.

5. Si su base de datos requiere una contraseña, seleccione la opción para incluir datos confidenciales y haga clic en **Siguiente**.

6. Haga clic en **Siguiente** en la página **Guardar la cadena de conexión en el archivo de configuración de la aplicación**.

7. Expanda el nodo **Tablas** en la página **Elija los objetos de base de datos**.

8. Seleccione las tablas `Customers` y `Orders` y después haga clic en **Finalizar**.

     **NorthwindDataSet** se agrega al proyecto y las tablas `Customers` y `Orders` aparecen en la ventana **Orígenes de datos**.

## <a name="set-the-customerid-column-of-the-orders-table-to-use-the-lookupbox-control"></a>Establecer la columna CustomerID de la tabla Orders para usar el control LookupBox

Dentro de la ventana **Orígenes de datos** puede establecer el control que se va a crear antes de arrastrar elementos a un formulario.

1. Abra **Form1** en el diseñador.

2. Expanda el nodo **Customers** en la ventana **Orígenes de datos**.

3. Expanda el nodo **Orders** (incluido en el nodo **Customers** debajo de la columna **Fax**).

4. Haga clic en la flecha de lista desplegable en el nodo **Orders** y elija **Detalles** de la lista de control.

5. Haga clic en la flecha de lista desplegable en la columna **CustomerID** (del nodo **Orders**) y elija **Personalizar**.

6. Seleccione **LookupBox** de la lista de **Controles asociados** en el cuadro de diálogo **Opciones de personalización de la interfaz de usuario de datos**.

7. Haga clic en **OK**.

8. Haga clic en la flecha de lista desplegable en la columna **CustomerID** y elija **LookupBox**.

## <a name="add-controls-to-the-form"></a>Agregar controles al formulario

Puede crear los controles enlazados a datos arrastrando elementos desde la ventana **Orígenes de datos** al **Form1**.

Para crear controles enlazados a datos en Windows Forms, arrastre el nodo **Orders** desde la ventana **orígenes de datos** hasta Windows Forms y compruebe que el control **LookupBox** se usa para mostrar los datos de la `CustomerID` columna.

## <a name="bind-the-control-to-look-up-companyname-from-the-customers-table"></a>Enlazar el control para buscar CompanyName desde la tabla customers

Para configurar los enlaces de búsqueda, seleccione el nodo principal **Customers** en la ventana **orígenes de datos** y arrástrelo al cuadro combinado de **CustomerIDLookupBox** en **Form1**.

Así configura el enlace de datos para mostrar el valor `CompanyName` de la tabla `Customers` a la vez que mantiene el valor `CustomerID` de la tabla `Orders`.

## <a name="run-the-application"></a>Ejecución de la aplicación

- Presione **F5** para ejecutar la aplicación.

- Navegue por algunos registros y compruebe que `CompanyName` aparece en el control `LookupBox`.

## <a name="see-also"></a>Consulte también

- [Enlazar controles de Windows Forms a datos en Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)
