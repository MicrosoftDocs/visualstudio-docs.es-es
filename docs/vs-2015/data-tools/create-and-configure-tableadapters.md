---
title: Crear y configurar TableAdapters | Documentos de Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
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
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 03cb6c67b4887762885a0cb920eb928359b4708b
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49917653"
---
# <a name="create-and-configure-tableadapters"></a>Crear y configurar TableAdapters
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Los TableAdapters comunican la aplicación con una base de datos. Se conectan a la base de datos, ejecutar consultas o procedimientos almacenados, y devuelven nuevos datos de tabla o rellenar existente <xref:System.Data.DataTable> con los datos devueltos. Los TableAdapters también puede enviar datos actualizados desde la aplicación a la base de datos.  
  
 Los TableAdapters se crean automáticamente al realizar una de las siguientes acciones:  
  
- Ejecute el [Asistente para configuración de origen de datos](http://msdn.microsoft.com/library/c4df7de5-5da0-4064-940c-761dd6d9e28f) y seleccione el **base de datos** o **servicio Web** tipo de origen de datos.  
  
- Arrastre los objetos de base de datos de [Explorador de servidores](http://msdn.microsoft.com/library/4ea29b3b-bbb2-45e4-9082-eaf635c41c4d) en el **Diseñador de Dataset**.  
  
  Puede crear un nuevo TableAdapter y configurarlo con un origen de datos arrastrando un TableAdapter desde el cuadro de herramientas a un área vacío en el **Diseñador de Dataset** superficie.  
  
  Para obtener una introducción a los TableAdapters, vea [llenar conjuntos de datos mediante TableAdapters](../data-tools/fill-datasets-by-using-tableadapters.md).  
  
  [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]  
  
## <a name="use-the-tableadapter-configuration-wizard"></a>Utilice al Asistente para configuración de TableAdapter  
 Ejecute el **TableAdapter Configuration Wizard** para crear o editar objetos TableAdapters y los objetos DataTables asociados. Puede configurar un TableAdapter existente con el botón secundario en él en el **Diseñador de Dataset**.  
  
 ![Asistente para configuración de adaptador de tabla raddata](../data-tools/media/raddata-table-adapter-configuration-wizard.png "raddata Asistente para configuración de adaptador de tabla")  
  
 Si arrastra un nuevo TableAdapter desde el cuadro de herramientas cuando el **Diseñador de Dataset** tiene el foco, las indicaciones del Asistente para especificar el origen de datos debe conectarse el TableAdapter y qué tipo de comandos deben usar para comunicarse con el base de datos, instrucciones SQL o procedimientos almacenados. No podrá ver si está configurando un TableAdapter que ya está asociado con un origen de datos.  
  
-   Mediante el **crear métodos para enviar actualizaciones directamente a la base de datos** opción es equivalente a establecer el `GenerateDBDirectMethods` propiedad en true. La opción no está disponible cuando la instrucción SQL original no proporciona suficiente información o la consulta no es una consulta actualizable. Esta situación puede ocurrir, por ejemplo, en **UNIR** las consultas y las consultas que devuelven un único valor (escalar).  
  
-   Tiene la opción para crear un nuevo procedimiento almacenado en la base de datos subyacente, si tiene los permisos correctos para la base de datos. Si no tiene estos permisos, esto no será una opción.  
  
-   También puede ejecutar los procedimientos almacenados existentes para el **seleccione**, **insertar**, **actualización**, y **eliminar** los comandos de la TableAdapter. El procedimiento almacenado que se asigna a la **actualización** comando, por ejemplo, se ejecuta cuando el `TableAdapter.Update()` se llama al método.  
  
     Asigne parámetros desde el procedimiento almacenado seleccionado a las columnas correspondientes de la tabla de datos. Por ejemplo, si el procedimiento almacenado acepta un parámetro denominado `@CompanyName` que pasa a la `CompanyName` conjunto de columnas en la tabla, el **columna de origen** de la `@CompanyName` parámetro `CompanyName`.  
  
    > [!NOTE]
    >  El procedimiento almacenado asignado al comando SELECT se ejecuta llamando al método del TableAdapter ese nombre en el paso siguiente del asistente. El método predeterminado es `Fill`, por lo que el código que se utiliza normalmente para ejecutar el procedimiento SELECT es `TableAdapter.Fill(tableName)`. Si cambia el nombre predeterminado de `Fill`, sustituya `Fill` con el nombre que asigne y reemplace "TableAdapter" por el nombre real del TableAdapter (por ejemplo, `CustomersTableAdapter`).  
  
-   El **opciones avanzadas** en el asistente le permiten generar instrucciones INSERT, UPDATE y DELETE basadas en la instrucción SELECT que se define en el **generar instrucciones SQL** página. Usar simultaneidad optimista y especificar si se ejecutan las instrucciones para actualizar la tabla de datos después de INSERT y UPDATE.  
  
## <a name="configure-a-tableadapters-fill-method"></a>Configuración del método de relleno de un TableAdapter  
 En ocasiones, es posible que desea cambiar el esquema de tabla del TableAdapter. Para ello, modifica principal del TableAdapter `Fill` método. Los TableAdapters se crean con un elemento principal `Fill` método que define el esquema de la tabla de datos asociada. La principal `Fill` método se basa en la consulta o procedimiento almacenado que escribió cuando se configuró originalmente el TableAdapter. Es el primer método (superior) en la tabla de datos en el Diseñador de DataSet.  
  
 ![TableAdapter con varias consultas](../data-tools/media/tableadapter.gif "TableAdapter")  
  
 Principal de los cambios realizados en el TableAdapter `Fill` método se reflejan en el esquema de la tabla de datos asociada. Por ejemplo, quitar una columna de la consulta en la ventana principal `Fill` método también quita la columna de la tabla de datos asociada. Además, quite la columna en la página principal `Fill` método quita la columna de cualquier consulta adicional a ese objeto TableAdapter.  
  
 Puede usar al Asistente para configuración de consulta de TableAdapter para crear y editar consultas adicionales del TableAdapter. Estas consultas adicionales deben ajustarse al esquema de tabla, a menos que devuelven un valor escalar.  Las consultas adicionales tienen los nombres que especifique (por ejemplo, `CustomersTableAdapter.FillByCity(NorthwindDataSet.Customers, "Seattle")`.)  
  
#### <a name="to-start-the-tableadapter-query-configuration-wizard-with-a-new-query"></a>Para iniciar al Asistente para configuración de consulta de TableAdapter con una consulta nueva  
  
1.  Abra el conjunto de datos en el **Diseñador de Dataset**.  
  
2.  Si va a crear una nueva consulta, arrastre un **consulta** objeto desde el **conjunto de datos** pestaña de la **cuadro de herramientas** hasta un <xref:System.Data.DataTable>, o seleccione **Add Query**desde el menú contextual del TableAdapter. También puede arrastrar un **consulta** objeto en un área vacía de la **Diseñador de Dataset**, que crea un TableAdapter sin asociado un <xref:System.Data.DataTable>. Estas consultas solo pueden devolver valores únicos de (escalares) o ejecutar UPDATE, INSERT o eliminar comandos en la base de datos.  
  
3.  En el **elegir la conexión de datos** pantalla, seleccione o cree la conexión que va a usar la consulta.  
  
    > [!NOTE]
    >  Esta pantalla sólo aparece cuando el diseñador no puede determinar la conexión apropiada que use, o cuando no hay conexiones disponibles.  
  
4.  En el **elegir un tipo de comando** pantalla, seleccione uno de los siguientes métodos de captura de datos de la base de datos:  
  
    -   **Usar instrucciones SQL** permite escribir una instrucción SQL para seleccionar los datos de la base de datos.  
  
    -   **Crear nuevo procedimiento almacenado** permite que el Asistente para crear un nuevo procedimiento almacenado (en la base de datos) basándose en la instrucción SELECT especificada.  
  
    -   **Usar procedimientos almacenados existentes** le permite ejecutar un procedimiento almacenado existente cuando se ejecuta la consulta.  
  
#### <a name="to-start-the-tableadapter-query-configuration-wizard-on-an-existing-query"></a>Para iniciar al Asistente para configuración de la consulta de TableAdapter en una consulta existente  
  
-   Si va a editar una consulta de TableAdapter existente, haga clic en la consulta y, a continuación, elija **configurar** en el menú contextual.  
  
    > [!NOTE]
    >  Haciendo clic en la consulta principal de un TableAdapter se vuelve a configurar el TableAdapter y <xref:System.Data.DataTable> esquema. Haciendo clic en una consulta adicional de un TableAdapter, sin embargo, se configura sólo la consulta seleccionada. El **TableAdapter Configuration Wizard** reconfigura la definición de TableAdapter, mientras que el Asistente para configuración de consulta de TableAdapter se vuelve a configurar solo la consulta seleccionada.  
  
#### <a name="to-add-a-global--query-to-a-tableadapter"></a>Para agregar una consulta global a un TableAdapter  
  
-   *Consultas globales* son consultas SQL que devuelven un único valor (escalar) o ningún valor. Normalmente, funciones globales de realizan operaciones de base de datos, como inserciones, actualizaciones, se elimina. También realiza la agregación de información, como un recuento de clientes en una tabla o los cargos totales para todos los elementos en un orden concreto.  
  
     Agregar consultas globales arrastrando un **consulta** objeto desde el **conjunto de datos** pestaña de la **cuadro de herramientas** en un área vacía de la **delDiseñadordeDataset**.  
  
-   Proporcionar una consulta que realiza la tarea deseada, por ejemplo, `SELECT COUNT(*) AS CustomerCount FROM Customers`.  
  
    > [!NOTE]
    >  Arrastrar un **consulta** objeto directamente en el **Diseñador de Dataset** crea un método que devuelve solo un valor escalar (único). Mientras que la consulta o procedimiento almacenado que selecciona podría devolver más de un solo valor, el método que se crea mediante el Asistente solo devuelve un valor único. Por ejemplo, la consulta podría devolver la primera columna de la primera fila de los datos devueltos.  
  
## <a name="see-also"></a>Vea también  
 [Llenar conjuntos de datos mediante TableAdapters](../data-tools/fill-datasets-by-using-tableadapters.md)

