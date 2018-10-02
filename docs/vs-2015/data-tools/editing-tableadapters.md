---
title: Editar TableAdapters | Documentos de Microsoft
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.datasource.dbtablefunctionwizard
- vs.datasource.datacomponentquerywizard
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- data [Visual Studio], data component queries
- data [Visual Studio], TableAdapters
- TableAdapter Query Configuration Wizard
- data [Visual Studio], table adapter queries
ms.assetid: 8c06b306-24d0-4521-948d-07e3b7badd95
caps.latest.revision: 24
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: 995c1cfb5b125437847f364a01b66f3e551b8b4e
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47581088"
---
# <a name="editing-tableadapters"></a>Editar TableAdapters
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

A veces es posible que desee cambiar el esquema de tabla del adaptador. Para ello, modifica principal del adaptador `Fill` método. Los TableAdapters se crean con un main `Fill` método que define el esquema de la tabla de datos asociada. El método main `Fill` método se basa en la consulta o procedimiento almacenado que escribió cuando se configuró originalmente el TableAdapter; es el primer método (superior) en la tabla de datos en el [crear y editar conjuntos de datos con tipo](../data-tools/creating-and-editing-typed-datasets.md).  
  
 ![TableAdapter con varias consultas](../data-tools/media/tableadapter.gif "TableAdapter")  
  
 Principal de los cambios realizados en el TableAdapter `Fill` método se reflejan en el esquema de la tabla de datos asociada. Por ejemplo, quitar una columna de la consulta en la ventana principal `Fill` método también quita la columna de la tabla de datos asociada. Además, quite la columna en la página principal `Fill` método quita la columna de cualquier consulta adicional a ese objeto TableAdapter.  
  
 Puede usar el **TableAdapter Query Configuration Wizard** para crear y editar consultas adicionales del TableAdapter. Estas consultas adicionales deben ajustarse al esquema de tabla, a menos que devuelven un valor escalar.  Las consultas adicionales tienen un nombre que especifique (por ejemplo, `CustomersTableAdapter.FillByCity(NorthwindDataSet.Customers, "Seattle")`.)  
  
#### <a name="to-start-the-tableadapter-query-configuration-wizard-with-a-new-query"></a>Para iniciar al Asistente para configuración de la consulta de TableAdapter con una consulta nueva  
  
1.  Abra el conjunto de datos en el **Diseñador de Dataset**.  
  
2.  Si va a crear una nueva consulta, arrastre un **consulta** objeto desde el **conjunto de datos** pestaña de la **cuadro de herramientas** hasta un <xref:System.Data.DataTable>, o seleccione **Add Query**desde el menú contextual del TableAdapter. También puede arrastrar un **consulta** objeto en un área vacía de la **Diseñador de Dataset**, que crea un TableAdapter sin asociado un <xref:System.Data.DataTable>. Estas consultas se limitan a devolver valores únicos (escalares) o ejecutar UPDATE, INSERT o eliminación comandos en la base de datos. Para obtener más información, consulte [Cómo: agregar consultas globales a un TableAdapter](../data-tools/how-to-add-global-queries-to-a-tableadapter.md).  
  
3.  En el **elegir la conexión de datos** página, seleccione o cree la conexión utilizará la consulta.  
  
    > [!NOTE]
    >  Esta página solo aparece cuando el diseñador no puede determinar la conexión apropiada que use, o cuando no hay conexiones disponibles.  
  
4.  En el **elegir un tipo de comando** página, seleccione uno de los siguientes métodos de captura de datos de la base de datos:  
  
    -   **Usar instrucciones SQL** permite escribir una instrucción SQL para seleccionar los datos de la base de datos.  
  
    -   **Crear nuevo procedimiento almacenado** : seleccione esta opción para que el Asistente para crear un nuevo procedimiento almacenado (en la base de datos) basándose en la instrucción SELECT especificada.  
  
    -   **Usar procedimientos almacenados existentes** : seleccione esta opción para ejecutar un procedimiento almacenado existente cuando se ejecute la consulta.  
  
#### <a name="to-start-the-tableadapter-query-configuration-wizard-on-an-existing-query"></a>Para iniciar al Asistente para configuración de la consulta de TableAdapter en una consulta existente  
  
-   Si va a editar una consulta de TableAdapter existente, haga clic en la consulta y elija **configurar** en el menú contextual.  
  
    > [!NOTE]
    >  Haciendo clic en la consulta principal de un TableAdapter se vuelve a configurar el TableAdapter y <xref:System.Data.DataTable> esquema, mientras que con el botón secundario de una consulta en un TableAdapter solo configura la consulta seleccionada. El **TableAdapter Configuration Wizard** vuelve a configurar la definición de TableAdapter; el **TableAdapter Query Configuration Wizard** reconfigura sólo la consulta seleccionada.  
  
## <a name="running-the-wizard"></a>Ejecutar el asistente  
 Arrastre las consultas en el **Diseñador de Dataset**, o configure las consultas existentes (cualquier consulta que se enumeran a continuación de la primera consulta).  
  
 La primera consulta en un TableAdapter es la consulta principal de TableAdapter. Editar esta consulta principal se abre el **TableAdapter Configuration Wizard** y edita el esquema de tabla de datos del TableAdapter. Todas las consultas que aparecen debajo de la consulta principal son consultas adicionales y se configuran mediante el **TableAdapter Query Configuration Wizard**. Para obtener más información acerca de cómo ejecutar el asistente, consulte [Cómo: iniciar el Asistente para configuración de consulta de TableAdapter](http://msdn.microsoft.com/library/fc7b468e-3417-48a4-a8aa-cace8f99c24a).  
  
## <a name="choose-your-data-connection"></a>Elegir la conexión de datos  
 Elija una conexión existente en la lista de conexiones o haga clic en **nueva conexión** para crear una conexión a la base de datos.  
  
 Tras la finalización de la **las propiedades de conexión** cuadro de diálogo, el **detalles de conexión** área muestra información sobre el proveedor seleccionado así como la cadena de conexión de solo lectura.  
  
## <a name="save-the-connection-string-to-the-application-configuration-file"></a>Guardar la cadena de conexión en el archivo de configuración de la aplicación  
 Elija **Sí, guardar la conexión como** para almacenar la cadena de conexión en el archivo de configuración de la aplicación. Escriba un nombre para la conexión o utilice el nombre predeterminado proporcionado.  
  
 Las cadenas de conexión guardadas en el archivo de configuración de la aplicación simplifican el proceso de mantenimiento de la aplicación si se modifica la conexión a la base de datos. En el caso de un cambio en la conexión a la base de datos, puede editar la cadena de conexión en el archivo de configuración de la aplicación. De esta manera, no es necesario editar el código fuente ni volver a compilar la aplicación. Para obtener información acerca de cómo editar una cadena de conexión en el archivo de configuración, consulte [Cómo: guardar y editar las cadenas de conexión](~/E:/Repos/visualstudio-docs-pr/docs/data-tools/how-to-save-and-edit-connection-strings.md).  
  
> [!IMPORTANT]
>  La información se almacena en el archivo de configuración de la aplicación como texto sin formato. Para reducir la posibilidad de un acceso no autorizado a información confidencial, puede que desee cifrar los datos. Para obtener más información, consulte [cifrar y descifrar datos](http://msdn.microsoft.com/en-us/22812ae8-e082-4eb1-a29b-21b6ee00c6b5).  
  
## <a name="use-sql-statements"></a>Usar instrucciones SQL  
 En esta sección se explica cómo finalizar el **TableAdapter Query Configuration Wizard** al seleccionar el **usar instrucciones SQL** opción.  
  
## <a name="choose-a-query-type"></a>Elija un tipo de consulta  
 El asistente crea varios tipos de consultas dependiendo de los requisitos de la aplicación. Puede elegir consultas SELECT que devuelven filas de datos (una tabla de datos) o consultas SELECT que devuelven un valor escalar (un valor sencillo como `Count` o `Sum`).  
  
 En el **elegir un tipo de consulta** página, seleccione el tipo de consulta para crear a partir de la lista de consultas disponibles.  
  
> [!NOTE]
>  Crear una instrucción INSERT, UPDATE o DELETE no reemplaza los comandos de TableAdapter que se utilizan al llamar al método `Update` de TableAdapter. Por ejemplo, al seleccionar UPDATE como un tipo de consulta, se creará una nueva consulta con el nombre que se especifique después en el asistente. Esta consulta se ejecuta llamando a este método con nombre de TableAdapter. Al llamar al método `Update` de TableAdapter, se ejecutarán instrucciones que se crearon cuando se configuró el TableAdapter original.  
  
## <a name="specify-a-sql-query-type-statement"></a>Especifique una instancia de SQL \<tipo de consulta > instrucción  
 En el **especificar una instrucción SQL** página, escriba la instrucción SQL para ejecutar al llamar a la consulta.  
  
> [!TIP]
>  El asistente proporciona acceso a la **generador de consultas**, una herramienta visual para crear consultas SQL. Para abrirlo, haga clic en el **generador de consultas** botón.  
  
## <a name="choose-methods-to-generate"></a>Elegir los métodos que se van a generar  
 Esta página proporciona las opciones para seleccionar qué métodos genera el asistente para la consulta.  
  
 **Rellenar un DataTable**  
 Crea un método para rellenar la tabla de datos. El usuario pasa el nombre de la tabla de datos como un parámetro al llamar a este método para llenar la tabla de datos con los datos devueltos.  
  
 Si lo desea, puede cambiar el nombre predeterminado en el **nombre del método** cuadro. Proporcionar un nombre descriptivo puede ser útil al trabajar con esta consulta en código.  
  
 **Devolver un DataTable**  
 Crea un método para devolver una tabla de datos llena. En ciertas aplicaciones, puede ser más atractivo devolver una tabla de datos llena a diferencia de llenar con datos la existente.  
  
 Si lo desea, puede cambiar el nombre predeterminado en el **nombre del método** cuadro.  
  
## <a name="choose-function-name"></a>Elegir un nombre de función  
 Escriba un nombre para la función. Al crear una consulta de TableAdapter, se agrega un método a TableAdapter con el nombre que se proporcionó aquí. Llame a este método para ejecutar la consulta. Proporcionar un nombre descriptivo es útil al trabajar con esta consulta en código.  
  
> [!NOTE]
>  Al crear nuevos procedimientos almacenados, se le pedirán dos nombres. El primero es el nombre del procedimiento almacenado creado en la base de datos; el segundo, es el nombre del método en TableAdapter que ejecuta el procedimiento almacenado cuando se le llama.  
  
## <a name="create-new-stored-procedures"></a>Crear nuevos procedimientos almacenados  
 En esta sección se explica cómo finalizar el **TableAdapter Query Configuration Wizard** al seleccionar el **crear nuevos procedimientos almacenados** opción.  
  
1.  En el **generar los procedimientos almacenados** página, escriba la instrucción SQL que se ejecutará cuando se llama al procedimiento almacenado.  
  
    > [!NOTE]
    >  El asistente proporciona acceso a la **generador de consultas**, una herramienta visual para crear consultas SQL. Para abrirlo, haga clic en el **generador de consultas** botón.  
  
2.  En el **crear los procedimientos almacenados** página, realice lo siguiente:  
  
    1.  Escriba un nombre para el nuevo procedimiento almacenado.  
  
    2.  Especifique si se crea el procedimiento almacenado en la base de datos subyacente.  
  
        > [!NOTE]
        >  La configuración de seguridad determina la capacidad de crear un procedimiento almacenado en la base de datos para la base de datos concreta.  
  
     El **ver resultados del asistente** página muestra los resultados de la creación de la consulta de TableAdapter. Si el asistente detecta algún problema, esta pantalla proporciona información del error.  
  
## <a name="use-existing-stored-procedures"></a>Usar procedimientos almacenados existentes  
 En esta sección se explica cómo finalizar el **TableAdapter Query Configuration Wizard** al seleccionar el **usar procedimientos almacenados existentes** opción.  
  
1.  Seleccione un procedimiento almacenado existente en la lista desplegable en el **elija un procedimiento almacenado existente** página del asistente.  
  
     El **parámetros** y **resultados** almacenados seleccionado procedimiento se muestran como referencia.  
  
2.  Haga clic en **Siguiente**.  
  
## <a name="choose-the-shape-of-data-returned-by-the-stored-procedure"></a>Elegir la forma de los datos devueltos por el procedimiento almacenado  
 El tipo de datos devuelto por el procedimiento almacenado seleccionado determina cómo el asistente crea los métodos de TableAdapter.  
  
 Seleccione el tipo de datos devuelto por esta consulta.  
  
-   Seleccionar **datos tabulares** abre el **elija los métodos para generar** página (descrita anteriormente en esta página de Ayuda), que le permite especificar los tipos de métodos, los nombres de método y compatibilidad con la paginación en crearse.  
  
-   Seleccionar **un único valor** crea un método con tipo que devuelve un valor único. Esta opción abre el **Elegir nombre de función** página (descrita anteriormente en esta página de Ayuda).  
  
-   Seleccionar **ningún valor** crea un método con tipo que se ejecuta el procedimiento almacenado y espera a que no hay datos que se va a devolver. Esta opción abre el **Elegir nombre de función** página (descrita anteriormente en esta página de Ayuda).  
  
## <a name="view-wizards-results"></a>Ver resultados del asistente  
 El **ver resultados del asistente** página muestra los resultados de la creación de la consulta de TableAdapter. Si el asistente detecta problemas, los detalles aparecen en esta pantalla.  
  
## <a name="see-also"></a>Vea también  
 [Información general sobre TableAdapter](../data-tools/tableadapter-overview.md)   
 [Cómo: editar consultas de TableAdapter](../data-tools/how-to-edit-tableadapter-queries.md)   
 [Tutoriales de datos](http://msdn.microsoft.com/library/15a88fb8-3bee-4962-914d-7a1f8bd40ec4)   
 [Enlazar controles de Windows Forms a datos en Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [Información general de aplicaciones de datos en Visual Studio](../data-tools/overview-of-data-applications-in-visual-studio.md)   
 [Conectarse a datos en Visual Studio](../data-tools/connecting-to-data-in-visual-studio.md)   
 [Preparar su aplicación para recibir datos](http://msdn.microsoft.com/library/c17bdb7e-c234-4f2f-9582-5e55c27356ad)   
 [Captura de datos en la aplicación](../data-tools/fetching-data-into-your-application.md)   
 [Enlazar controles a los datos en Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [Edición de datos en la aplicación](../data-tools/editing-data-in-your-application.md)   
 [Validación de datos](http://msdn.microsoft.com/library/b3a9ee4e-5d4d-4411-9c56-c811f2b4ee7e)   
 [Guardar datos](../data-tools/saving-data.md)