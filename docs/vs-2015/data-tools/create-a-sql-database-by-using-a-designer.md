---
title: Crear una base de datos SQL mediante un diseñador | Microsoft Docs
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
- SQL Server Express
- local data
- LocalDB
- SQLEXPRESS
- data [Visual Studio], Local data
- SQL Express
- data [Visual Studio], walkthroughs
- databases, creating
- database files, creating
ms.assetid: 99c2b06f-47aa-414e-8057-a3453712fd23
caps.latest.revision: 54
author: jillre
ms.author: jillfra
manager: jillfra
robots: noindex,nofollow
ms.openlocfilehash: 33b97050f04fd23a9fa3b6c3c641faa5dfe4802f
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72651058"
---
# <a name="create-a-sql-database-by-using-a-designer"></a>Creación de una base de datos SQL mediante un diseñador
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Puede explorar tareas básicas, como agregar tablas y definir columnas, utilizando Visual Studio para crear y actualizar un archivo de base de datos local en SQL Server Express LocalDB. Después de finalizar este tutorial, puede explorar las funciones más avanzadas usando la base de datos local como punto de partida para otros tutoriales que la necesiten.

 También puede crear una base de datos mediante SQL Server Management Studio (una descarga independiente) o instrucciones Transact-SQL en la ventana de herramientas de **Explorador de objetos de SQL Server** en Visual Studio.

 Durante este tutorial explorará las tareas siguientes:

- [Crear un proyecto y un archivo de base de datos local](../data-tools/create-a-sql-database-by-using-a-designer.md#BKMK_CreateNewSQLDB)

- [Crear tablas, columnas, claves principales y claves externas](../data-tools/create-a-sql-database-by-using-a-designer.md#BKMK_CreateNewTbls)

- [Rellenar las tablas con datos](../data-tools/create-a-sql-database-by-using-a-designer.md#BKMK_Populating)

## <a name="prerequisites"></a>Requisitos previos
 Para completar este tutorial, asegúrese de que ha instalado SQL Server Data Tools. En el menú **Ver** , debería ver **Explorador de objetos de SQL Server**. Si no está allí, vaya a **Agregar o quitar programas**, haga clic **en Visual Studio 2015**, seleccione **cambiar**y active la casilla situada junto a **SQL Server Data Tools**.

## <a name="BKMK_CreateNewSQLDB"></a>Crear un proyecto y un archivo de base de datos local

#### <a name="to-create-a-project-and-a-database-file"></a>Para crear un proyecto y un archivo de base de datos

1. Cree un proyecto de Windows Forms denominado `SampleDatabaseWalkthrough`.

2. En la barra de menús, seleccione **proyecto**  > **Agregar nuevo elemento**.

3. En la lista de plantillas de elementos, desplácese hacia abajo y seleccione **base de datos basada en servicio**.

    ![Cuadro de diálogo plantillas de elementos](../data-tools/media/raddata-vsitemtemplates.png "raddata VSItemTemplates")

4. Asigne un nombre a la base de datos **SampleDatabase**y seleccione el botón **Agregar** .

5. Si la **ventana orígenes de datos** no está abierta, ábrala seleccionando las teclas Mayús + Alt + D o, en la barra de menús, seleccionando **Ver**  > **otras ventanas**  > **orígenes de datos**.

6. En la ventana **orígenes de datos** , seleccione el vínculo **Agregar nuevo origen de datos** .

7. En el **Asistente**para la configuración de orígenes de datos, seleccione el botón **siguiente** cuatro veces para aceptar la configuración predeterminada y, a continuación, seleccione el botón **Finalizar** .

   Abra la ventana de propiedades de la base de datos para ver la cadena de conexión y la ubicación del archivo .mdf principal. Verá que el archivo de base de datos se encuentra en la carpeta del proyecto.

- En Visual Studio, seleccione **ver**  > **Explorador de objetos de SQL Server** si la ventana no está abierta todavía. Abra la ventana Propiedades. para ello, expanda el nodo **conexiones de datos** , abra el menú contextual de SampleDatabase. MDF y, a continuación, seleccione **propiedades**.

- Como alternativa, puede seleccionar **ver**  > **Explorador de servidores**, si la ventana no está abierta todavía. Expanda el nodo **conexiones de datos** para abrir la ventana Propiedades. Abra el menú contextual de SampleDatabase. MDF y, a continuación, seleccione **propiedades**.

## <a name="BKMK_CreateNewTbls"></a>Crear tablas, columnas, claves principales y claves externas
 En esta sección, creará un par de tablas, una clave principal en cada tabla y algunas filas de datos de ejemplo. En el siguiente tutorial, obtendrá una idea de cómo puede aparecer esa información en una aplicación. También creará una clave externa para especificar cuántos registros de una tabla pueden corresponder a registros de la otra tabla.

#### <a name="to-create-the-customers-table"></a>Para crear la tabla Customers

1. En **Explorador de servidores** o **Explorador de objetos de SQL Server**, expanda el nodo **conexiones de datos** y, a continuación, expanda el nodo **SampleDatabase. MDF** .

2. Abra el menú contextual para **tablas**y, a continuación, seleccione **Agregar nueva tabla**.

     El **Diseñador de tablas** se abre y muestra una cuadrícula con una fila predeterminada que representa una columna única de la tabla que está creando. Al agregar filas a la cuadrícula, agregará columnas en la tabla.

3. En la cuadrícula, agregue una fila para cada una de las entradas siguientes:

    |Nombre de columna|Tipo de datos|Permitir valores NULL|
    |-----------------|---------------|-----------------|
    |`CustomerID`|`nchar(5)`|False (desactivada)|
    |`CompanyName`|`nvarchar(50)`|False (desactivada)|
    |`ContactName`|`nvarchar (50)`|True (seleccionada)|
    |`Phone`|`nvarchar (24)`|True (seleccionada)|

4. Abra el menú contextual de la fila de `CustomerID` y, a continuación, seleccione **establecer clave principal**.

5. Abra el menú contextual de la fila predeterminada y, a continuación, seleccione **eliminar**.

6. Asigne un nombre a la tabla Customers actualizando la primera línea del panel de script para que coincida con el ejemplo siguiente:

    ```
    CREATE TABLE [dbo].[Customers]
    ```

     Verá algo parecido a esto:

     ![Diseñador de tablas](../data-tools/media/raddata-table-designer.png "Diseñador de tablas raddata")

7. En la esquina superior izquierda del **Diseñador de tablas**, seleccione el botón **Actualizar** .

8. En el cuadro de diálogo **vista previa de actualizaciones de base de datos** , seleccione el botón **Actualizar base de datos** .

     Los cambios realizados se guardarán en el archivo de base de datos local.

#### <a name="to-create-the-orders-table"></a>Para crear la tabla Orders

1. Agregue otra tabla y, después, agregue una fila para cada entrada de la tabla siguiente:

    |Nombre de columna|Tipo de datos|Permitir valores NULL|
    |-----------------|---------------|-----------------|
    |`OrderID`|`int`|False (desactivada)|
    |`CustomerID`|`nchar(5)`|False (desactivada)|
    |`OrderDate`|`datetime`|True (seleccionada)|
    |`OrderQuantity`|`int`|True (seleccionada)|

2. Establezca **OrderID** como la clave principal y, a continuación, elimine la fila predeterminada.

3. Asigne un nombre a la tabla Orders actualizando la primera línea del panel de script para que coincida con el ejemplo siguiente:

    ```
    CREATE TABLE [dbo].[Orders]
    ```

4. En la esquina superior izquierda del **Diseñador de tablas**, seleccione el botón **Actualizar** .

5. En el cuadro de diálogo **vista previa de actualizaciones de base de datos** , seleccione el botón **Actualizar base de datos** .

     Los cambios realizados se guardarán en el archivo de base de datos local.

#### <a name="to-create-a-foreign-key"></a>Para crear una clave externa

1. En el panel de contexto de la derecha de la cuadrícula, abra el menú contextual de **claves externas**y, a continuación, seleccione **Agregar nueva clave externa**, como se muestra en la siguiente ilustración.

     ![Agregar una clave externa en Diseñador de tablas](../data-tools/media/foreignkey.png "ForeignKey")

2. En el cuadro de texto que aparece, reemplace **ToTable** por `Customers`.

3. En el panel T-SQL, actualice la última línea para que coincida con el ejemplo siguiente:

    ```
    CONSTRAINT [FK_Orders_Customers] FOREIGN KEY ([CustomerID]) REFERENCES [Customers]([CustomerID])
    ```

4. En la esquina superior izquierda del **Diseñador de tablas**, seleccione el botón **Actualizar** .

5. En el cuadro de diálogo **vista previa de actualizaciones de base de datos** , seleccione el botón **Actualizar base de datos** .

     Los cambios realizados se guardarán en el archivo de base de datos local.

## <a name="BKMK_Populating"></a>Rellenar las tablas con datos

#### <a name="to-populate-the-tables-with-data"></a>Para rellenar las tablas con datos

1. En **Explorador de servidores** o **Explorador de objetos de SQL Server**, expanda el nodo de la base de datos de ejemplo.

2. Abra el menú contextual del nodo **tablas** , seleccione **Actualizar**y, a continuación, expanda el nodo **tablas** .

3. Abra el menú contextual para la tabla Customers y, a continuación, seleccione **Mostrar datos de tabla**.

4. Agregue los datos que desee de al menos tres clientes.

     Puede especificar los cinco caracteres que desee como identificadores de cliente, pero elija al menos uno que pueda recordar para usarlo posteriormente en este procedimiento.

5. Abra el menú contextual de la tabla Orders y, a continuación, seleccione **Mostrar datos de tabla**.

6. Agregue datos para al menos tres pedidos.

    > [!IMPORTANT]
    > Asegúrese de que todos los identificadores y cantidades de pedidos sean números enteros y que cada identificador de cliente coincida con el valor que especificó en la columna de la tabla Customers.

7. En la barra de menús, seleccione **archivo**  > **guardar todo**.

8. En la barra de menús, seleccione **archivo**  > **cerrar solución**.

    > [!NOTE]
    > Como procedimiento recomendado, puede hacer una copia de seguridad del archivo de base de datos que acaba de crear, copiándolo y luego pegando la copia en otra ubicación o dando a la copia un nombre diferente.

## <a name="next-steps"></a>Pasos siguientes
 Ahora que tiene un archivo de base de datos local con algunos datos de ejemplo, puede completar cualquiera de los tutoriales que muestran las tareas de base de datos.
