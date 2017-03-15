---
title: "Asistente para la configuraci&#243;n de consultas de TableAdapter | Microsoft Docs"
ms.custom: ""
ms.date: "09/21/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.datasource.dbtablefunctionwizard"
  - "vs.datasource.datacomponentquerywizard"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "aspx"
helpviewer_keywords: 
  - "datos [Visual Studio], consultas de componentes de datos"
  - "datos [Visual Studio], consultas de adaptador de tabla"
  - "datos [Visual Studio], TableAdapters"
  - "Asistente para la configuración de consultas de TableAdapter"
ms.assetid: 8c06b306-24d0-4521-948d-07e3b7badd95
caps.latest.revision: 24
caps.handback.revision: 20
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
robots: noindex,nofollow
---
# Asistente para la configuraci&#243;n de consultas de TableAdapter
El **Asistente para la configuración de consultas de TableAdapter** ayuda a crear y editar las consultas adicionales que se pueden agregar a TableAdapters.  Una consulta de TableAdapter es cualquier consulta SQL válida o cualquier procedimiento almacenado que devuelve datos que satisfacen el mismo esquema que la tabla de datos asociada de TableAdapter, o bien devuelve un valor escalar.  Después de finalizar el asistente, se agrega un método a TableAdapter que, cuando se le llama, ejecuta la consulta.  \(Por ejemplo: `CustomersTableAdapter.FillByCity(NorthwindDataSet.Customers, "Seattle")`.\)  
  
## Ejecutar el asistente  
 Arrastre las consultas al **Diseñador de DataSet** o configure las consultas existentes \(cualquier consulta que aparezca debajo de la primera consulta\).  
  
 La primera consulta en un TableAdapter es la consulta principal de TableAdapter.  Al editar esta consulta principal, se abre el **Asistente para configuración de TableAdapter** y se edita el esquema de la tabla de datos de TableAdapter.  Todas las consultas que aparecen debajo de la consulta principal son consultas adicionales y se configuran con el **Asistente para configuración de consultas de TableAdapter**.  Para obtener más información sobre cómo ejecutar el asistente, vea [Cómo: Iniciar el Asistente para la configuración de consultas de TableAdapter](../Topic/How%20to:%20Start%20the%20TableAdapter%20Query%20Configuration%20Wizard.md).  
  
## Elegir la conexión de datos  
 Elija una conexión existente de la lista de conexiones o haga clic en **Nueva conexión** para crear una conexión a su base de datos.  
  
 Después de completar el cuadro de diálogo **Propiedades de la conexión**, el área **Detalles de conexión** muestra la información de solo lectura sobre el proveedor seleccionado así como la cadena de conexión.  
  
## Guardar la cadena de conexión en el archivo de configuración de la aplicación  
 Elija **Sí, guardar la conexión como** para almacenar la cadena de conexión en el archivo de configuración de la aplicación.  Escriba un nombre para la conexión o utilice el nombre predeterminado proporcionado.  
  
 Las cadenas de conexión guardadas en el archivo de configuración de la aplicación simplifican el proceso de mantenimiento de la aplicación si se modifica la conexión a la base de datos.  En el caso de un cambio en la conexión a la base de datos, puede editar la cadena de conexión en el archivo de configuración de la aplicación.  De esta manera, no es necesario editar el código fuente ni volver a compilar la aplicación.  Para obtener información sobre cómo editar una cadena de conexión en el archivo de configuración de la aplicación, vea [Cómo: Guardar y editar cadenas de conexión](../Topic/How%20to:%20Save%20and%20Edit%20Connection%20Strings.md).  
  
> [!IMPORTANT]
>  La información se almacena en el archivo de configuración de la aplicación como texto sin formato.  Para reducir la posibilidad de un acceso no autorizado a información confidencial, puede que desee cifrar los datos.  Para obtener más información, vea [Encrypting and Decrypting Data](http://msdn.microsoft.com/es-es/22812ae8-e082-4eb1-a29b-21b6ee00c6b5).  
  
## Usar instrucciones SQL  
 En esta sección se explica cómo finalizar el **Asistente para configuración de consultas de TableAdapter** al seleccionar la opción **Usar instrucciones SQL**.  
  
## Elija un tipo de consulta  
 El asistente crea varios tipos de consultas dependiendo de los requisitos de la aplicación.  Puede elegir consultas SELECT que devuelven filas de datos \(una tabla de datos\) o consultas SELECT que devuelven un valor escalar \(un valor sencillo como `Count` o `Sum`\).  
  
 En la página **Elija un tipo de consulta**, seleccione el tipo de consulta que va a crear a partir de la lista de consultas disponibles.  
  
> [!NOTE]
>  Crear una instrucción INSERT, UPDATE o DELETE no reemplaza los comandos de TableAdapter que se utilizan al llamar al método `Update` de TableAdapter.  Por ejemplo, al seleccionar UPDATE como un tipo de consulta, se creará una nueva consulta con el nombre que se especifique después en el asistente.  Esta consulta se ejecuta llamando a este método con nombre de TableAdapter.  Al llamar al método `Update` de TableAdapter, se ejecutarán instrucciones que se crearon cuando se configuró el TableAdapter original.  
  
## Especificar una instrucción SQL \<Query Type\>  
 En la página **Especifique una instrucción SQL.**, escriba la instrucción SQL para que se ejecute al llamar a la consulta.  
  
> [!TIP]
>  El asistente proporciona acceso al **Generador de consultas**, una herramienta visual para crear consultas SQL.  Para abrirlo, haga clic en el botón **Generador de consultas**.  
  
## Elegir los métodos que se van a generar  
 Esta página proporciona las opciones para seleccionar qué métodos genera el asistente para la consulta.  
  
 **Rellenar un DataTable**  
 Crea un método para rellenar la tabla de datos.  El usuario pasa el nombre de la tabla de datos como un parámetro al llamar a este método para llenar la tabla de datos con los datos devueltos.  
  
 También puede cambiar el nombre predeterminado en el cuadro **Nombre de método**.  Proporcionar un nombre descriptivo puede ser útil al trabajar con esta consulta en código.  
  
 **Devolver un DataTable**  
 Crea un método para devolver una tabla de datos llena.  En ciertas aplicaciones, puede ser más atractivo devolver una tabla de datos llena a diferencia de llenar con datos la existente.  
  
 También puede cambiar el nombre predeterminado en el cuadro **Nombre de método**.  
  
## Elegir un nombre de función  
 Escriba un nombre para la función.  Al crear una consulta de TableAdapter, se agrega un método a TableAdapter con el nombre que se proporcionó aquí.  Llame a este método para ejecutar la consulta.  Proporcionar un nombre descriptivo es útil al trabajar con esta consulta en código.  
  
> [!NOTE]
>  Al crear nuevos procedimientos almacenados, se le pedirán dos nombres.  El primero es el nombre del procedimiento almacenado creado en la base de datos; el segundo, es el nombre del método en TableAdapter que ejecuta el procedimiento almacenado cuando se le llama.  
  
## Crear nuevos procedimientos almacenados  
 En esta sección se explica cómo finalizar el **Asistente para configuración de consultas de TableAdapter** al seleccionar la opción **Crear nuevos procedimientos almacenados**.  
  
1.  En la página **Generar los procedimientos almacenados**, escriba la instrucción SQL que se va a ejecutar al llamar al procedimiento almacenado.  
  
    > [!NOTE]
    >  El asistente proporciona acceso al **Generador de consultas**, una herramienta visual para crear consultas SQL.  Para abrirlo, haga clic en el botón **Generador de consultas**.  
  
2.  En la página **Crear los procedimientos almacenados**, haga lo siguiente:  
  
    1.  Escriba un nombre para el nuevo procedimiento almacenado.  
  
    2.  Especifique si se crea el procedimiento almacenado en la base de datos subyacente.  
  
        > [!NOTE]
        >  La configuración de seguridad determina la capacidad de crear un procedimiento almacenado en la base de datos para la base de datos concreta.  
  
     En la página **Ver resultados del asistente** se muestran los resultados de la creación de la consulta de TableAdapter.  Si el asistente detecta algún problema, esta pantalla proporciona información del error.  
  
## Usar procedimientos almacenados existentes  
 En esta sección se explica cómo finalizar el **Asistente para configuración de consultas de TableAdapter** al seleccionar la opción **Usar procedimientos almacenados existentes**.  
  
1.  Seleccione un procedimiento almacenado existente a partir de la lista desplegable de la página del asistente **Elija un procedimiento almacenado existente**.  
  
     Aparecen como referencia **Parámetros** y **Resultados** para el procedimiento almacenado seleccionado.  
  
2.  Haga clic en **Siguiente**.  
  
## Elegir la forma de los datos devueltos por el procedimiento almacenado  
 El tipo de datos devuelto por el procedimiento almacenado seleccionado determina cómo el asistente crea los métodos de TableAdapter.  
  
 Seleccione el tipo de datos devuelto por esta consulta.  
  
-   Al seleccionar **Datos tabulares**, se abre la página **Elija los métodos que se van a generar** \(descrita anteriormente en esta página de ayuda\), que permite especificar los tipos de métodos, nombres de método y compatibilidad con la paginación que se van a crear.  
  
-   Al seleccionar **Un valor único**, se crea un método con tipo que devuelve un valor único.  Esta opción abre la página **Elija un nombre de función** \(descrita anteriormente en esta página de ayuda\).  
  
-   Al seleccionar **Sin valor**, se crea un método con tipo que ejecuta el procedimiento almacenado y espera que no se devuelvan datos.  Esta opción abre la página **Elija un nombre de función** \(descrita anteriormente en esta página de ayuda\).  
  
## Ver resultados del asistente  
 En la página **Ver resultados del asistente** se muestran los resultados de la creación de la consulta de TableAdapter.  Si el asistente detecta problemas, los detalles aparecen en esta pantalla.  
  
## Vea también  
 [Información general sobre TableAdapter](../data-tools/tableadapter-overview.md)   
 [Cómo: Editar consultas de TableAdapter](../data-tools/how-to-edit-tableadapter-queries.md)   
 [Tutoriales sobre datos](../Topic/Data%20Walkthroughs.md)   
 [Enlazar controles de Windows Forms a datos en Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [Información general de las aplicaciones de datos en Visual Studio](../data-tools/overview-of-data-applications-in-visual-studio.md)   
 [Conectarse a datos en Visual Studio](../data-tools/connecting-to-data-in-visual-studio.md)   
 [Preparar la aplicación para recibir datos](../Topic/Preparing%20Your%20Application%20to%20Receive%20Data.md)   
 [Buscar datos en la aplicación](../data-tools/fetching-data-into-your-application.md)   
 [Enlazar controles a los datos en Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [Modificar datos en la aplicación](../data-tools/editing-data-in-your-application.md)   
 [Validar datos](../Topic/Validating%20Data.md)   
 [Guardar datos](../data-tools/saving-data.md)