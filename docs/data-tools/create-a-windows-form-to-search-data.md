---
title: Crear Windows Forms para buscar en datos
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Windows Forms, searching data
- Windows Forms, displaying data
- parameters, displaying filtered data
- data [Visual Studio], parameterizing queries
- data [Visual Studio], searching
ms.assetid: 65ca79a9-7458-466c-af55-978cd24c549e
author: gewarren
ms.author: gewarren
manager: jillfra
ms.prod: visual-studio-dev15
ms.workload:
- data-storage
ms.openlocfilehash: 1f17a69706b224598bff095374f197ee1492af55
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 01/25/2019
ms.locfileid: "55001282"
---
# <a name="create-a-windows-form-to-search-data"></a>Crear Windows Forms para buscar en datos

Un escenario habitual de la aplicación es mostrar los datos seleccionados en un formulario. Por ejemplo, puede que desee mostrar los pedidos de un cliente concreto o los detalles de un pedido específico. En este caso, un usuario escribe información en un formulario y, a continuación, se ejecuta una consulta con la entrada del usuario como parámetro; es decir, los datos se seleccionan basándose en una consulta parametrizada. La consulta devuelve sólo los datos que satisfacen los criterios escritos por el usuario. Este tutorial muestra cómo crear una consulta que devuelve los clientes de una ciudad específica y cómo modificar la interfaz de usuario para que los usuarios puedan escribir el nombre de una ciudad y presionar un botón para ejecutar la consulta.

El uso de consultas parametrizadas ayuda a que la aplicación sea más eficaz, ya que permite a la base de datos realizar el trabajo que mejor sabe hacer: filtrar registros rápidamente. Al contrario, si solicita una tabla de base de datos completa, la transfiere por la red y, a continuación, utiliza la lógica de la aplicación para buscar los registros pertinentes, la aplicación puede tornarse más lenta y difícil de utilizar.

Puede agregar consultas parametrizadas a cualquier TableAdapter (y controles para aceptar los valores de parámetro y ejecutar la consulta), mediante el **generador de criterios de búsqueda** cuadro de diálogo. Abra el cuadro de diálogo seleccionando el comando **Agregar consulta** del menú **Datos** (o en cualquier etiqueta inteligente del TableAdapter).

Las tareas ilustradas en este tutorial incluyen:

-   Crear un proyecto nuevo de **aplicación de Windows Forms**.

-   Crear y configurar el origen de datos en la aplicación con el **configuración origen de datos** asistente.

-   Establecer el tipo de colocación de los elementos de la **orígenes de datos** ventana.

-   Crear controles que muestran datos arrastrando elementos desde la ventana **Orígenes de datos** hasta un formulario.

-   Agregar controles para mostrar los datos en el formulario.

-   Completar la **generador de criterios de búsqueda** cuadro de diálogo.

-   Escribir parámetros en el formulario y ejecutar la consulta con parámetros.

## <a name="prerequisites"></a>Requisitos previos

En este tutorial usa SQL Server Express LocalDB y la base de datos de ejemplo Northwind.

1.  Si no tiene SQL Server Express LocalDB, instálelo de desde el [página de descarga de SQL Server Express](https://www.microsoft.com/sql-server/sql-server-editions-express), o a través del **instalador de Visual Studio**. En el **instalador de Visual Studio**, puede instalar SQL Server Express LocalDB como parte de la **procesamiento y almacenamiento de datos** carga de trabajo, o como un componente individual.

2.  Instalar la base de datos de ejemplo Northwind, siga estos pasos:

    1. En Visual Studio, abra el **Explorador de objetos de SQL Server** ventana. (Explorador de objetos de SQL Server se instala como parte de la **procesamiento y almacenamiento de datos** carga de trabajo en el **instalador de Visual Studio**.) Expanda el **SQL Server** nodo. Haga doble clic en la instancia de LocalDB y seleccione **nueva consulta**.

       Se abre una ventana del editor de consultas.

    2. Copia el [script Transact-SQL de Northwind](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true) en el Portapapeles. Este script de Transact-SQL crea la base de datos Northwind desde el principio y lo rellena con datos.

    3. Pegue el script de Transact-SQL en el editor de consultas y, a continuación, elija el **Execute** botón.

       Después de un breve tiempo, finalice la consulta y se crea la base de datos Northwind.

## <a name="create-the-windows-forms-application"></a>Crear la aplicación de Windows Forms

El primer paso es crear una aplicación de Windows Forms. Asignar un nombre al proyecto es opcional en este paso, pero daremos aquí un nombre dado que se guardará el proyecto más adelante:

1. En Visual Studio, en el **archivo** menú, seleccione **New** > **proyecto**.

2. Expanda el **Visual C#** o **Visual Basic** en el panel izquierdo, seleccione **Windows Desktop**.

3. En el panel central, seleccione la **aplicación de Windows Forms** tipo de proyecto.

4. Denomine el proyecto **WindowsSearchForm**y, a continuación, elija **Aceptar**.

     El proyecto **WindowsSearchForm** se crea y se agrega al **Explorador de soluciones**.

## <a name="create-the-data-source"></a>Crear el origen de datos

Este paso crea un origen de datos a partir de una base de datos utilizando el asistente para la **Configuración de origen de datos**:

1.  Para abrir el **orígenes de datos** ventana, en el **datos** menú, haga clic en **Mostrar orígenes de datos**.

2.  En la ventana **Orígenes de datos**, seleccione **Agregar nuevo origen de datos** para iniciar el **Asistente para configuración de orígenes de datos**.

3.  Seleccione **Base de datos** en la página **Elegir un tipo de datos de origen** y luego haga clic en **Siguiente**.

4.  En la página **Elegir la conexión de datos** realice una de las siguientes operaciones:

    -   Si una conexión de datos a la base de datos de ejemplo Northwind está disponible en la lista desplegable, selecciónela.

    -   Seleccione **Nueva conexión** para iniciar el cuadro de diálogo **Agregar o modificar conexión**.

5.  Si su base de datos requiere una contraseña, seleccione la opción para incluir datos confidenciales y haga clic en **Siguiente**.

6.  Haga clic en **Siguiente** en la página **Guardar la cadena de conexión en el archivo de configuración de la aplicación**.

7.  Expanda el nodo **Tablas** en la página **Elija los objetos de base de datos**.

8.  Seleccione la tabla **Customers** y, a continuación, haga clic en **Finalizar**.

     Se agrega al proyecto **NorthwindDataSet** y la tabla **Customers** aparece en la ventana **Orígenes de datos**.

## <a name="create-the-form"></a>Crear el formulario

Puede crear los controles enlazados a datos arrastrando elementos desde la ventana **Orígenes de datos** al formulario:

1.  Expanda el nodo **Customers** en la ventana **Orígenes de datos**.

2.  Arrastre el nodo **Customers** desde la ventana **Orígenes de datos** hasta el formulario.

     En el formulario aparecen un control <xref:System.Windows.Forms.DataGridView> y una barra de herramientas (<xref:System.Windows.Forms.BindingNavigator>) para navegar por los registros. En la bandeja de componentes aparecen [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md), CustomersTableAdapter, <xref:System.Windows.Forms.BindingSource> y <xref:System.Windows.Forms.BindingNavigator>.

## <a name="add-parameterization-search-functionality-to-the-query"></a>Agregar parametrización (funcionalidad de búsqueda) a la consulta

Puede agregar una cláusula WHERE a la consulta original utilizando el **generador de criterios de búsqueda** cuadro de diálogo:

1.  Seleccione el control <xref:System.Windows.Forms.DataGridView> y, a continuación, elija **Agregar consulta** en el menú **Datos**.

2.  Tipo **FillByCity** en el **nuevo nombre de consulta** área en la **generador de criterios de búsqueda** cuadro de diálogo.

3.  Agregue `WHERE City = @City` a la consulta en el área **Texto de la consulta**.

     La consulta debe ser similar a lo siguiente:

     ```sql
     SELECT CustomerID, CompanyName, ContactName, ContactTitle,
          Address, City, Region, PostalCode, Country, Phone, Fax
     FROM Customers
     WHERE City = @City
     ```

    > [!NOTE]
    > Orígenes de datos de Access y OLE DB utilizan el signo de interrogación ("?") para denotar los parámetros, por lo que la cláusula WHERE tendría un aspecto similar al siguiente: `WHERE City = ?`.

4.  Haga clic en **Aceptar** para cerrar el cuadro de diálogo **Generador de criterios de búsqueda**.

     **FillByCityToolStrip** se agrega al formulario.

## <a name="test-the-application"></a>Probar la aplicación

Ejecutar la aplicación abre el formulario y prepara tomar el parámetro como entrada:

1.  Presione **F5** para ejecutar la aplicación.

2.  Escriba **Londres** en el cuadro de texto **Ciudad** y haga clic en **FillByCity**.

     La cuadrícula de datos se rellena con los clientes que cumplen los criterios. En este ejemplo, la cuadrícula de datos muestra sólo los clientes que tienen un valor de **Londres** en su columna **Ciudad**.

## <a name="next-steps"></a>Pasos siguientes

Dependiendo de los requisitos de la aplicación, existen varios pasos que se pueden realizar después de crear un formulario parametrizado. Entre las mejoras que podría realizar se incluyen:

-   Agregar controles que muestran datos relacionados. Para obtener más información, consulte [relaciones en conjuntos de datos](relationships-in-datasets.md).

-   Modificar el conjunto de datos agregando o quitando objetos de la base de datos. Para obtener más información, vea [Crear y configurar conjuntos de datos](../data-tools/create-and-configure-datasets-in-visual-studio.md).

## <a name="see-also"></a>Vea también

- [Enlazar controles de Windows Forms a datos en Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)
