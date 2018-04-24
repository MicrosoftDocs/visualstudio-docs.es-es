---
title: Cree un archivo de base de datos y usar el Diseñador de tablas en Visual Studio
ms.date: 11/03/2017
ms.topic: conceptual
helpviewer_keywords:
- database tables, creating
- database files, creating
- table designer
ms.assetid: 99c2b06f-47aa-414e-8057-a3453712fd23
author: gewarren
ms.author: gewarren
manager: douge
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 305374cbce519a87f1d40e09efac7f490b28fe0d
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/19/2018
---
# <a name="create-a-database-and-add-tables-in-visual-studio"></a>Crear una base de datos y agregar las tablas en Visual Studio
Puede usar Visual Studio para crear y actualizar un archivo de base de datos local de SQL Server Express LocalDB. También puede crear una base de datos mediante la ejecución de instrucciones de Transact-SQL en el **Explorador de objetos de SQL Server** ventana de herramientas en Visual Studio. En este tema, se creará un archivo .mdf y agregar tablas y claves mediante el Diseñador de tablas.

## <a name="prerequisites"></a>Requisitos previos
Para completar este tutorial, debe tener opcional **almacenamiento de datos y el procesamiento** cargas de trabajo instalado en Visual Studio. Para instalarlo, abra **instalador de Visual Studio** y elija la **las cargas de trabajo** ficha. En **Web & nube**, elija **almacenamiento de datos y el procesamiento**. Elija la **modificar** botón para agregar la carga de trabajo para Visual Studio.

## <a name="create-a-project-and-a-local-database-file"></a>Crear un proyecto y un archivo de base de datos local

### <a name="to-create-a-project-and-a-database-file"></a>Para crear un proyecto y un archivo de base de datos
1.  Crear un proyecto de formularios Windows Forms que se denomina `SampleDatabaseWalkthrough`.

2.  En la barra de menús, seleccione **proyecto**, **Agregar nuevo elemento**.

3.  En la lista de plantillas de elementos, desplácese hacia abajo y seleccione **base de datos basada en servicio**.

     ![Cuadro de diálogo de plantillas de elemento](../data-tools/media/raddata-vsitemtemplates.png "raddata VSItemTemplates")

4.  Nombre de la base de datos **SampleDatabase**y, a continuación, seleccione la **agregar** botón.

### <a name="to-add-a-data-source"></a>Para agregar un origen de datos
5.  Si el **orígenes de datos** ventana no está abierta, ábrala, seleccione la **Mayús + Alt + D** claves o, en la barra de menús, seleccione **vista**, **otras ventanas**, **Orígenes de datos**.

6.  En el **orígenes de datos** ventana, seleccione la **Agregar nuevo origen de datos** vínculo.

    El **Asistente para configuración de orígenes de datos** se abre.

7. En el **elegir un tipo de origen de datos** página, elija **base de datos** y, a continuación, elija **siguiente**.

8. En el **elegir un modelo de base de datos** página, elija **siguiente** para aceptar el valor predeterminado (conjunto de datos).

9. En el **elegir la conexión de datos** página, seleccione la **SampleDatabase.mdf** un archivo en la lista desplegable y, a continuación, elija **siguiente**.

10. En el **Guardar cadena de conexión en el archivo de configuración de aplicación** página, elija **siguiente**.

11. Una el **elija los objetos de base de datos** página, verá un mensaje que indica la base de datos no contiene ningún objeto. Elija **Finalizar**.

### <a name="to-view-properties-of-the-data-connection"></a>Para ver las propiedades de la conexión de datos
Puede ver la cadena de conexión para el archivo SampleDatabase.mdf abriendo la ventana Propiedades de la conexión de datos:

-   En Visual Studio, seleccione **vista**, **Explorador de objetos de SQL Server** si esa ventana no está abierta. Abrir la ventana Propiedades, expanda el **las conexiones de datos** nodo, abra el menú contextual de SampleDatabase.mdf y, a continuación, seleccione **propiedades**.

-   Como alternativa, puede seleccionar **vista**, **Explorador de servidores**, si esa ventana no está abierta. Abrir la ventana Propiedades, expanda el **las conexiones de datos** nodo. Abra el menú contextual de SampleDatabase.mdf y, a continuación, seleccione **propiedades**.

## <a name="create-tables-and-keys-by-using-table-designer"></a>Crear tablas y claves mediante el Diseñador de tablas
En esta sección, creará dos tablas, una clave principal en cada tabla y algunas filas de datos de ejemplo. También podrá crear una clave externa para especificar cómo se corresponden los registros de una tabla en los registros de la otra tabla.

### <a name="to-create-the-customers-table"></a>Para crear la tabla Customers
1.  En **Explorador de servidores** o **Explorador de objetos de SQL Server**, expanda la **las conexiones de datos** nodo y, a continuación, expanda el **SampleDatabase.mdf**nodo.

2.  Abra el menú contextual para **tablas**y, a continuación, seleccione **agregar nueva tabla**.

     El **Diseñador de tablas** se abre y muestra una cuadrícula con una fila predeterminada, que representa una sola columna de la tabla que va a crear. Al agregar filas a la cuadrícula, agregará columnas en la tabla.

3.  En la cuadrícula, agregue una fila para cada una de las entradas siguientes:

    |Nombre de columna|Tipo de datos|Permitir valores NULL|
    |-----------------|---------------|-----------------|
    |`CustomerID`|`nchar(5)`|False (desactivada)|
    |`CompanyName`|`nvarchar(50)`|False (desactivada)|
    |`ContactName`|`nvarchar (50)`|True (seleccionada)|
    |`Phone`|`nvarchar (24)`|True (seleccionada)|

4.  Abra el menú contextual para el `CustomerID` fila y, a continuación, seleccione **establecer clave principal**.

5.  Abra el menú contextual para la fila predeterminada y, a continuación, seleccione **eliminar**.

6.  Asigne un nombre a la tabla Customers actualizando la primera línea del panel de script para que coincida con el ejemplo siguiente:

    ```
    CREATE TABLE [dbo].[Customers]
    ```

    Verá algo parecido a esto:

    ![Diseñador de tablas](../data-tools/media/raddata-table-designer.png "raddata Diseñador de tablas")

7.  En la esquina superior izquierda de la **Diseñador de tablas**, seleccione la **actualización** botón.

8.  En el **actualizaciones de base de datos de vista previa** cuadro de diálogo, seleccione la **Actualizar base de datos** botón.

    Los cambios realizados se guardarán en el archivo de base de datos local.

### <a name="to-create-the-orders-table"></a>Para crear la tabla Orders
1.  Agregue otra tabla y, después, agregue una fila para cada entrada de la tabla siguiente:

    |Nombre de columna|Tipo de datos|Permitir valores NULL|
    |-----------------|---------------|-----------------|
    |`OrderID`|`int`|False (desactivada)|
    |`CustomerID`|`nchar(5)`|False (desactivada)|
    |`OrderDate`|`datetime`|True (seleccionada)|
    |`OrderQuantity`|`int`|True (seleccionada)|

2.  Establecer **OrderID** como clave principal y, a continuación, elimine la fila predeterminada.

3.  Asigne un nombre a la tabla Orders actualizando la primera línea del panel de script para que coincida con el ejemplo siguiente:

    ```sql
    CREATE TABLE [dbo].[Orders]
    ```

4.  En la esquina superior izquierda de la **Diseñador de tablas**, seleccione la **actualización** botón.

5.  En el **actualizaciones de base de datos de vista previa** cuadro de diálogo, seleccione la **Actualizar base de datos** botón.

    Los cambios realizados se guardarán en el archivo de base de datos local.

### <a name="to-create-a-foreign-key"></a>Para crear una clave externa
1.  En el panel de contexto en el lado derecho de la cuadrícula, abra el menú contextual de **claves externas**y, a continuación, seleccione **agregar nueva clave externa**, como se muestra en la siguiente ilustración.

     ![Agregar una clave externa en el Diseñador de tablas](../data-tools/media/foreignkey.png "ForeignKey")

2.  En el cuadro de texto que aparece, reemplace **ToTable** con `Customers`.

3.  En el panel de T-SQL, actualice la última línea para que coincida con el ejemplo siguiente:

    ```sql
    CONSTRAINT [FK_Orders_Customers] FOREIGN KEY ([CustomerID]) REFERENCES [Customers]([CustomerID])
    ```

4.  En la esquina superior izquierda de la **Diseñador de tablas**, seleccione la **actualización** botón.

5.  En el **actualizaciones de base de datos de vista previa** cuadro de diálogo, seleccione la **Actualizar base de datos** botón.

    Los cambios realizados se guardarán en el archivo de base de datos local.

## <a name="populate-the-tables-with-data"></a>Rellenar las tablas con datos

### <a name="to-populate-the-tables-with-data"></a>Para rellenar las tablas con datos

1.  En **Explorador de servidores** o **Explorador de objetos de SQL Server**, expanda el nodo de la base de datos de ejemplo.

2.  Abra el menú contextual para el **tablas** nodo, seleccione **actualizar**y, a continuación, expanda el **tablas** nodo.

3.  Abra el menú contextual para la tabla Customers y, a continuación, seleccione **mostrar datos de tabla**.

4.  Agregue los datos que desee para algunos clientes.

    Puede especificar los cinco caracteres que desee como identificadores de cliente, pero elija al menos uno que pueda recordar para usarlo posteriormente en este procedimiento.

5.  Abra el menú contextual de la tabla Orders y, a continuación, seleccione **mostrar datos de tabla**.

6.  Agregar datos para algunos pedidos.

    > [!IMPORTANT]
    > Asegúrese de que todos los identificadores y cantidades de pedido son enteros y que cada identificador de cliente coincide con un valor que especificó en la columna CustomerID de la tabla Customers.

7.  En la barra de menús, seleccione **archivo**, **guardar todo**.

## <a name="see-also"></a>Vea también

- [Obtener acceso a los datos en Visual Studio](accessing-data-in-visual-studio.md)