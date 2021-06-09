---
title: Crear Windows Forms para buscar en datos
description: Lea un ejemplo de cómo crear un formulario Windows Form para buscar datos. Cree la aplicación, el origen de datos y el formulario de Windows Form. Agregar parametrización. Pruebe la aplicación.
ms.custom: SEO-VS-2020
ms.date: 06/07/2021
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
manager: jmartens
ms.workload:
- data-storage
ms.openlocfilehash: 2ce9d3eeebf42855ad69f02b2d72330190a2b390
ms.sourcegitcommit: 01a411cd7ae3488b7b979a947bca92fd296a98e9
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/09/2021
ms.locfileid: "111761100"
---
# <a name="create-a-windows-form-to-search-data"></a>Crear Windows Forms para buscar en datos

Un escenario habitual de la aplicación es mostrar los datos seleccionados en un formulario. Por ejemplo, puede que desee mostrar los pedidos de un cliente concreto o los detalles de un pedido específico. En este caso, un usuario escribe información en un formulario y, a continuación, se ejecuta una consulta con la entrada del usuario como parámetro; es decir, los datos se seleccionan basándose en una consulta parametrizada. La consulta devuelve sólo los datos que satisfacen los criterios escritos por el usuario. Este tutorial muestra cómo crear una consulta que devuelve los clientes de una ciudad específica y cómo modificar la interfaz de usuario para que los usuarios puedan escribir el nombre de una ciudad y presionar un botón para ejecutar la consulta.

El uso de consultas parametrizadas ayuda a que la aplicación sea más eficaz, ya que permite a la base de datos realizar el trabajo que mejor sabe hacer: filtrar registros rápidamente. Al contrario, si solicita una tabla de base de datos completa, la transfiere por la red y, a continuación, utiliza la lógica de la aplicación para buscar los registros pertinentes, la aplicación puede tornarse más lenta y difícil de utilizar.

Puede agregar consultas parametrizadas a cualquier TableAdapter (y controles para aceptar valores de parámetro y ejecutar la consulta), mediante el cuadro de diálogo Generador de criterios **de** búsqueda. Abra el cuadro de diálogo seleccionando el comando **Agregar consulta** del menú **Datos** (o en cualquier etiqueta inteligente del TableAdapter).

Las tareas ilustradas en este tutorial incluyen:

- Creación y configuración del origen de datos en la aplicación con el Asistente **para configuración del origen de** datos.

- Establecer el tipo de colocación de los elementos en la **ventana Orígenes de** datos.

- Crear controles que muestran datos arrastrando elementos desde la ventana **Orígenes de datos** hasta un formulario.

- Agregar controles para mostrar los datos en el formulario.

- Completar el cuadro **de diálogo Generador de criterios de** búsqueda.

- Escribir parámetros en el formulario y ejecutar la consulta parametrizada.

> [!NOTE]
> Los procedimientos de este artículo solo se aplican a .NET Framework Windows Forms proyectos, no a proyectos de .NET Core Windows Forms.

## <a name="prerequisites"></a>Requisitos previos

Debe tener instalada la **carga de trabajo Almacenamiento y procesamiento** de datos. Vea [Modificación de Visual Studio](../install/modify-visual-studio.md).

En este tutorial se SQL Server Express LocalDB y la base de datos de ejemplo Northwind.

1. Si no tiene una SQL Server Express LocalDB, instálla [](https://www.microsoft.com/sql-server/sql-server-editions-express)desde la página de descarga de SQL Server Express o a través del **Instalador de Visual Studio**. En el **Instalador de Visual Studio**, puede instalar SQL Server Express LocalDB como parte  de la carga de trabajo Almacenamiento y procesamiento de datos, o como un componente individual.

2. Instale la base de datos de ejemplo Northwind siguiendo estos pasos:

    1. En Visual Studio, abra **Explorador de objetos de SQL Server** ventana. (Explorador de objetos de SQL Server se instala como parte de la carga de trabajo Almacenamiento y **procesamiento** de datos en **la Instalador de Visual Studio**). Expanda el **SQL Server** nodo. Haga clic con el botón derecho en la instancia de LocalDB y seleccione **Nueva consulta.**

       Se abre una ventana del editor de consultas.

    2. Copie el [script de Transact-SQL Northwind](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true) en el Portapapeles. Este script de T-SQL crea la base de datos Northwind desde cero y la rellena con datos.

    3. Pegue el script de T-SQL en el editor de consultas y, a continuación, elija **el botón** Ejecutar.

       Después de un breve período de tiempo, la consulta termina de ejecutarse y se crea la base de datos Northwind.

## <a name="create-the-windows-forms-application"></a>Creación de la Windows Forms aplicación

:::moniker range="vs-2017"

Cree un nuevo **proyecto Windows Forms App (.NET Framework)** para C# o Visual Basic. Asigne al proyecto el nombre **WindowsSearchForm**.

## <a name="create-the-data-source"></a>Creación del origen de datos

Este paso crea un origen de datos a partir de una base de datos utilizando el asistente para la **Configuración de origen de datos**:

1. Para abrir la ventana **Orígenes de** datos, en el **menú Datos** , haga clic en Mostrar orígenes **de datos**.

2. En la **ventana Orígenes de** datos, seleccione Agregar nuevo origen de datos **para** iniciar el Asistente para configuración del **origen de** datos.

3. Seleccione **Base de datos** en la página **Elegir un tipo de datos de origen** y luego haga clic en **Siguiente**.

4. En la página **Elegir la conexión de datos** realice una de las siguientes operaciones:

    - Si una conexión de datos a la base de datos de ejemplo Northwind está disponible en la lista desplegable, selecciónela.

    - Seleccione **Nueva conexión** para iniciar el cuadro de diálogo **Agregar o modificar conexión**.

5. Si su base de datos requiere una contraseña, seleccione la opción para incluir datos confidenciales y haga clic en **Siguiente**.

6. Haga clic en **Siguiente** en la página **Guardar la cadena de conexión en el archivo de configuración de la aplicación**.

7. Expanda el nodo **Tablas** en la página **Elija los objetos de base de datos**.

8. Seleccione la tabla **Customers** y, a continuación, haga clic en **Finalizar**.

     Se agrega al proyecto **NorthwindDataSet** y la tabla **Customers** aparece en la ventana **Orígenes de datos**.

:::moniker-end

:::moniker range=">=vs-2019"

Cree un nuevo **proyecto Windows Forms App (.NET Framework)** para C# o Visual Basic. Asigne al proyecto el nombre **WindowsSearchForm**.

## <a name="create-the-data-source"></a>Creación del origen de datos

Este paso crea un origen de datos a partir de una base de datos utilizando el asistente para la **Configuración de origen de datos**:

1. Para abrir la **ventana Orígenes de** datos, use la búsqueda rápida **(Ctrl** + **Q)** y busque **Orígenes de datos**.

1. En la **ventana Orígenes de** datos, seleccione Agregar nuevo origen de datos **para** iniciar el Asistente para configuración del **origen de** datos.

1. Seleccione **Base de datos** en la página **Elegir un tipo de datos de origen** y luego haga clic en **Siguiente**.

1. En la pantalla **Elegir un modelo de base de** datos, elija Conjunto **de** datos y, a continuación, haga clic **en Siguiente.**

1. En la página **Elegir la conexión de datos** realice una de las siguientes operaciones:

    - Si una conexión de datos a la base de datos de ejemplo Northwind está disponible en la lista desplegable, selecciónela.

    - Seleccione **Nueva conexión** para iniciar el cuadro de diálogo **Agregar o modificar conexión**.

1. Haga clic en **Siguiente** en la página **Guardar la cadena de conexión en el archivo de configuración de la aplicación**.

1. Expanda el nodo **Tablas** en la página **Elija los objetos de base de datos**.

1. Seleccione la tabla **Customers** y, a continuación, haga clic en **Finalizar**.

     Se agrega al proyecto **NorthwindDataSet** y la tabla **Customers** aparece en la ventana **Orígenes de datos**.

:::moniker-end

## <a name="create-the-form"></a> Crear el formulario

Puede crear los controles enlazados a datos arrastrando elementos desde la ventana **Orígenes de datos** al formulario:

1. Asegúrese de que el Windows Forms de datos tiene el foco activo y que la **ventana Orígenes** de datos está abierta y anclada.

1. Expanda el nodo **Customers** en la ventana **Orígenes de datos**.

1. Arrastre el nodo **Customers** desde la ventana **Orígenes de datos** hasta el formulario.

     En el formulario aparecen un control <xref:System.Windows.Forms.DataGridView> y una barra de herramientas (<xref:System.Windows.Forms.BindingNavigator>) para navegar por los registros. En la bandeja de componentes aparecen [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md), CustomersTableAdapter, <xref:System.Windows.Forms.BindingSource> y <xref:System.Windows.Forms.BindingNavigator>.

## <a name="add-parameterization-search-functionality-to-the-query"></a>Agregar parametrización (funcionalidad de búsqueda) a la consulta

Puede agregar una cláusula WHERE a la consulta original mediante el cuadro de diálogo **Generador de criterios de** búsqueda:

1. Justo debajo de la superficie de diseño del formulario, seleccione el botón **customersTableAdapter** y, a continuación, en la ventana **Propiedades,** **elija Agregar consulta...**.

2. Escriba **FillByCity en el** área Nuevo nombre de **consulta** en el cuadro de diálogo Generador **de criterios** de búsqueda.

3. Agregue `WHERE City = @City` a la consulta en el área **Texto de la consulta**.

     La consulta debe ser similar a lo siguiente:

     ```sql
     SELECT CustomerID, CompanyName, ContactName, ContactTitle,
          Address, City, Region, PostalCode, Country, Phone, Fax
     FROM Customers
     WHERE City = @City
     ```

    > [!NOTE]
    > Los orígenes OLE DB datos de acceso y de acceso usan el signo de interrogación ('?') para indicar parámetros, por lo que la cláusula WHERE tendría el siguiente aspecto: `WHERE City = ?` .

4. Haga clic en **Aceptar** para cerrar el cuadro de diálogo **Generador de criterios de búsqueda**.

     **FillByCityToolStrip** se agrega al formulario.

## <a name="test-the-application"></a>Prueba de la aplicación

Al ejecutar la aplicación, se abre el formulario y se prepara para tomar el parámetro como entrada:

1. Presione **F5** para ejecutar la aplicación.

2. Escriba **Londres** en el cuadro de texto **Ciudad** y haga clic en **FillByCity**.

     La cuadrícula de datos se rellena con clientes que cumplen los criterios. En este ejemplo, la cuadrícula de datos muestra sólo los clientes que tienen un valor de **Londres** en su columna **Ciudad**.

## <a name="next-steps"></a>Pasos siguientes

Dependiendo de los requisitos de la aplicación, existen varios pasos que se pueden realizar después de crear un formulario parametrizado. Entre las mejoras que podría realizar se incluyen:

- Agregar controles que muestran datos relacionados. Para obtener más información, vea [Relaciones en conjuntos de datos.](relationships-in-datasets.md)

- Modificar el conjunto de datos agregando o quitando objetos de la base de datos. Para obtener más información, vea [Crear y configurar conjuntos de datos](../data-tools/create-and-configure-datasets-in-visual-studio.md).

## <a name="see-also"></a>Vea también

- [Enlazar controles de Windows Forms a datos en Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)
