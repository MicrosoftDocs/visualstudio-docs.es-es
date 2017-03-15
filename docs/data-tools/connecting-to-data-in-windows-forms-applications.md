---
title: "Conectar a los datos en aplicaciones de Windows Forms | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "System.Data.SqlClient.SqlConnection"
  - "System.Data.Odbc.OdbcConnection"
  - "System.Data.OleDb.OleDbConnection"
  - "System.Data.OracleClient.OracleConnection"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "aspx"
helpviewer_keywords: 
  - "conectar a bases de datos, conexiones de ADO.NET"
  - "objetos de conexión"
  - "objetos de conexión, herramientas para trabajar"
  - "objetos de conexión, tipos de"
  - "agrupación de conexiones, conexiones de ADO.NET"
  - "cadenas de conexión [Visual Studio], ADO.NET"
  - "conexiones, acerca de las conexiones"
  - "conexiones, en tiempo de diseño"
  - "datos [Visual Studio], conectar"
  - "adaptadores de datos, conexiones"
  - "conexiones de bases de datos [Visual Studio], ADO.NET"
  - "bases de datos [Visual Studio], conectar"
  - "conexiones en tiempo de diseño"
  - "propiedades dinámicas, conexiones de ADO.NET"
  - "OleDbConnection (clase), objetos de conexión de ADO.NET"
  - "SqlConnection (clase), objetos de conexión de ADO.NET"
  - "TableAdapters, conexiones"
  - "transacciones, ADO.NET"
ms.assetid: 184cbd0d-3b26-418d-a11c-f9f8f004fbff
caps.latest.revision: 31
caps.handback.revision: 31
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
robots: noindex,nofollow
---
# Conectar a los datos en aplicaciones de Windows Forms
[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] proporciona herramientas para conectar su aplicación con los datos de muchos orígenes diferentes, tales como bases de datos, servicios web y objetos.  Si usa herramientas de diseño de datos en [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], normalmente no necesitará crear explícitamente un objeto de conexión para su formulario o componente.  El objeto de conexión suele crearse al completar uno de los asistentes para datos o al arrastrar objetos de datos al formulario.  Para conectar su aplicación a los datos de una base de datos, servicio web u objeto, ejecute el [Asistente para la configuración de orígenes de datos](../data-tools/media/data-source-configuration-wizard.png) seleccionando **Agregar nuevo origen de datos** en la [Orígenes de datos \(ventana\)](../Topic/Data%20Sources%20Window.md).  
  
 El diagrama siguiente muestra el flujo estándar de operaciones al conectarse a datos mediante la ejecución de una consulta de TableAdapter para buscar datos y mostrarlos en un formulario de una aplicación de Windows.  
  
 ![Flujo de datos de una aplicación cliente](../data-tools/media/clientdatadiagram.gif "ClientDataDiagram")  
  
 En algunos casos, es conveniente crear un objeto de conexión sin la asistencia de herramientas de diseño de datos.  Para obtener información sobre cómo crear conexiones mediante programación, vea [Conectarse a un origen de datos](../Topic/Connecting%20to%20a%20Data%20Source%20in%20ADO.NET.md).  
  
> [!NOTE]
>  Para obtener más información sobre cómo conectar aplicaciones web a datos, vea [ASP.NET Data Access Content Map](http://msdn.microsoft.com/es-es/f9219396-a0fa-481f-894d-e3d9c67d64f2).  
  
## Tutoriales para conectar aplicaciones de Windows Forms a datos  
 Los siguientes tutoriales proporcionan los procedimientos para conectarse aplicaciones de Windows Forms a datos:  
  
-   [Tutorial: Conectar a los datos en una base de datos \(Windows Forms\)](../Topic/Walkthrough:%20Connecting%20to%20Data%20in%20a%20Database%20\(Windows%20Forms\).md)  
  
-   [Tutorial: Conectar con los datos de un archivo de base de datos local \(Windows Forms\)](../data-tools/walkthrough-connecting-to-data-in-a-local-database-file-windows-forms.md)  
  
-   [Tutorial: Conectar a los datos en un servicio Web \(Windows Forms\)](../Topic/Walkthrough:%20Connecting%20to%20Data%20in%20a%20Web%20Service%20\(Windows%20Forms\).md)  
  
-   [Tutorial: Conectar a los datos en objetos \(Windows Forms\)](../Topic/Walkthrough:%20Connecting%20to%20Data%20in%20Objects%20\(Windows%20Forms\).md)  
  
-   [Tutorial: Conectar a los datos en una base de datos de Access \(Windows Forms\)](../data-tools/connect-to-data-in-an-access-database-windows-forms.md)  
  
## Crear conexiones  
 En [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], las conexiones se configuran con el cuadro de diálogo **Agregar o modificar conexión**.  El cuadro de diálogo **Agregar conexión** se muestra cuando se editan o se crean conexiones dentro de uno de los asistentes para datos o del [Explorador de servidores\/Explorador de bases de datos](../Topic/Server%20Explorer.md) o cuando se editan las propiedades de la conexión en la ventana **Propiedades**.  
  
 Las conexiones de datos se configuran automáticamente cuando se realiza una de las siguientes acciones.  
  
|Acción|Descripción|  
|------------|-----------------|  
|Ejecute el [Asistente para la configuración de orígenes de datos](../data-tools/media/data-source-configuration-wizard.png).|Las conexiones se configuran cuando se elige la ruta de acceso a la base de datos en el **Asistente para configuración de orígenes de datos**.  Para obtener más información, vea [Cómo: Conectarse a los datos de una base de datos](../data-tools/how-to-connect-to-data-in-a-database.md).|  
|Ejecute el [Asistente para la configuración de TableAdapter](../Topic/TableAdapter%20Configuration%20Wizard.md).|Las conexiones se crean en el **Asistente para configuración de TableAdapter**.  Para obtener más información, vea [Cómo: Crear TableAdapters](../data-tools/create-and-configure-tableadapters.md).|  
|Ejecute el [Asistente para la configuración de consultas de TableAdapter](../data-tools/editing-tableadapters.md).|Las conexiones se crean en el **Asistente para configuración de consultas de TableAdapter**.  Para obtener más información, vea [Cómo: Crear consultas de TableAdapter](../data-tools/how-to-create-tableadapter-queries.md).|  
|Arrastre elementos desde la [Orígenes de datos \(ventana\)](../Topic/Data%20Sources%20Window.md) a un formulario o al [Component Designer](../Topic/Component%20Designer.md).|Los objetos de conexión se crean al arrastrar elementos desde la ventana **Orígenes de datos** al **Diseñador de Windows Forms** o **Diseñador de componentes**.  Para obtener más información, vea [Enlazar controles a los datos en Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md).|  
|Agregue nuevas conexiones de datos al [Explorador de servidores\/Explorador de bases de datos](../Topic/Server%20Explorer.md).|En el **Explorador de servidores\/Explorador de bases de datos**, las conexiones de datos se muestran en la lista de conexiones disponibles, dentro de los asistentes para datos.|  
  
## Cadenas de conexión  
 Las cadenas de conexión se pueden almacenar dentro de la aplicación compilada o en el archivo de configuración de la aplicación.  Para obtener más información, vea [Cómo: Guardar y editar cadenas de conexión](../Topic/How%20to:%20Save%20and%20Edit%20Connection%20Strings.md).  
  
## Información de la conexión y seguridad  
 Como abrir una conexión implica obtener acceso a un recurso importante \(una base de datos\), configurar y trabajar con una conexión implica algunos aspectos en cuanto a la seguridad.  
  
 La manera de proteger la aplicación y su acceso al origen de datos depende de la arquitectura del sistema.  En una aplicación web, por ejemplo, los usuarios suelen acceder anónimamente a Internet Information Services \(IIS\) y, por lo tanto, no proporcionan credenciales de seguridad.  En ese caso, su aplicación mantiene su propia información de inicio de sesión y la usa, en lugar de una información de usuario específica, para abrir la conexión y acceder a la base de datos.  
  
> [!IMPORTANT]
>  Guardar detalles de la cadena de conexión \(como la contraseña\) puede afectar a la seguridad de la aplicación.  El uso de la seguridad integrada de Windows es una forma más segura de controlar el acceso a una base de datos.  Para obtener más información, vea [Proteger la información de conexión](../Topic/Protecting%20Connection%20Information.md).  
  
 En aplicaciones de intranet o de varios niveles, puede aprovechar las ventajas de la opción de seguridad integrada que proporcionan Windows, IIS y SQL Server.  En ese modelo, las credenciales de autenticación de un usuario para la red local también se usan para acceder a los recursos de base de datos y no se usa ningún nombre de usuario o contraseña específicos en la cadena de conexión.  Normalmente, los permisos se establecen en el equipo servidor de base de datos mediante grupos, para que no tenga que establecer permisos individuales para cada usuario que pudiera acceder a la base de datos.  En este modelo, no necesita almacenar la información de inicio de sesión para la conexión y no se requieren pasos adicionales para proteger la información de la cadena de conexión.  
  
 Para obtener más información sobre seguridad, vea los temas siguientes:  
  
-   [Proteger aplicaciones de ADO.NET](../Topic/Securing%20ADO.NET%20Applications.md)  
  
-   [More Secure File and Data Access in Windows Forms](../Topic/More%20Secure%20File%20and%20Data%20Access%20in%20Windows%20Forms.md)  
  
## Conexiones en tiempo de diseño en el Explorador de servidores\/Explorador de bases de datos  
 El **Explorador de servidores\/Explorador de bases de datos** permite crear conexiones en tiempo de diseño a orígenes de datos.  Esto permite examinar los orígenes de datos disponibles, mostrar información sobre las tablas, columnas y otros elementos que contienen, y editar y crear elementos de base de datos.  
  
 La aplicación no usa directamente las conexiones disponibles en el **Explorador de servidores\/Explorador de bases de datos**.  [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] usa estas conexiones para trabajar con la base de datos en tiempo de diseño.  Para obtener más información, vea [Visual Database Tools](http://msdn.microsoft.com/es-es/6b145922-2f00-47db-befc-bf351b4809a1).  
  
 Por ejemplo, en tiempo de diseño podría usar el **Explorador de servidores\/Explorador de bases de datos** para crear una conexión a una base de datos.  Después, cuando diseñe un formulario, puede examinar la base de datos, seleccionar columnas de una tabla y arrastrarlas al [Diseñador de Dataset](../data-tools/creating-and-editing-typed-datasets.md).  Esto crea un [TableAdapter](../data-tools/tableadapter-overview.md) en su conjunto de datos.  También crea un nuevo objeto de conexión, que forma parte del TableAdapter recién creado.  
  
 La información sobre las conexiones en tiempo de diseño se almacenan en el equipo local independientemente de un proyecto o solución específicos.  Por lo tanto, una vez establecida una conexión en tiempo de diseño mientras trabaja en una aplicación, aparece en el **Explorador de servidores\/Explorador de bases de datos** siempre que trabaje en [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], mientras el servidor al que apunta la conexión esté disponible.  Para obtener más información, vea [How to: Connect to a Database from Server Explorer](http://msdn.microsoft.com/es-es/7c1c3067-0d77-471b-872b-639f9f50db74).  
  
 [!INCLUDE[SQLObjectExplorer](../data-tools/includes/sqlobjectexplorer_md.md)]  
  
## Vea también  
 [Conectarse a datos en Visual Studio](../data-tools/connecting-to-data-in-visual-studio.md)   
 [Cómo: Conectarse a los datos de una base de datos](../data-tools/how-to-connect-to-data-in-a-database.md)   
 [Tutorial: Conectar a los datos en una base de datos \(Windows Forms\)](../Topic/Walkthrough:%20Connecting%20to%20Data%20in%20a%20Database%20\(Windows%20Forms\).md)   
 [ASP.NET Data Access Content Map](http://msdn.microsoft.com/es-es/f9219396-a0fa-481f-894d-e3d9c67d64f2)   
 [Preparar la aplicación para recibir datos](../Topic/Preparing%20Your%20Application%20to%20Receive%20Data.md)   
 [Buscar datos en la aplicación](../data-tools/fetching-data-into-your-application.md)   
 [Enlazar controles a los datos en Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [Modificar datos en la aplicación](../data-tools/editing-data-in-your-application.md)   
 [Validar datos](../Topic/Validating%20Data.md)   
 [Guardar datos](../data-tools/saving-data.md)