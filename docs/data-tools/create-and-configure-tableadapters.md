---
title: Crear y configurar los TableAdapters
ms.date: 09/01/2017
ms.topic: conceptual
helpviewer_keywords:
- table adapters, creating
- creating TableAdapters
- data [Visual Studio], creating data components
- data [Visual Studio], TableAdapters
- data [Visual Studio], creating table adapters
ms.assetid: 08630d69-0d6c-4e8f-b42d-2922f45f8415
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: c59128fe0ed0c1053c044431bbde68fb5906de31
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/26/2018
---
# <a name="create-and-configure-tableadapters"></a>Crear y configurar los TableAdapters
Los TableAdapters comunican la aplicación con una base de datos. Se conectan a la base de datos, ejecución de consultas o procedimientos almacenados, y devuelven un nuevos datos de la tabla o el relleno existente <xref:System.Data.DataTable> con los datos devueltos. Los TableAdapters también puede enviar datos actualizados desde la aplicación a la base de datos.

Los TableAdapters se crean automáticamente al realizar una de las siguientes acciones:

-   Ejecute el [Asistente para configuración de orígenes de datos](../data-tools/media/data-source-configuration-wizard.png) y seleccione la **base de datos** o **servicio Web** tipo de origen de datos.

-   Arrastrar objetos de base de datos de **Explorador de servidores** en el **Diseñador de Dataset**.

También puede crear un nuevo TableAdapter y configurarlo con un origen de datos arrastrando un TableAdapter desde el cuadro de herramientas a un área vacío en la **Diseñador de Dataset** superficie.

Para obtener una introducción a TableAdapters, vea [rellenar conjuntos de datos mediante el uso de los TableAdapters](../data-tools/fill-datasets-by-using-tableadapters.md).

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

## <a name="use-the-tableadapter-configuration-wizard"></a>Use el Asistente para configuración de TableAdapter
Ejecute el **Asistente para configuración de TableAdapter** para crear o editar objetos TableAdapters y los objetos DataTables asociados. Puede configurar un TableAdapter existente con el botón secundario en él en el **Diseñador de Dataset**.

![Asistente para configuración de adaptador de tabla raddata](../data-tools/media/raddata-table-adapter-configuration-wizard.png "raddata Asistente de configuración de adaptador de tabla")

Si se arrastra un nuevo TableAdapter desde el cuadro de herramientas cuando el **Diseñador de Dataset** está en centrarse, inicia el asistente y solicita que especifique qué datos del origen de TableAdapter debe conectarse a. En la página siguiente, el asistente le preguntará qué tipo de comandos debe usar para comunicarse con la base de datos, instrucciones SQL o procedimientos almacenados. (No verá esto si va a configurar un TableAdapter que ya está asociado a un origen de datos.)

-   Tiene la opción para crear un nuevo procedimiento almacenado en la base de datos subyacente, si tiene los permisos correctos para la base de datos. Si no tiene estos permisos, esto no será una opción.

-   También puede elegir ejecutar los procedimientos almacenados existentes para la **seleccione**, **insertar**, **actualización**, y **eliminar** los comandos de la TableAdapter. El procedimiento almacenado que se asigna a la **actualización** comando, por ejemplo, se ejecuta cuando el `TableAdapter.Update()` se llama al método.

Asigne parámetros desde el procedimiento almacenado seleccionado a las columnas correspondientes de la tabla de datos. Por ejemplo, si el procedimiento almacenado acepta un parámetro denominado `@CompanyName` que pasa a la `CompanyName` conjunto de columnas en la tabla, el **columna de origen** de la `@CompanyName` parámetro `CompanyName`.

> [!NOTE]
>  El procedimiento almacenado que se asigna al comando SELECT se ejecuta llamando al método del TableAdapter ese nombre en el paso siguiente del asistente. El método predeterminado es `Fill`, por lo que el código que normalmente se usa para ejecutar el procedimiento SELECT es `TableAdapter.Fill(tableName)`. Si cambia el nombre predeterminado de `Fill`, sustituir `Fill` con el nombre asignar y reemplace "TableAdapter" por el nombre real del TableAdapter (por ejemplo, `CustomersTableAdapter`).

-   Al seleccionar la **crear métodos para enviar actualizaciones directamente a la base de datos** opción es equivalente a establecer el `GenerateDBDirectMethods` propiedad en true. La opción no está disponible cuando la instrucción SQL original no proporciona bastante información o la consulta no es una consulta actualizable. Esto puede suceder, por ejemplo, en **UNIR** las consultas y las consultas que devuelven un único valor (escalar).

El **opciones avanzadas** en el Asistente para permitirle:
- Generar instrucciones INSERT, UPDATE y DELETE basadas en la instrucción SELECT que se define en el **generar las instrucciones SQL** página
- Usar simultaneidad optimista
- Especifique si desea actualizar la tabla de datos después de la INSERCIÓN y se ejecutan las instrucciones UPDATE

## <a name="configure-a-tableadapters-fill-method"></a>Configurar método de relleno de un TableAdapter
En ocasiones, puede cambiar el esquema de la tabla del TableAdapter. Para ello, modifique principal del TableAdapter `Fill` método. Los TableAdapters se crean con un elemento principal `Fill` método que define el esquema de la tabla de datos asociada. La principal `Fill` método se basa en la consulta o el procedimiento almacenado que se escribió cuando se configuró originalmente el TableAdapter. Es el primer método (superior) en la tabla de datos en el Diseñador de DataSet.

![TableAdapter con varias consultas](../data-tools/media/tableadapter.gif "TableAdapter")

Principal de los cambios realizados en el TableAdapter `Fill` método se refleja en el esquema de la tabla de datos asociada. Por ejemplo, quitar una columna de la consulta en la ventana principal `Fill` método también quita la columna de la tabla de datos asociada. Además, quitar la columna de los principales `Fill` método quita la columna de cualquier consulta adicional a ese objeto TableAdapter.

Puede usar al Asistente para configuración de consultas de TableAdapter para crear y editar consultas adicionales de TableAdapter. Estas consultas adicionales deben ajustarse al esquema de tabla, a menos que devuelven un valor escalar.  Cada consulta adicional tiene un nombre que especifique.

En el ejemplo siguiente se muestra cómo llamar a una consulta adicional denominada `FillByCity`:

`CustomersTableAdapter.FillByCity(NorthwindDataSet.Customers, "Seattle")`

#### <a name="to-start-the-tableadapter-query-configuration-wizard-with-a-new-query"></a>Para iniciar al Asistente para configuración de consultas de TableAdapter con una nueva consulta

1.  Abra su conjunto de datos en el **Diseñador de Dataset**.

2.  Si va a crear una nueva consulta, arrastre un **consulta** objeto desde el **conjunto de datos** pestaña de la **cuadro de herramientas** en un <xref:System.Data.DataTable>, o seleccione **Agregar consulta**desde el menú contextual del TableAdapter. También puede arrastrar un **consulta** objeto en un área vacía de la **Diseñador de Dataset**, que crea un TableAdapter sin asociada <xref:System.Data.DataTable>. Estas consultas solo pueden devolver valores únicos de (escalares) o ejecución UPDATE, INSERT o eliminar comandos en la base de datos.

3.  En el **elegir la conexión de datos** pantalla, seleccione o cree la conexión que va a utilizar la consulta.

    > [!NOTE]
    >  Esta pantalla sólo aparece cuando el diseñador no puede determinar la conexión apropiada que utilizar, o cuando no hay disponible ninguna conexión.

4.  En el **elegir un tipo de comando** pantalla, seleccione uno de los siguientes métodos de obtención de datos de la base de datos:

    -   **Usar instrucciones SQL** le permite escribir una instrucción SQL para seleccionar los datos de la base de datos.

    -   **Crear nuevo procedimiento almacenado** permite que el Asistente para crear un nuevo procedimiento almacenado (en la base de datos) en función de la instrucción SELECT especificada.

    -   **Usar procedimientos almacenados existentes** permite ejecutar un procedimiento almacenado existente al ejecutar la consulta.

#### <a name="to-start-the-tableadapter-query-configuration-wizard-on-an-existing-query"></a>Para iniciar al Asistente para configuración de consultas de TableAdapter en una consulta existente

-   Si va a editar una consulta de TableAdapter existente, haga clic en la consulta y, a continuación, elija **configurar** en el menú contextual.

    > [!NOTE]
    >  Con el botón secundario de la consulta principal de un TableAdapter vuelve a configurar el TableAdapter y <xref:System.Data.DataTable> esquema. Con el botón secundario de una consulta en un TableAdapter, sin embargo, se configura sólo la consulta seleccionada. El **Asistente para configuración de TableAdapter** reconfigura la definición de TableAdapter, mientras que el Asistente para configuración de consultas de TableAdapter reconfigura sólo la consulta seleccionada.

#### <a name="to-add-a-global--query-to-a-tableadapter"></a>Para agregar una consulta global a un TableAdapter

-   *Consultas globales* son consultas SQL que devuelven un único valor (escalar) o ningún valor. Normalmente, las funciones globales realizan operaciones de base de datos como las inserciones, actualizaciones, eliminaciones. También agrega información, como un recuento de clientes en una tabla o el costo total de todos los elementos en un orden concreto.

     Agregar consultas globales, arrastre un **consulta** del objeto de la **conjunto de datos** pestaña de la **cuadro de herramientas** en un área vacía de la **Diseñador de Dataset**.

-   Proporcionar una consulta que realiza la tarea deseada, por ejemplo, `SELECT COUNT(*) AS CustomerCount FROM Customers`.

    > [!NOTE]
    >  Arrastrar un **consulta** objeto directamente en el **Diseñador de Dataset** crea un método que devuelva solo un valor escalar (único). Mientras que la consulta o el procedimiento almacenado que selecciona puede devolver más de un solo valor, el método que es creado por el Asistente solo devuelve un valor único. Por ejemplo, la consulta podría devolver la primera columna de la primera fila de los datos devueltos.

## <a name="see-also"></a>Vea también

- [Llenar conjuntos de datos mediante TableAdapters](../data-tools/fill-datasets-by-using-tableadapters.md)