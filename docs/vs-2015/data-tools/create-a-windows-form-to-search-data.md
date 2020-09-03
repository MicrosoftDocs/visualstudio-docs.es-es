---
title: Crear un formulario de Windows Forms para buscar datos | Microsoft Docs
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
- Windows Forms, searching data
- Windows Forms, displaying data
- parameters, displaying filtered data
- data [Visual Studio], parameterizing queries
- data [Visual Studio], searching
ms.assetid: 65ca79a9-7458-466c-af55-978cd24c549e
caps.latest.revision: 31
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 81980f38cbd8fb595530cc52b2cf32056feb43a7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "72670055"
---
# <a name="create-a-windows-form-to-search-data"></a>Crear Windows Forms para buscar en datos
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Un escenario habitual de la aplicación es mostrar los datos seleccionados en un formulario. Por ejemplo, puede que desee mostrar los pedidos de un cliente concreto o los detalles de un pedido específico. En este caso, un usuario escribe información en un formulario y, a continuación, se ejecuta una consulta con la entrada del usuario como parámetro; es decir, los datos se seleccionan basándose en una consulta parametrizada. La consulta devuelve sólo los datos que satisfacen los criterios escritos por el usuario. Este tutorial muestra cómo crear una consulta que devuelve los clientes de una ciudad específica y cómo modificar la interfaz de usuario para que los usuarios puedan escribir el nombre de una ciudad y presionar un botón para ejecutar la consulta.

 El uso de consultas parametrizadas ayuda a que la aplicación sea más eficaz, ya que permite a la base de datos realizar el trabajo que mejor sabe hacer: filtrar registros rápidamente. Al contrario, si solicita una tabla de base de datos completa, la transfiere por la red y, a continuación, utiliza la lógica de la aplicación para buscar los registros pertinentes, la aplicación puede tornarse más lenta y difícil de utilizar.

 Puede Agregar consultas con parámetros a cualquier TableAdapter (y controles para aceptar valores de parámetro y ejecutar la consulta) mediante el cuadro de diálogo **generador de criterios de búsqueda** . Abra el cuadro de diálogo seleccionando el comando **Agregar consulta** del menú **Datos** (o en cualquier etiqueta inteligente del TableAdapter).

 Las tareas ilustradas en este tutorial incluyen:

- Crear un proyecto nuevo de aplicación Windows Forms.

- Crear y configurar el origen de datos en la aplicación con el Asistente para la **configuración de orígenes de datos** .

- Establecer el tipo de colocación de los elementos en la ventana **orígenes de datos** .

- Crear controles que muestran datos arrastrando elementos desde la ventana **Orígenes de datos** hasta un formulario.

- Agregar controles para mostrar los datos en el formulario.

- Completando el cuadro de diálogo **generador de criterios de búsqueda** .

- Escribir parámetros en el formulario y ejecutar la consulta con parámetros.

## <a name="prerequisites"></a>Prerrequisitos
 Para completar las tareas de este tutorial, necesitará:

- Acceso a la base de datos de ejemplo Northwind.

## <a name="create-the-windows-application"></a>Crear la aplicación para Windows
 El primer paso es crear una **aplicación para Windows**. En este paso, la asignación de un nombre al proyecto es opcional, pero le asignará un nombre, ya que lo guardará más adelante.

#### <a name="to-create-the-new-windows-application-project"></a>Para crear el nuevo proyecto de aplicación para Windows

1. En el menú **archivo** , cree un nuevo proyecto.

2. Dé un nombre al proyecto `WindowsSearchForm`.

3. Seleccione **aplicación para Windows** y haga clic en **Aceptar**.

     El proyecto **WindowsSearchForm** se crea y se agrega al **Explorador de soluciones**.

## <a name="create-the-data-source"></a>Crear el origen de datos
 Este paso crea un origen de datos a partir de una base de datos mediante el Asistente para la **configuración de orígenes de datos** . Debe tener acceso a la base de datos de ejemplo Northwind para crear la conexión. Para obtener información sobre cómo configurar la base de datos de ejemplo Northwind, vea [instalar SQL Server bases](../data-tools/install-sql-server-sample-databases.md)de datos de ejemplo.

#### <a name="to-create-the-data-source"></a>Para crear el origen de datos

1. En el menú **Datos** , haga clic en **Mostrar orígenes de datos**.

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
 Puede crear los controles enlazados a datos arrastrando elementos desde la ventana **orígenes de datos** hasta el formulario.

#### <a name="to-create-data-bound-controls-on-the-form"></a>Para crear controles enlazados en el formulario

1. Expanda el nodo **Customers** en la ventana **Orígenes de datos**.

2. Arrastre el nodo **Customers** desde la ventana **Orígenes de datos** hasta el formulario.

     En el formulario aparecen un control <xref:System.Windows.Forms.DataGridView> y una barra de herramientas (<xref:System.Windows.Forms.BindingNavigator>) para navegar por los registros. En la bandeja de componentes aparecen [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md), CustomersTableAdapter, <xref:System.Windows.Forms.BindingSource> y <xref:System.Windows.Forms.BindingNavigator>.

## <a name="addparameterization-search-functionality-to-the-query"></a>Addparameterization (funcionalidad de búsqueda) a la consulta
 Puede Agregar una cláusula WHERE a la consulta original mediante el cuadro de diálogo **generador de criterios de búsqueda** .

#### <a name="to-create-a-parameterized-query-and-controls-to-enter-the-parameters"></a>Para crear una consulta parametrizada y controles para escribir los parámetros

1. Seleccione el control <xref:System.Windows.Forms.DataGridView> y, a continuación, elija **Agregar consulta** en el menú **Datos**.

2. Escriba `FillByCity` en el área **nuevo nombre de consulta** en el cuadro de diálogo **generador de criterios de búsqueda** .

3. Agregue `WHERE City = @City` a la consulta en el área **Texto de la consulta**.

     La consulta debe ser similar a lo siguiente:

     `SELECT CustomerID, CompanyName, ContactName, ContactTitle, Address, City, Region, PostalCode, Country, Phone, Fax`

     `FROM Customers`

     `WHERE City = @City`

    > [!NOTE]
    > Los orígenes de datos de acceso y OLE DB utilizan el signo de interrogación ('? ') para denotar los parámetros, por lo que la cláusula WHERE tendría el siguiente aspecto: `WHERE City = ?` .

4. Haga clic en **Aceptar** para cerrar el cuadro de diálogo **Generador de criterios de búsqueda**.

     **FillByCityToolStrip** se agrega al formulario.

## <a name="testing-the-application"></a>Probar la aplicación
 Al ejecutar la aplicación, se abre el formulario listo para tomar el parámetro como entrada.

#### <a name="to-test-the-application"></a>Para probar la aplicación

1. Presione F5 para ejecutar la aplicación.

2. Escriba **Londres** en el cuadro de texto **Ciudad** y haga clic en **FillByCity**.

     La cuadrícula de datos se rellena con los clientes que cumplen los criterios. En este ejemplo, la cuadrícula de datos muestra sólo los clientes que tienen un valor de **Londres** en su columna **Ciudad**.

## <a name="next-steps"></a>Pasos siguientes
 Dependiendo de los requisitos de la aplicación, existen varios pasos que se pueden realizar después de crear un formulario parametrizado. Entre las mejoras que podría realizar se incluyen:

- Agregar controles que muestran datos relacionados.

- Modificar el conjunto de datos agregando o quitando objetos de la base de datos. Para obtener más información, vea [Crear y configurar conjuntos de datos](../data-tools/create-and-configure-datasets-in-visual-studio.md).

## <a name="see-also"></a>Consulte también
 [Enlazar controles de Windows Forms a datos en Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)
