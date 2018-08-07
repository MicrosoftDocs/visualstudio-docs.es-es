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
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 7b2a72306a3636bb5bca601f600afdaa175b4dd1
ms.sourcegitcommit: 3a11feebad45a0dd4ac45efcbfdf172fce46e1de
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/07/2018
ms.locfileid: "39582426"
---
# <a name="create-a-windows-form-to-search-data"></a>Crear Windows Forms para buscar en datos

Un escenario habitual de la aplicación es mostrar los datos seleccionados en un formulario. Por ejemplo, puede que desee mostrar los pedidos de un cliente concreto o los detalles de un pedido específico. En este caso, un usuario escribe información en un formulario y, a continuación, se ejecuta una consulta con la entrada del usuario como parámetro; es decir, los datos se seleccionan basándose en una consulta parametrizada. La consulta devuelve sólo los datos que satisfacen los criterios escritos por el usuario. Este tutorial muestra cómo crear una consulta que devuelve los clientes de una ciudad específica y cómo modificar la interfaz de usuario para que los usuarios puedan escribir el nombre de una ciudad y presionar un botón para ejecutar la consulta.

El uso de consultas parametrizadas ayuda a que la aplicación sea más eficaz, ya que permite a la base de datos realizar el trabajo que mejor sabe hacer: filtrar registros rápidamente. En cambio, si solicita una tabla de base de datos completa, transferirla a través de la red y, a continuación, usar lógica de aplicación para buscar los registros que desea, la aplicación puede ser ineficaz y lento.

Puede agregar consultas parametrizadas a cualquier TableAdapter (y controles para aceptar los valores de parámetro y ejecutar la consulta), mediante el **generador de criterios de búsqueda** cuadro de diálogo. Abra el cuadro de diálogo seleccionando el **Agregar consulta** comando el **datos** menú (o en cualquier etiqueta inteligente del TableAdapter).

Las tareas ilustradas en este tutorial incluyen:

-   Crear un nuevo **aplicación de Windows Forms** proyecto.

-   Crear y configurar el origen de datos en la aplicación con el **configuración origen de datos** asistente.

-   Establecer el tipo de colocación de los elementos de la **orígenes de datos** ventana.

-   Crear controles que muestran datos arrastrando elementos desde la **orígenes de datos** ventana en un formulario.

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

     El **WindowsSearchForm** se crea y se agrega al proyecto **el Explorador de soluciones**.

## <a name="create-the-data-source"></a>Crear el origen de datos

Este paso crea un origen de datos de una base de datos utilizando el **configuración origen de datos** asistente:

1.  En el menú **Datos** , haga clic en **Mostrar orígenes de datos**.

2.  En el **orígenes de datos** ventana, seleccione **Agregar nuevo origen de datos** para iniciar el **configuración origen de datos** asistente.

3.  Seleccione **Base de datos** en la página **Elegir un tipo de datos de origen** y luego haga clic en **Siguiente**.

4.  En el **elegir la conexión de datos** realice página uno de los siguientes:

    -   Si una conexión de datos a la base de datos de ejemplo Northwind está disponible en la lista desplegable, selecciónela.

    -   Seleccione **nueva conexión** para iniciar el **agregar o modificar conexión** cuadro de diálogo.

5.  Si la base de datos requiere una contraseña, seleccione la opción para incluir datos confidenciales y, a continuación, haga clic en **siguiente**.

6.  En el **Guardar cadena de conexión en el archivo de configuración de la aplicación** página, haga clic en **siguiente**.

7.  En el **elija los objetos de base de datos** , expanda el **tablas** nodo.

8.  Seleccione el **clientes** de tabla y, a continuación, haga clic en **finalizar**.

     El **NorthwindDataSet** se agrega al proyecto y el **clientes** tabla aparece en el **orígenes de datos** ventana.

## <a name="create-the-form"></a>Crear el formulario

Puede crear los controles enlazados a datos arrastrando elementos desde la **orígenes de datos** ventana hasta el formulario:

1.  Expanda el **clientes** nodo en el **orígenes de datos** ventana.

2.  Arrastre el **clientes** nodo desde el **orígenes de datos** ventana al formulario.

     En el formulario aparecen un control <xref:System.Windows.Forms.DataGridView> y una barra de herramientas (<xref:System.Windows.Forms.BindingNavigator>) para navegar por los registros. Un [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md), CustomersTableAdapter, <xref:System.Windows.Forms.BindingSource>, y <xref:System.Windows.Forms.BindingNavigator> aparecen en la Bandeja de componentes.

## <a name="add-parameterization-search-functionality-to-the-query"></a>Agregar parametrización (funcionalidad de búsqueda) a la consulta

Puede agregar una cláusula WHERE a la consulta original utilizando el **generador de criterios de búsqueda** cuadro de diálogo:

1.  Seleccione el <xref:System.Windows.Forms.DataGridView> controlar y, a continuación, elija **Agregar consulta** en el **datos** menú.

2.  Tipo **FillByCity** en el **nuevo nombre de consulta** área en la **generador de criterios de búsqueda** cuadro de diálogo.

3.  Agregar `WHERE City = @City` a la consulta en el **texto de la consulta** área.

     La consulta debe ser similar a lo siguiente:

     ```sql
     SELECT CustomerID, CompanyName, ContactName, ContactTitle,
          Address, City, Region, PostalCode, Country, Phone, Fax
     FROM Customers
     WHERE City = @City
     ```

    > [!NOTE]
    > Orígenes de datos de Access y OLE DB utilizan el signo de interrogación ("?") para denotar los parámetros, por lo que la cláusula WHERE tendría un aspecto similar al siguiente: `WHERE City = ?`.

4.  Haga clic en **Aceptar** para cerrar el **generador de criterios de búsqueda** cuadro de diálogo.

     Un **FillByCityToolStrip** se agrega al formulario.

## <a name="test-the-application"></a>Probar la aplicación

Ejecutar la aplicación abre el formulario y prepara tomar el parámetro como entrada:

1.  Presione **F5** para ejecutar la aplicación.

2.  Tipo **London** en el **Ciudad** cuadro de texto y, a continuación, haga clic en **FillByCity**.

     La cuadrícula de datos se rellena con los clientes que cumplen los criterios. En este ejemplo, la cuadrícula de datos muestra sólo los clientes que tienen un valor de **London** en sus **Ciudad** columna.

## <a name="next-steps"></a>Pasos siguientes

Dependiendo de los requisitos de la aplicación, existen varios pasos que se pueden realizar después de crear un formulario parametrizado. Entre las mejoras que podría realizar se incluyen:

-   Agregar controles que muestran datos relacionados. Para obtener más información, consulte [relaciones en conjuntos de datos](relationships-in-datasets.md).

-   Modificar el conjunto de datos agregando o quitando objetos de la base de datos. Para obtener más información, vea [Crear y configurar conjuntos de datos](../data-tools/create-and-configure-datasets-in-visual-studio.md).

## <a name="see-also"></a>Vea también

- [Enlazar controles de Windows Forms a datos en Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)