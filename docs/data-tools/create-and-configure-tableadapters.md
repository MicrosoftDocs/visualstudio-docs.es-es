---
title: Crear y configurar TableAdapters
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
manager: jillfra
ms.prod: visual-studio-dev15
ms.workload:
- data-storage
ms.openlocfilehash: 7f43cbd8e9002d026fba632046907dfee969884d
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 01/25/2019
ms.locfileid: "54948367"
---
# <a name="create-and-configure-tableadapters"></a>Crear y configurar TableAdapters

Los TableAdapters comunican la aplicación con una base de datos. Se conectan a la base de datos, ejecutar consultas o procedimientos almacenados, y devuelven nuevos datos de tabla o rellenar existente <xref:System.Data.DataTable> con los datos devueltos. Los TableAdapters también puede enviar datos actualizados desde la aplicación a la base de datos.

Los TableAdapters se crean automáticamente al realizar una de las siguientes acciones:

- Arrastre los objetos de base de datos de **Explorador de servidores** en el **Diseñador de Dataset**.

- Ejecute el Asistente para configuración de orígenes de datos y seleccione el **base de datos** o **servicio Web** tipo de origen de datos.

   ![Asistente para configuración de origen de datos en Visual Studio](media/data-source-configuration-wizard.png)

También puede crear un nuevo TableAdapter y configurarlo con un origen de datos si arrastra un TableAdapter desde el **cuadro de herramientas** a un área vacío en el **Diseñador de Dataset** superficie.

Para obtener una introducción a los TableAdapters, vea [llenar conjuntos de datos mediante TableAdapters](../data-tools/fill-datasets-by-using-tableadapters.md).

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

## <a name="use-the-tableadapter-configuration-wizard"></a>Utilice al Asistente para configuración de TableAdapter

Ejecute el **TableAdapter Configuration Wizard** para crear o editar objetos TableAdapters y los objetos DataTables asociados. Puede configurar un TableAdapter existente con el botón secundario en él en el **Diseñador de Dataset**.

![Asistente para configuración de adaptador de tabla raddata](../data-tools/media/raddata-table-adapter-configuration-wizard.png)

Si arrastra un nuevo TableAdapter desde el cuadro de herramientas cuando el **Diseñador de Dataset** está en centrarse, se inicia el asistente e indicaciones para especificar qué datos de origen del TableAdapter deben conectarse a. En la página siguiente, el asistente pregunta qué tipo de comandos debe usar para comunicarse con la base de datos, instrucciones SQL o procedimientos almacenados. (No verá esto si está configurando un TableAdapter que ya está asociado con un origen de datos.)

- Tiene la opción para crear un nuevo procedimiento almacenado en la base de datos subyacente, si tiene los permisos correctos para la base de datos. Si no tiene estos permisos, esto no será una opción.

- También puede ejecutar los procedimientos almacenados existentes para el **seleccione**, **insertar**, **actualización**, y **eliminar** los comandos de la TableAdapter. El procedimiento almacenado que se asigna a la **actualización** comando, por ejemplo, se ejecuta cuando el `TableAdapter.Update()` se llama al método.

Asigne parámetros desde el procedimiento almacenado seleccionado a las columnas correspondientes de la tabla de datos. Por ejemplo, si el procedimiento almacenado acepta un parámetro denominado `@CompanyName` que pasa a la `CompanyName` conjunto de columnas en la tabla, el **columna de origen** de la `@CompanyName` parámetro `CompanyName`.

> [!NOTE]
> El procedimiento almacenado asignado al comando SELECT se ejecuta llamando al método del TableAdapter ese nombre en el paso siguiente del asistente. El método predeterminado es `Fill`, por lo que el código que se utiliza normalmente para ejecutar el procedimiento SELECT es `TableAdapter.Fill(tableName)`. Si cambia el nombre predeterminado de `Fill`, sustituya `Fill` con el nombre que asigne y reemplace "TableAdapter" por el nombre real del TableAdapter (por ejemplo, `CustomersTableAdapter`).

- Seleccionar el **crear métodos para enviar actualizaciones directamente a la base de datos** opción es equivalente a establecer el `GenerateDBDirectMethods` propiedad en true. Esta opción no está disponible cuando la instrucción SQL original no proporciona bastante información o la consulta no es una consulta actualizable. Esta situación puede ocurrir, por ejemplo, en **UNIR** las consultas y las consultas que devuelven un único valor (escalar).

El **opciones avanzadas** en el asistente le permiten:

- Generar instrucciones INSERT, UPDATE y DELETE basadas en la instrucción SELECT que se define en el **generar instrucciones SQL** página
- Usar simultaneidad optimista
- Especifique si desea actualizar la tabla de datos después de la INSERCIÓN y se ejecutan las instrucciones UPDATE

## <a name="configure-a-tableadapters-fill-method"></a>Configuración del método de relleno de un TableAdapter

En ocasiones, es posible que desea cambiar el esquema de tabla del TableAdapter. Para ello, modifica principal del TableAdapter `Fill` método. Los TableAdapters se crean con un elemento principal `Fill` método que define el esquema de la tabla de datos asociada. La principal `Fill` método se basa en la consulta o procedimiento almacenado que escribió cuando se configuró originalmente el TableAdapter. Es el primer método (superior) en la tabla de datos en el Diseñador de DataSet.

![TableAdapter con múltiples consultas](../data-tools/media/tableadapter.gif)

Principal de los cambios realizados en el TableAdapter `Fill` método se reflejan en el esquema de la tabla de datos asociada. Por ejemplo, quitar una columna de la consulta en la ventana principal `Fill` método también quita la columna de la tabla de datos asociada. Además, quite la columna en la página principal `Fill` método quita la columna de cualquier consulta adicional a ese objeto TableAdapter.

Puede usar al Asistente para configuración de consulta de TableAdapter para crear y editar consultas adicionales del TableAdapter. Estas consultas adicionales deben ajustarse al esquema de tabla, a menos que devuelven un valor escalar.  Cada consulta adicional tiene un nombre que especifique.

El ejemplo siguiente muestra cómo llamar a una consulta adicional denominada `FillByCity`:

`CustomersTableAdapter.FillByCity(NorthwindDataSet.Customers, "Seattle")`

### <a name="to-start-the-tableadapter-query-configuration-wizard-with-a-new-query"></a>Para iniciar al Asistente para configuración de consulta de TableAdapter con una consulta nueva

1.  Abra su conjunto de datos en el **Diseñador de Dataset**.

2.  Si va a crear una nueva consulta, arrastre un **consulta** objeto desde el **conjunto de datos** pestaña de la **cuadro de herramientas** hasta un <xref:System.Data.DataTable>, o seleccione **Add Query**desde el menú contextual del TableAdapter. También puede arrastrar un **consulta** objeto en un área vacía de la **Diseñador de Dataset**, que crea un TableAdapter sin asociado un <xref:System.Data.DataTable>. Estas consultas solo pueden devolver valores únicos de (escalares) o ejecutar UPDATE, INSERT o eliminar comandos en la base de datos.

3.  En el **elegir la conexión de datos** pantalla, seleccione o cree la conexión que va a usar la consulta.

    > [!NOTE]
    > Esta pantalla sólo aparece cuando el diseñador no puede determinar la conexión apropiada que use, o cuando no hay conexiones disponibles.

4.  En el **elegir un tipo de comando** pantalla, seleccione uno de los siguientes métodos de captura de datos de la base de datos:

    - **Usar instrucciones SQL** permite escribir una instrucción SQL para seleccionar los datos de la base de datos.

    - **Crear nuevo procedimiento almacenado** permite que el Asistente para crear un nuevo procedimiento almacenado (en la base de datos) basándose en la instrucción SELECT especificada.

    - **Usar procedimientos almacenados existentes** le permite ejecutar un procedimiento almacenado existente cuando se ejecuta la consulta.

### <a name="to-start-the-tableadapter-query-configuration-wizard-on-an-existing-query"></a>Para iniciar al Asistente para configuración de la consulta de TableAdapter en una consulta existente

- Si va a editar una consulta de TableAdapter existente, haga clic en la consulta y, a continuación, elija **configurar** en el menú contextual.

    > [!NOTE]
    > Haciendo clic en la consulta principal de un TableAdapter se vuelve a configurar el TableAdapter y <xref:System.Data.DataTable> esquema. Haciendo clic en una consulta adicional de un TableAdapter, sin embargo, se configura sólo la consulta seleccionada. El **TableAdapter Configuration Wizard** vuelve a configurar la definición de TableAdapter, mientras que el **TableAdapter Query Configuration Wizard** reconfigura sólo la consulta seleccionada.

### <a name="to-add-a-global-query-to-a-tableadapter"></a>Para agregar una consulta global a un TableAdapter

- Consultas globales son consultas SQL que devuelven un único valor (escalar) o ningún valor. Normalmente, las funciones globales realizan operaciones de base de datos, como inserciones, actualizaciones y eliminaciones. También realiza la agregación de información, como un recuento de clientes en una tabla o los cargos totales para todos los elementos en un orden concreto.

     Agregar consultas globales arrastrando un **consulta** objeto desde el **conjunto de datos** pestaña de la **cuadro de herramientas** en un área vacía de la **delDiseñadordeDataset**.

- Proporcionar una consulta que realiza la tarea deseada, por ejemplo, `SELECT COUNT(*) AS CustomerCount FROM Customers`.

    > [!NOTE]
    > Arrastrar un **consulta** objeto directamente en el **Diseñador de Dataset** crea un método que devuelve solo un valor escalar (único). Mientras que la consulta o procedimiento almacenado que selecciona podría devolver más de un solo valor, el método que se crea mediante el Asistente solo devuelve un valor único. Por ejemplo, la consulta podría devolver la primera columna de la primera fila de los datos devueltos.

## <a name="see-also"></a>Vea también

- [Llenar conjuntos de datos mediante TableAdapters](../data-tools/fill-datasets-by-using-tableadapters.md)