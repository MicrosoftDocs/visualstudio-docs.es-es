---
title: Crear y configurar TableAdapters | Microsoft Docs
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
- table adapters, creating
- creating TableAdapters
- data [Visual Studio], creating data components
- data [Visual Studio], TableAdapters
- data [Visual Studio], creating table adapters
ms.assetid: 08630d69-0d6c-4e8f-b42d-2922f45f8415
caps.latest.revision: 33
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 9a2136960dfcbbbcf63fbefeb16d527793d4b939
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "72631038"
---
# <a name="create-and-configure-tableadapters"></a>Crear y configurar TableAdapters
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Los TableAdapters comunican la aplicación con una base de datos. Se conectan a la base de datos, ejecutan consultas o procedimientos almacenados y devuelven una nueva tabla de datos o rellenan una existente <xref:System.Data.DataTable> con los datos devueltos. Los TableAdapters también pueden enviar datos actualizados desde la aplicación a la base de datos.

 Los TableAdapters se crean automáticamente cuando se realiza una de las siguientes acciones:

- Ejecute el [Asistente para la configuración de orígenes de datos](https://msdn.microsoft.com/library/c4df7de5-5da0-4064-940c-761dd6d9e28f) y seleccione el tipo de origen de datos **base** de datos o **servicio Web** .

- Arrastre los objetos de base de datos de [Explorador de servidores](https://msdn.microsoft.com/library/4ea29b3b-bbb2-45e4-9082-eaf635c41c4d) al **Diseñador de DataSet**.

  Puede crear un nuevo TableAdapter y configurarlo con un origen de datos arrastrando un TableAdapter desde el cuadro de herramientas a una región vacía de la superficie de **Diseñador de DataSet** .

  Para obtener una introducción a los TableAdapters, vea [rellenar conjuntos de valores mediante TableAdapters](../data-tools/fill-datasets-by-using-tableadapters.md).

  [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]

## <a name="use-the-tableadapter-configuration-wizard"></a>Usar el Asistente para configuración de TableAdapter
 Ejecute el **Asistente** para la configuración de TableAdapter para crear o editar TableAdapters y sus tablas de objetos asociadas. Para configurar un TableAdapter existente, haga clic con el botón derecho en él en el **Diseñador de DataSet**.

 ![Asistente para configuración del adaptador de tabla de raddata](../data-tools/media/raddata-table-adapter-configuration-wizard.png "Asistente para configuración del adaptador de tabla de raddata")

 Si arrastra un nuevo TableAdapter desde el cuadro de herramientas cuando el **Diseñador de DataSet** está en el foco, el asistente le pedirá que especifique a qué origen de datos debe conectarse el TableAdapter y qué tipo de comandos debe utilizar para comunicarse con la base de datos, las instrucciones SQL o los procedimientos almacenados. No verá esto si está configurando un TableAdapter que ya está asociado a un origen de datos.

- El uso de la opción **crear métodos para enviar actualizaciones directamente a la base de datos** equivale a establecer la `GenerateDBDirectMethods` propiedad en true. Esta opción no está disponible cuando la instrucción SQL original no proporciona bastante información o la consulta no es una consulta actualizable. Esta situación puede producirse, por ejemplo, en consultas **join** y consultas que devuelven un único valor (escalar).

- Tiene la opción de crear un nuevo procedimiento almacenado en la base de datos subyacente si tiene los permisos correctos para la base de datos. Si no tiene estos permisos, no será una opción.

- También puede optar por ejecutar los procedimientos almacenados existentes para los comandos **Select**, **Insert**, **Update**y **Delete** de TableAdapter. El procedimiento almacenado que se asigna al comando de **actualización** , por ejemplo, se ejecuta cuando `TableAdapter.Update()` se llama al método.

     Asigne parámetros desde el procedimiento almacenado seleccionado a las columnas correspondientes de la tabla de datos. Por ejemplo, si el procedimiento almacenado acepta un parámetro denominado `@CompanyName` que pasa a la `CompanyName` columna de la tabla, establezca la **columna de origen** del `@CompanyName` parámetro en `CompanyName` .

    > [!NOTE]
    > El procedimiento almacenado que se asigna al comando SELECT se ejecuta llamando al método de TableAdapter que se denomina en el paso siguiente del asistente. El método predeterminado es `Fill` , por lo que el código que se usa normalmente para ejecutar el procedimiento Select es `TableAdapter.Fill(tableName)` . Si cambia el nombre predeterminado de `Fill` , sustituya `Fill` por el nombre que asigne y reemplace "TableAdapter" por el nombre real de TableAdapter (por ejemplo, `CustomersTableAdapter` ).

- Las **Opciones avanzadas** del asistente le permiten generar instrucciones INSERT, Update y DELETE basadas en la instrucción SELECT que se define en la página **generar instrucciones SQL** . Use la simultaneidad optimista y especifique si desea actualizar la tabla de datos después de que se ejecuten las instrucciones INSERT y UPDATE.

## <a name="configure-a-tableadapters-fill-method"></a>Configurar el método Fill de un TableAdapter
 En ocasiones, es posible que desee cambiar el esquema de la tabla de TableAdapter. Para ello, modifique el método principal del TableAdapter `Fill` . Los TableAdapters se crean con un `Fill` método principal que define el esquema de la tabla de datos asociada. El `Fill` método principal se basa en la consulta o el procedimiento almacenado que se especificó cuando se configuró originalmente el TableAdapter. Es el primer método (más alto) de la tabla de datos en el diseñador de DataSet.

 ![TableAdapter con múltiples consultas](../data-tools/media/tableadapter.gif "TableAdapter")

 Cualquier cambio que realice en el método Main del TableAdapter `Fill` se reflejará en el esquema de la tabla de datos asociada. Por ejemplo, al quitar una columna de la consulta en el `Fill` método Main, también se quita la columna de la tabla de datos asociada. Además, al quitar la columna del método Main, se `Fill` quita la columna de cualquier consulta adicional para ese TableAdapter.

 Puede usar el Asistente para configuración de consultas de TableAdapter para crear y editar consultas adicionales para el TableAdapter. Estas consultas adicionales deben ajustarse al esquema de tabla, a menos que devuelvan un valor escalar.  Las consultas adicionales tienen los nombres especificados (por ejemplo, `CustomersTableAdapter.FillByCity(NorthwindDataSet.Customers, "Seattle")` ).

#### <a name="to-start-the-tableadapter-query-configuration-wizard-with-a-new-query"></a>Para iniciar el Asistente para configuración de consultas de TableAdapter con una nueva consulta

1. Abra su conjunto de datos en el **Diseñador de Dataset**.

2. Si va a crear una nueva consulta, arrastre un objeto de **consulta** desde la pestaña **DataSet** del **cuadro de herramientas** hasta un <xref:System.Data.DataTable> o seleccione **Agregar consulta** desde el menú contextual del TableAdapter. También puede arrastrar un objeto de **consulta** hasta un área vacía de la **Diseñador de DataSet**, que crea un TableAdapter sin un asociado <xref:System.Data.DataTable> . Estas consultas solo pueden devolver valores únicos (escalares) o ejecutar comandos UPDATE, INSERT o DELETE en la base de datos.

3. En la pantalla **elegir la conexión de datos** , seleccione o cree la conexión que usará la consulta.

    > [!NOTE]
    > Esta pantalla solo aparece cuando el diseñador no puede determinar la conexión adecuada que se va a utilizar o cuando no hay ninguna conexión disponible.

4. En la pantalla **elegir un tipo de comando** , seleccione uno de los siguientes métodos para obtener datos de la base de datos:

    - **Usar instrucciones SQL** le permite escribir una instrucción SQL para seleccionar los datos de la base de datos.

    - **Crear nuevo procedimiento almacenado** permite que el asistente cree un nuevo procedimiento almacenado (en la base de datos) basándose en la instrucción SELECT especificada.

    - **Usar procedimientos almacenados existentes** le permite ejecutar un procedimiento almacenado existente al ejecutar la consulta.

#### <a name="to-start-the-tableadapter-query-configuration-wizard-on-an-existing-query"></a>Para iniciar el Asistente para configuración de consultas de TableAdapter en una consulta existente

- Si está editando una consulta de TableAdapter existente, haga clic con el botón secundario en la consulta y, a continuación, elija **configurar** en el menú contextual.

    > [!NOTE]
    > Al hacer clic con el botón secundario en la consulta principal de TableAdapter, se reconfiguran el TableAdapter y el <xref:System.Data.DataTable> esquema. Sin embargo, al hacer clic con el botón secundario en una consulta adicional en un TableAdapter, solo se configura la consulta seleccionada. El **Asistente para configuración de TableAdapter** vuelve a configurar la definición de TableAdapter, mientras que el Asistente para configuración de consultas de TableAdapter vuelve a configurar solo la consulta seleccionada.

#### <a name="to-add-a-global--query-to-a-tableadapter"></a>Para agregar una consulta global a un TableAdapter

- *Las consultas globales* son consultas SQL que devuelven un único valor (escalar) o ningún valor. Normalmente, las funciones globales realizan operaciones de base de datos como inserciones, actualizaciones y eliminaciones. También agregan información, como un recuento de clientes en una tabla o los cargos totales de todos los artículos en un orden determinado.

     Para agregar consultas globales, arrastre un objeto de **consulta** desde la pestaña **conjunto** de propiedades del **cuadro de herramientas** hasta un área vacía de la **Diseñador de DataSet**.

- Proporcione una consulta que realice la tarea deseada, por ejemplo, `SELECT COUNT(*) AS CustomerCount FROM Customers` .

    > [!NOTE]
    > Al arrastrar un objeto de **consulta** directamente al **Diseñador de DataSet** , se crea un método que solo devuelve un valor escalar (único). Aunque es posible que la consulta o el procedimiento almacenado que seleccione devuelvan más de un valor único, el método creado por el asistente solo devuelve un valor único. Por ejemplo, la consulta podría devolver la primera columna de la primera fila de los datos devueltos.

## <a name="see-also"></a>Consulte también
 [Rellenar conjuntos de datos mediante TableAdapters](../data-tools/fill-datasets-by-using-tableadapters.md)
