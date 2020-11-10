---
title: Crear Windows Forms para buscar en datos
description: Lea un ejemplo de cómo crear un formulario de Windows Forms para buscar datos. Cree la aplicación, el origen de datos y el formulario de Windows Forms. Agregar parametrización. Probar la aplicación.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Windows Forms, searching data
- Windows Forms, displaying data
- parameters, displaying filtered data
- data [Visual Studio], parameterizing queries
- data [Visual Studio], searching
ms.assetid: 65ca79a9-7458-466c-af55-978cd24c549e
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 00b492c7aec41d30e972df93206f9e597ea82eb3
ms.sourcegitcommit: ed26b6e313b766c4d92764c303954e2385c6693e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/10/2020
ms.locfileid: "94435292"
---
# <a name="create-a-windows-form-to-search-data"></a>Crear Windows Forms para buscar en datos

Un escenario habitual de la aplicación es mostrar los datos seleccionados en un formulario. Por ejemplo, puede que desee mostrar los pedidos de un cliente concreto o los detalles de un pedido específico. En este caso, un usuario escribe información en un formulario y, a continuación, se ejecuta una consulta con la entrada del usuario como parámetro; es decir, los datos se seleccionan basándose en una consulta parametrizada. La consulta devuelve sólo los datos que satisfacen los criterios escritos por el usuario. Este tutorial muestra cómo crear una consulta que devuelve los clientes de una ciudad específica y cómo modificar la interfaz de usuario para que los usuarios puedan escribir el nombre de una ciudad y presionar un botón para ejecutar la consulta.

El uso de consultas parametrizadas ayuda a que la aplicación sea más eficaz, ya que permite a la base de datos realizar el trabajo que mejor sabe hacer: filtrar registros rápidamente. Al contrario, si solicita una tabla de base de datos completa, la transfiere por la red y, a continuación, utiliza la lógica de la aplicación para buscar los registros pertinentes, la aplicación puede tornarse más lenta y difícil de utilizar.

Puede Agregar consultas con parámetros a cualquier TableAdapter (y controles para aceptar valores de parámetro y ejecutar la consulta) mediante el cuadro de diálogo **generador de criterios de búsqueda** . Abra el cuadro de diálogo seleccionando el comando **Agregar consulta** del menú **Datos** (o en cualquier etiqueta inteligente del TableAdapter).

Las tareas ilustradas en este tutorial incluyen:

- Crear y configurar el origen de datos en la aplicación con el Asistente para la **configuración de orígenes de datos** .

- Establecer el tipo de colocación de los elementos en la ventana **orígenes de datos** .

- Crear controles que muestran datos arrastrando elementos desde la ventana **Orígenes de datos** hasta un formulario.

- Agregar controles para mostrar los datos en el formulario.

- Completando el cuadro de diálogo **generador de criterios de búsqueda** .

- Escribir parámetros en el formulario y ejecutar la consulta con parámetros.

## <a name="prerequisites"></a>Requisitos previos

En este tutorial se usa SQL Server Express LocalDB y la base de datos de ejemplo Northwind.

1. Si no tiene SQL Server Express LocalDB, instálelo desde la [Página de descarga de SQL Server Express](https://www.microsoft.com/sql-server/sql-server-editions-express)o a través de la **instalador de Visual Studio**. En el **instalador de Visual Studio** , puede instalar SQL Server Express LocalDB como parte de la carga de trabajo de **procesamiento y almacenamiento de datos** , o como un componente individual.

2. Instale la base de datos de ejemplo Northwind siguiendo estos pasos:

    1. En Visual Studio, abra la ventana **Explorador de objetos de SQL Server** . (Explorador de objetos de SQL Server se instala como parte de la carga de trabajo de **procesamiento y almacenamiento de datos** en el **instalador de Visual Studio** ). Expanda el nodo **SQL Server** . Haga clic con el botón secundario en la instancia de LocalDB y seleccione **nueva consulta**.

       Se abre una ventana del editor de consultas.

    2. Copie el [script de Transact-SQL Northwind](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true) en el portapapeles. Este script T-SQL crea la base de datos Northwind desde cero y la rellena con datos.

    3. Pegue el script T-SQL en el editor de consultas y, a continuación, elija el botón **Ejecutar** .

       Tras un breve período de tiempo, la consulta termina de ejecutarse y se crea la base de datos Northwind.

## <a name="create-the-windows-forms-application"></a>Creación de la aplicación Windows Forms

Cree un nuevo proyecto de **aplicación de Windows Forms** para C# o Visual Basic. Asigne al proyecto el nombre **WindowsSearchForm**.

## <a name="create-the-data-source"></a>Crear el origen de datos

Este paso crea un origen de datos a partir de una base de datos utilizando el asistente para la **Configuración de origen de datos** :

1. Para abrir la ventana **orígenes de datos** , en el menú **datos** , haga clic en **Mostrar orígenes de datos**.

2. En la ventana **orígenes de datos** , seleccione **Agregar nuevo origen de datos** para iniciar el Asistente para la configuración de orígenes de **datos** .

3. Seleccione **Base de datos** en la página **Elegir un tipo de datos de origen** y luego haga clic en **Siguiente**.

4. En la página **Elegir la conexión de datos** realice una de las siguientes operaciones:

    - Si una conexión de datos a la base de datos de ejemplo Northwind está disponible en la lista desplegable, selecciónela.

    - Seleccione **Nueva conexión** para iniciar el cuadro de diálogo **Agregar o modificar conexión**.

5. Si su base de datos requiere una contraseña, seleccione la opción para incluir datos confidenciales y haga clic en **Siguiente**.

6. Haga clic en **Siguiente** en la página **Guardar la cadena de conexión en el archivo de configuración de la aplicación**.

7. Expanda el nodo **Tablas** en la página **Elija los objetos de base de datos**.

8. Seleccione la tabla **Customers** y, a continuación, haga clic en **Finalizar**.

     Se agrega al proyecto **NorthwindDataSet** y la tabla **Customers** aparece en la ventana **Orígenes de datos**.

## <a name="create-the-form"></a> Crear el formulario

Puede crear los controles enlazados a datos arrastrando elementos desde la ventana **Orígenes de datos** al formulario:

1. Expanda el nodo **Customers** en la ventana **Orígenes de datos**.

2. Arrastre el nodo **Customers** desde la ventana **Orígenes de datos** hasta el formulario.

     En el formulario aparecen un control <xref:System.Windows.Forms.DataGridView> y una barra de herramientas (<xref:System.Windows.Forms.BindingNavigator>) para navegar por los registros. En la bandeja de componentes aparecen [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md), CustomersTableAdapter, <xref:System.Windows.Forms.BindingSource> y <xref:System.Windows.Forms.BindingNavigator>.

## <a name="add-parameterization-search-functionality-to-the-query"></a>Agregar parametrización (funcionalidad de búsqueda) a la consulta

Puede Agregar una cláusula WHERE a la consulta original mediante el cuadro de diálogo **generador de criterios de búsqueda** :

1. Seleccione el control <xref:System.Windows.Forms.DataGridView> y, a continuación, elija **Agregar consulta** en el menú **Datos**.

2. Escriba **FillByCity** en el área **nuevo nombre de consulta** en el cuadro de diálogo **generador de criterios de búsqueda** .

3. Agregue `WHERE City = @City` a la consulta en el área **Texto de la consulta**.

     La consulta debe ser similar a lo siguiente:

     ```sql
     SELECT CustomerID, CompanyName, ContactName, ContactTitle,
          Address, City, Region, PostalCode, Country, Phone, Fax
     FROM Customers
     WHERE City = @City
     ```

    > [!NOTE]
    > Los orígenes de datos de acceso y OLE DB utilizan el signo de interrogación ('? ') para denotar los parámetros, por lo que la cláusula WHERE tendría el siguiente aspecto: `WHERE City = ?` .

4. Haga clic en **Aceptar** para cerrar el cuadro de diálogo **Generador de criterios de búsqueda**.

     **FillByCityToolStrip** se agrega al formulario.

## <a name="test-the-application"></a>Prueba de la aplicación

La ejecución de la aplicación abre el formulario y hace que esté listo para tomar el parámetro como entrada:

1. Presione **F5** para ejecutar la aplicación.

2. Escriba **Londres** en el cuadro de texto **Ciudad** y haga clic en **FillByCity**.

     La cuadrícula de datos se rellena con los clientes que cumplen los criterios. En este ejemplo, la cuadrícula de datos muestra sólo los clientes que tienen un valor de **Londres** en su columna **Ciudad**.

## <a name="next-steps"></a>Pasos siguientes

Dependiendo de los requisitos de la aplicación, existen varios pasos que se pueden realizar después de crear un formulario parametrizado. Entre las mejoras que podría realizar se incluyen:

- Agregar controles que muestran datos relacionados. Para obtener más información, vea [relaciones en conjuntos de](relationships-in-datasets.md)datos.

- Modificar el conjunto de datos agregando o quitando objetos de la base de datos. Para obtener más información, vea [Crear y configurar conjuntos de datos](../data-tools/create-and-configure-datasets-in-visual-studio.md).

## <a name="see-also"></a>Consulte también

- [Enlazar controles de Windows Forms a datos en Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)
