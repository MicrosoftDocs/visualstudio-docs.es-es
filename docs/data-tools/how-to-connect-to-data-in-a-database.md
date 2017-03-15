---
title: "C&#243;mo: Conectarse a los datos de una base de datos | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "aspx"
helpviewer_keywords: 
  - "datos [Visual Studio], conectar a bases de datos"
  - "orígenes de datos, crear"
  - "orígenes de datos, bases de datos"
  - "conexiones de bases de datos"
  - "bases de datos, conectar"
ms.assetid: 6c56e54e-8834-4297-85aa-cc1a443ba556
caps.latest.revision: 55
caps.handback.revision: 55
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
robots: noindex,nofollow
---
# C&#243;mo: Conectarse a los datos de una base de datos
Puede utilizar Visual Studio para conectar una aplicación con una base de datos.  Después de crear la conexión de datos, Visual Studio genera un modelo de datos que su aplicación utiliza para interactuar con los datos de la base de datos.  Los objetos del modelo de datos aparecen en la [Orígenes de datos \(ventana\)](../Topic/Data%20Sources%20Window.md).  Después puede crear controles enlazados a datos arrastrando elementos de la ventana **Orígenes de datos** a la superficie de diseño.  Para obtener más información, vea [Enlazar controles a los datos en Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md).  
  
 En este tema se proporcionan las instrucciones para conectarse a una base de datos y crear los siguientes tipos de modelos de datos:  
  
-   Conjunto de datos  
  
-   Entity Data Model \(EDM\)  
  
> [!NOTE]
>  También puede utilizar Visual Studio para crear las clases LINQ to SQL a partir de una base de datos.  Sin embargo, las clases LINQ to SQL no aparecen en la ventana **Orígenes de datos** y, por consiguiente, no se pueden arrastrar directamente a un diseñador para crear controles enlazados a datos.  Para obtener más información sobre cómo crear las clases LINQ to SQL a partir de una base de datos, vea [Cómo: Crear clases de LINQ to SQL asignadas a tablas y vistas \(Object Relational Designer\)](../data-tools/how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md).  
  
 [!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
##  <a name="dataset"></a> Conectarse a una base de datos y crear un conjunto de datos  
 Al crear un conjunto de datos basado en una base de datos, Visual Studio crea un conjunto de clases que representan una vista programable de los datos.  La clase principal se denomina *conjunto de datos con tipo*.  El conjunto de datos con tipo contiene objetos de tabla de datos que representan las tablas en la base de datos.  Para obtener más información sobre los conjuntos de datos con tipo, vea [Trabajar con los conjuntos de datos en Visual Studio](../data-tools/dataset-tools-in-visual-studio.md).  
  
 Después de crear un conjunto de datos, puede crear controles Windows Forms o WPF enlazados a datos arrastrando los objetos del conjunto de datos de la ventana Orígenes de datos al diseñador de Windows Forms o de WPF.  
  
#### Para conectar la aplicación a una base de datos y crear un conjunto de datos  
  
1.  Abra un proyecto existente en Visual Studio o cree un nuevo proyecto.  
  
2.  En el menú **Datos**, haga clic en **Agregar nuevo elemento**.  
  
     Se abrirá el **Asistente para la configuración de orígenes de datos**.  
  
3.  En la página **Elegir un tipo de origen de datos**, seleccione **Base de datos** y, a continuación, haga clic en **Siguiente**.  
  
4.  En la página **Elegir un modelo de base de datos**, seleccione **Conjunto de datos** y, a continuación, haga clic en **Siguiente**.  
  
5.  Seleccione una conexión de datos de la lista de conexiones disponible en la página **Elegir la conexión de datos** y haga clic en **Siguiente**.  
  
     Si la conexión de datos deseada no está disponible, cree una nueva siguiendo los pasos para [Crear una nueva conexión a bases de datos](#CreatingDataConnection).  
  
6.  En la página **Guardar cadena de conexión en el archivo de config. de la aplicación**, opcionalmente desactive la casilla **Sí, guardar la conexión como** si desea guardar la cadena de conexión en la aplicación de compilación directamente.  De forma predeterminada, la conexión se guarda en el archivo de configuración de la aplicación.  Para obtener más información, vea [Cómo: Guardar y editar cadenas de conexión](../Topic/How%20to:%20Save%20and%20Edit%20Connection%20Strings.md).  
  
7.  En la página **Elija los objetos de base de datos**, seleccione los objetos de base de datos que utilizará en la aplicación.  También tiene la opción de reemplazar el **Nombre de DataSet** predeterminado.  
  
8.  Haga clic en **Finalizar**.  El conjunto de datos que acaba de crear estará disponible en la ventana **Orígenes de datos**.  
  
    > [!NOTE]
    >  Si la ventana **Orígenes de datos** no está abierta, haga clic en **Mostrar orígenes de datos** en el menú **Datos** para abrirla.  
  
9. Ahora puede arrastrar los elementos de la ventana **Orígenes de datos** al diseñador WPF, el diseñador de Windows Forms o [Component Designer](../Topic/Component%20Designer.md) para crear controles enlazados a datos.  Para obtener más información, vea [Enlazar controles a los datos en Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md).  
  
##  <a name="edm"></a> Conectarse a una base de datos y crear un Entity Data Model  
 Al crear un Entity Data Model basado en una base de datos, Visual Studio crea un conjunto de clases que representan una vista programable de los datos.  Para obtener más información sobre Entity Data Models y ADO.NET Entity Framework, vea [Información general de Entity Framework](../Topic/Entity%20Framework%20Overview.md).  
  
 Después de crear un Entity Data Model, puede crear los controles WPF enlazados a datos arrastrando los objetos entidad de la ventana Orígenes de datos al diseñador WPF.  
  
#### Para conectar la aplicación a una base de datos y crear un Entity Data Model  
  
1.  Abra un proyecto existente en Visual Studio o cree un nuevo proyecto.  
  
2.  Siga los pasos del **Asistente de Entity Data Model** para conectarse a una base de datos y especificar el contenido del modelo.  Para obtener más información, vea [How to: Create a New .edmx File](http://msdn.microsoft.com/es-es/beb8189e-e51c-4051-839c-9902c224abf2).  
  
3.  Después de completar el **Asistente de Entity Data Model**, el Entity Data Model que creó se abre en el Diseñador de Entity Data Model y los objetos de datos están ahora disponibles en la ventana **Orígenes de datos**.  
  
    > [!NOTE]
    >  Si la ventana **Orígenes de datos** no está abierta, haga clic en **Mostrar orígenes de datos** en el menú **Datos** para abrirla.  
  
4.  Si el diseñador WPF está abierto, puede arrastrar los elementos de la ventana **Orígenes de datos** al diseñador para crear controles que se enlazan al Entity Data Model.  Para obtener más información, vea [Cómo: Enlazar controles WPF a datos en Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio2.md).  
  
     Si el diseñador de Windows Forms está abierto, no puede arrastrar los elementos de **Orígenes de datos** al diseñador.  Para crear controles que se enlazan al Entity Data Model, debe compilar el proyecto, agregar un nuevo origen de datos de objeto basado en el Entity Data Model y, a continuación, arrastrar esos objetos al diseñador.  
  
##  <a name="CreatingDataConnection"></a> Crear una nueva conexión de base de datos  
 Cuando utilice el **Asistente para la configuración de orígenes de datos** o el **Asistente de Entity Data Model**, debe especificar una conexión a la base de datos que desea utilizar.  Si aún no tiene una conexión, siga estos pasos para crearla.  
  
 Estas instrucciones suponen que ya ha iniciado el **Asistente para la configuración de orígenes de datos** o el **Asistente de Entity Data Model** como se describe en [Conectar a una base de datos y crear un conjunto de datos](#dataset) y [Conectarse a una base de datos y crear un Entity Data Model](#edm).  
  
#### Para crear una nueva conexión a una base de datos  
  
1.  En la página **Elegir la conexión de datos** del **Asistente para la configuración de orígenes de datos** o del **Asistente de Entity Data Model**, haga clic en **Nueva conexión**.  
  
     Se produce una de las acciones siguientes:  
  
    -   Si ya ha creado una conexión de datos en Visual Studio, el cuadro de diálogo **Agregar conexión** se abre.  
  
    -   Si se trata de la primera conexión de datos que crea en Visual Studio, se muestra el cuadro de diálogo **Elegir origen de datos**.  Seleccione el tipo de base de datos con el que desea conectarse y, a continuación, haga clic en **Aceptar** para mostrar el cuadro de diálogo **Agregar conexión**.  
  
2.  En el cuadro de diálogo **Agregar conexión**, escriba la información solicitada.  El cuadro de diálogo **Agregar conexión** es diferente para cada tipo de proveedor de datos.  
  
    > [!NOTE]
    >  Si el **Origen de datos** seleccionado en el cuadro de diálogo **Agregar conexión** no es al que desea conectarse, haga clic en **Cambiar** para abrir el cuadro de diálogo **Cambiar origen de datos** y elegir un origen de datos diferente.  
  
3.  Haga clic en **Aceptar** en el cuadro de diálogo **Agregar conexión**.  
  
     Vuelve a la página **Elegir la conexión de datos** del **Asistente para la configuración de orígenes de datos** o el **Asistente de Entity Data Model**.  
  
4.  En la página **Elegir la conexión de datos** asegúrese de que la nueva conexión de datos está seleccionada y haga clic en **Siguiente**.  
  
5.  Complete los pasos restantes del **Asistente para la configuración de orígenes de datos** o del **Asistente de Entity Data Model**.  
  
## Seguridad de .NET Framework  
 Almacenar información confidencial, como una contraseña, puede afectar la seguridad de la aplicación.  El uso de la autenticación de Windows \(también conocida como seguridad integrada\) es un modo más seguro de controlar el acceso a una base de datos.  Para obtener más información, vea [Proteger la información de conexión](../Topic/Protecting%20Connection%20Information.md).  
  
## Vea también  
 [Información general sobre orígenes de datos](../data-tools/add-new-data-sources.md)   
 [Tutoriales sobre datos](../Topic/Data%20Walkthroughs.md)   
 [Enlazar controles de Windows Forms a datos en Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [Conectarse a datos en Visual Studio](../data-tools/connecting-to-data-in-visual-studio.md)   
 [Conectarse a un origen de datos](../Topic/Connecting%20to%20a%20Data%20Source%20in%20ADO.NET.md)