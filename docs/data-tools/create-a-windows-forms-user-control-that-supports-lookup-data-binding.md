---
title: 'Utilizar tablas de búsqueda en el enlace de datos: los controles de Windows Forms | Microsoft Docs'
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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: fc8c29ae4d146a0ec66a362fd6fb99251d726906
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/22/2019
ms.locfileid: "60056060"
---
# <a name="create-a-windows-forms-user-control-that-supports-lookup-data-binding"></a>Crear un control de usuario de Windows Forms que admita el enlace de datos de búsqueda

Cuando muestra datos en formularios Windows Forms, puede elegir controles existentes en el **Cuadro de herramientas** o puede crear controles personalizados si la aplicación requiere funcionalidad que no está disponible en los controles estándar. En este tutorial se muestra cómo crear un control que implementa <xref:System.ComponentModel.LookupBindingPropertiesAttribute>. Los controles que implementan <xref:System.ComponentModel.LookupBindingPropertiesAttribute> pueden contener tres propiedades que se pueden enlazar a los datos. Tales controles son similares a <xref:System.Windows.Forms.ComboBox>.

Para obtener más información sobre la creación de controles, vea [controla el desarrollo de Windows Forms en tiempo de diseño](/dotnet/framework/winforms/controls/developing-windows-forms-controls-at-design-time).

Al crear controles para usarlos en escenarios de enlace de datos, es necesario implementar uno de los atributos de enlace de datos siguientes:

|Uso de atributos de enlace de datos|
| - |
|Implemente el <xref:System.ComponentModel.DefaultBindingPropertyAttribute> en controles sencillos, como un <xref:System.Windows.Forms.TextBox>, que muestra una única columna (o propiedad) de datos. Para obtener más información, consulte [crear un control de usuario de Windows Forms que admita el enlace de datos simple](../data-tools/create-a-windows-forms-user-control-that-supports-simple-data-binding.md).|
|Implemente el <xref:System.ComponentModel.ComplexBindingPropertiesAttribute> en controles, como <xref:System.Windows.Forms.DataGridView>, que muestra listas (o tablas) de datos. Para obtener más información, consulte [crear un control de usuario de Windows Forms que admita el enlace de datos complejos](../data-tools/create-a-windows-forms-user-control-that-supports-complex-data-binding.md).|
|Implemente el <xref:System.ComponentModel.LookupBindingPropertiesAttribute> en controles, como <xref:System.Windows.Forms.ComboBox>, que muestren listas (o tablas) de datos pero que también necesiten presentar una única columna o propiedad. (Este proceso se describe en esta página del tutorial.)|

Este tutorial crea un control de búsqueda que se enlaza a los datos de dos tablas. En este ejemplo se utilizan las tablas `Customers` y `Orders` de la base de datos de ejemplo Northwind. El control de búsqueda está enlazado a la `CustomerID` arrastrándolo desde la `Orders` tabla. Usa este valor para buscar el `CompanyName` desde el `Customers` tabla.

Durante este tutorial, obtendrá información sobre cómo:

- Crear una nueva **aplicación de Windows Forms**.

- Agregue un nuevo **Control de usuario** a su proyecto.

- Diseñe visualmente el control de usuario.

- Implemente el atributo `LookupBindingProperty`.

- Crear un conjunto de datos con el **configuración origen de datos** asistente.

- Establezca la columna **CustomerID** de la tabla **Pedidos** en la ventana **Orígenes de datos** para utilizar el nuevo control.

- Cree un formulario para mostrar los datos en el nuevo control.

## <a name="prerequisites"></a>Requisitos previos

En este tutorial usa SQL Server Express LocalDB y la base de datos de ejemplo Northwind.

1. Si no tiene SQL Server Express LocalDB, instálelo de desde el [página de descarga de SQL Server Express](https://www.microsoft.com/sql-server/sql-server-editions-express), o a través del **instalador de Visual Studio**. En el **instalador de Visual Studio**, puede instalar SQL Server Express LocalDB como parte de la **procesamiento y almacenamiento de datos** carga de trabajo, o como un componente individual.

2. Instalar la base de datos de ejemplo Northwind, siga estos pasos:

    1. En Visual Studio, abra el **Explorador de objetos de SQL Server** ventana. (Explorador de objetos de SQL Server se instala como parte de la **procesamiento y almacenamiento de datos** carga de trabajo en el instalador de Visual Studio.) Expanda el **SQL Server** nodo. Haga doble clic en la instancia de LocalDB y seleccione **nueva consulta**.

       Se abre una ventana del editor de consultas.

    2. Copia el [script Transact-SQL de Northwind](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true) en el Portapapeles. Este script de Transact-SQL crea la base de datos Northwind desde el principio y lo rellena con datos.

    3. Pegue el script de Transact-SQL en el editor de consultas y, a continuación, elija el **Execute** botón.

       Después de un breve tiempo, finalice la consulta y se crea la base de datos Northwind.

## <a name="create-a-windows-forms-app-project"></a>Crear un proyecto de aplicación de Windows Forms

El primer paso es crear un **aplicación de Windows Forms** proyecto.

1. En Visual Studio, en el **archivo** menú, seleccione **New** > **proyecto**.

2. Expanda el **Visual C#** o **Visual Basic** en el panel izquierdo, seleccione **Windows Desktop**.

3. En el panel central, seleccione la **aplicación de Windows Forms** tipo de proyecto.

4. Denomine el proyecto **LookupControlWalkthrough**y, a continuación, elija **Aceptar**.

     El proyecto **LookupControlWalkthrough** se crea y se agrega al **Explorador de soluciones**.

## <a name="add-a-user-control-to-the-project"></a>Agregar un control de usuario al proyecto

Este tutorial crea un control de búsqueda a partir de un **Control de usuario**, por lo que debe agregar un elemento **Control de usuario** al proyecto **LookupControlWalkthrough**.

1. En el menú **Proyecto**, elija **Agregar control de usuario**.

2. Tipo `LookupBox` en el **nombre** área y, a continuación, haga clic en **agregar**.

     El control **LookupBox** se agrega al **Explorador de soluciones** y se abre en el diseñador.

## <a name="design-the-lookupbox-control"></a>Diseñar el control LookupBox

Para diseñar el control LookupBox, arrastre un <xref:System.Windows.Forms.ComboBox> desde el **cuadro de herramientas** hasta la superficie de diseño del control de usuario.

## <a name="add-the-required-data-binding-attribute"></a>Agregue el atributo de enlace de datos requerido

Para controles de búsqueda que admiten el enlace de datos, puede implementar <xref:System.ComponentModel.LookupBindingPropertiesAttribute>.

1. Cambie el control **LookupBox** a vista de código. (En el menú **Ver**, elija **Código**.)

2. Reemplace el código de `LookupBox` por lo siguiente:

     [!code-vb[VbRaddataDisplaying#5](../data-tools/codesnippet/VisualBasic/create-a-windows-forms-user-control-that-supports-lookup-data-binding_1.vb)]
     [!code-csharp[VbRaddataDisplaying#5](../data-tools/codesnippet/CSharp/create-a-windows-forms-user-control-that-supports-lookup-data-binding_1.cs)]

3. En el menú **Compilar** , elija **Compilar solución**.

## <a name="create-a-data-source-from-your-database"></a>Crear un origen de datos de la base de datos

En este paso se crea un origen de datos utilizando el **Asistente para configuración de orígenes de datos** basado en las tablas `Customers` y `Orders` de la base de datos de ejemplo Northwind.

1. Para abrir el **orígenes de datos** ventana, en el **datos** menú, haga clic en **Mostrar orígenes de datos**.

2. En la ventana **Orígenes de datos**, seleccione **Agregar nuevo origen de datos** para iniciar el **Asistente para configuración de orígenes de datos**.

3. Seleccione **Base de datos** en la página **Elegir un tipo de datos de origen** y luego haga clic en **Siguiente**.

4. En la página **Elegir la conexión de datos** realice una de las siguientes operaciones:

    - Si una conexión de datos a la base de datos de ejemplo Northwind está disponible en la lista desplegable, selecciónela.

    - Seleccione **Nueva conexión** para iniciar el cuadro de diálogo **Agregar o modificar conexión**.

5. Si su base de datos requiere una contraseña, seleccione la opción para incluir datos confidenciales y haga clic en **Siguiente**.

6. Haga clic en **Siguiente** en la página **Guardar la cadena de conexión en el archivo de configuración de la aplicación**.

7. Expanda el nodo **Tablas** en la página **Elija los objetos de base de datos**.

8. Seleccione las tablas `Customers` y `Orders` y después haga clic en **Finalizar**.

     **NorthwindDataSet** se agrega al proyecto y las tablas `Customers` y `Orders` aparecen en la ventana **Orígenes de datos**.

## <a name="set-the-customerid-column-of-the-orders-table-to-use-the-lookupbox-control"></a>Establezca la columna CustomerID de la tabla Orders para utilizar el control LookupBox

Dentro de la ventana **Orígenes de datos** puede establecer el control que se va a crear antes de arrastrar elementos a un formulario.

1. Abra **Form1** en el diseñador.

2. Expanda el nodo **Customers** en la ventana **Orígenes de datos**.

3. Expanda el nodo **Orders** (incluido en el nodo **Customers** debajo de la columna **Fax**).

4. Haga clic en la flecha de lista desplegable en el nodo **Orders** y elija **Detalles** de la lista de control.

5. Haga clic en la flecha de lista desplegable en la columna **CustomerID** (del nodo **Orders**) y elija **Personalizar**.

6. Seleccione **LookupBox** de la lista de **Controles asociados** en el cuadro de diálogo **Opciones de personalización de la interfaz de usuario de datos**.

7. Haga clic en **Aceptar**.

8. Haga clic en la flecha de lista desplegable en la columna **CustomerID** y elija **LookupBox**.

## <a name="add-controls-to-the-form"></a>Agregar controles al formulario

Puede crear los controles enlazados a datos arrastrando elementos desde la ventana **Orígenes de datos** al **Form1**.

Para crear controles enlazados a datos en el formulario de Windows, arrastre el **pedidos** nodo desde el **orígenes de datos** ventana hasta el formulario de Windows y compruebe que la **LookupBox** control es utilizado para mostrar los datos en la `CustomerID` columna.

## <a name="bind-the-control-to-look-up-companyname-from-the-customers-table"></a>Enlazar el control para buscar CompanyName desde la tabla Customers

Para configurar los enlaces de búsqueda, seleccione el método main **clientes** nodo en el **orígenes de datos** ventana y arrastre en el cuadro combinado del cuadro en el **CustomerIDLookupBox** en **Form1**.

Así configura el enlace de datos para mostrar el valor `CompanyName` de la tabla `Customers` a la vez que mantiene el valor `CustomerID` de la tabla `Orders`.

## <a name="run-the-application"></a>Ejecutar la aplicación

- Presione **F5** para ejecutar la aplicación.

- Navegue por algunos registros y compruebe que `CompanyName` aparece en el control `LookupBox`.

## <a name="see-also"></a>Vea también

- [Enlazar controles de Windows Forms a datos en Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)