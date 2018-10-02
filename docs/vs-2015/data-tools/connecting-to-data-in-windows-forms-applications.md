---
title: Las aplicaciones de conexión a datos en Windows Forms | Documentos de Microsoft
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- System.Data.SqlClient.SqlConnection
- System.Data.Odbc.OdbcConnection
- System.Data.OleDb.OleDbConnection
- System.Data.OracleClient.OracleConnection
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- connection objects, tools for working with
- OleDbConnection class, ADO.NET connection objects
- databases [Visual Studio], connecting to
- data adapters, connections
- connection pooling, ADO.NET connections
- connection strings [Visual Studio], ADO.NET
- connection objects, types of
- dynamic properties, ADO.NET connections
- connections, about connections
- data [Visual Studio], connecting
- design-time connections
- connections, design-time
- TableAdapters, connections
- connection objects
- SqlConnection class, ADO.NET connection objects
- connecting to databases, ADO.NET connections
- transactions, ADO.NET
- database connections [Visual Studio], ADO.NET
ms.assetid: 184cbd0d-3b26-418d-a11c-f9f8f004fbff
caps.latest.revision: 31
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: d1132ee07e892886e49fbaa4670b309afc448da6
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47581278"
---
# <a name="connecting-to-data-in-windows-forms-applications"></a>Conectar a los datos en aplicaciones de Windows Forms
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../includes/vsprvs-md.md)] proporciona herramientas para conectar su aplicación con los datos de muchos orígenes diferentes, tales como bases de datos, servicios web y objetos. Si usa herramientas de diseño de datos en [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], normalmente no necesitará crear explícitamente un objeto de conexión para su formulario o componente. El objeto de conexión suele crearse al completar uno de los asistentes para datos o al arrastrar objetos de datos al formulario. Para conectar la aplicación a los datos en una base de datos, un servicio web o un objeto, ejecute el [Asistente para configuración de origen de datos](http://msdn.microsoft.com/library/c4df7de5-5da0-4064-940c-761dd6d9e28f) seleccionando **Agregar nuevo origen de datos** desde el [deventanadeorígenesdedatos](http://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992).  
  
 El diagrama siguiente muestra el flujo estándar de operaciones al conectarse a datos mediante la ejecución de una consulta de TableAdapter para buscar datos y mostrarlos en un formulario de una aplicación de Windows.  
  
 ![Flujo de datos en una aplicación cliente](../data-tools/media/clientdatadiagram.gif "ClientDataDiagram")  
  
 En algunos casos, es conveniente crear un objeto de conexión sin la asistencia de herramientas de diseño de datos. Para obtener información sobre cómo crear conexiones mediante programación, vea [conectarse a un origen de datos](http://msdn.microsoft.com/library/9abc3f92-1be3-4e1a-b360-762dc689650e).  
  
> [!NOTE]
>  Para obtener información sobre cómo conectar aplicaciones web a los datos, vea [mapa de contenido de acceso de datos de ASP.NET](http://msdn.microsoft.com/en-us/f9219396-a0fa-481f-894d-e3d9c67d64f2).  
  
## <a name="walkthroughs-for-connecting-windows-forms-applications-to-data"></a>Tutoriales para conectar aplicaciones de Windows Forms a datos  
 Los siguientes tutoriales proporcionan los procedimientos para conectarse aplicaciones de Windows Forms a datos:  
  
-   [Tutorial: Conectarse a datos en una base de datos (formularios Windows Forms)](http://msdn.microsoft.com/library/02d39aa6-8993-4602-be13-a13536af3d1c)  
  
-   [Tutorial: Conectar con los datos de un archivo de base de datos local (Windows Forms)](../data-tools/walkthrough-connecting-to-data-in-a-local-database-file-windows-forms.md)  
  
-   [Tutorial: Conectarse a datos en un servicio Web (formularios Windows Forms)](http://msdn.microsoft.com/library/079fb9b0-c733-40c1-acd1-d0d68834354d)  
  
-   [Tutorial: Conectar a los datos de objetos (formularios Windows Forms)](http://msdn.microsoft.com/library/21a7fba2-b38b-4726-8cbe-d22154b75a05)  
  
-   [Conectar a los datos en una base de datos de Access (Windows Forms)](../data-tools/connect-to-data-in-an-access-database-windows-forms.md)  
  
## <a name="creating-connections"></a>Crear conexiones  
 En [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], las conexiones se configuran mediante el **agregar o modificar conexión** cuadro de diálogo. El **Agregar conexión** cuadro de diálogo aparece cuando se editan o se crean conexiones dentro de uno de los asistentes de datos o [Server Explorer/Database Explorer](http://msdn.microsoft.com/library/4ea29b3b-bbb2-45e4-9082-eaf635c41c4d) o cuando se editan las propiedades de conexión en el **propiedades** ventana.  
  
 Las conexiones de datos se configuran automáticamente cuando se realiza una de las siguientes acciones.  
  
|Acción|Descripción|  
|------------|-----------------|  
|Ejecute el [Asistente para la configuración del origen de datos](http://msdn.microsoft.com/library/c4df7de5-5da0-4064-940c-761dd6d9e28f).|Las conexiones se configuran cuando se elige la ruta de acceso de la base de datos en el **Asistente para configuración de origen de datos**. Para obtener más información, consulte [Cómo: conectarse a datos en una base de datos](../data-tools/how-to-connect-to-data-in-a-database.md).|  
|Ejecute el [Asistente para configuración de TableAdapter](http://msdn.microsoft.com/library/3a373dd9-7b34-4d3c-a48b-69414512bac8).|Las conexiones se crean dentro de la **TableAdapter Configuration Wizard**. Para obtener más información, consulte [crear y configurar TableAdapters](../data-tools/create-and-configure-tableadapters.md).|  
|Ejecute el [editar TableAdapters](../data-tools/editing-tableadapters.md).|Las conexiones se crean dentro de la **TableAdapter Query Configuration Wizard**. Para obtener más información, consulte [Cómo: crear consultas de TableAdapter](../data-tools/how-to-create-tableadapter-queries.md).|  
|Arrastre elementos desde el [ventana Orígenes de datos](http://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992) hasta un formulario o la [Component Designer](http://msdn.microsoft.com/library/61a3a450-5b15-465e-bd9a-72a6c8c2b282).|Objetos de conexión se crean al arrastrar elementos desde el **orígenes de datos** ventana hasta la **Diseñador de Windows Forms** o **Component Designer**. Para obtener más información, consulte [enlazar controles a datos en Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md).|  
|Agregar nuevas conexiones de datos a [Server Explorer/Database Explorer](http://msdn.microsoft.com/library/4ea29b3b-bbb2-45e4-9082-eaf635c41c4d).|Conexiones de datos en **Server Explorer/Database Explorer** aparecen en la lista de conexiones disponibles dentro de los asistentes para datos|  
  
## <a name="connection-strings"></a>Cadenas de conexión  
 Las cadenas de conexión se pueden almacenar dentro de la aplicación compilada o en el archivo de configuración de la aplicación. Para obtener más información, consulte [Cómo: guardar y editar las cadenas de conexión](~/E:/Repos/visualstudio-docs-pr/docs/data-tools/how-to-save-and-edit-connection-strings.md).  
  
## <a name="connection-information-and-security"></a>Información de la conexión y seguridad  
 Como abrir una conexión implica obtener acceso a un recurso importante (una base de datos), configurar y trabajar con una conexión implica algunos aspectos en cuanto a la seguridad.  
  
 La manera de proteger la aplicación y su acceso al origen de datos depende de la arquitectura del sistema. En una aplicación web, por ejemplo, los usuarios suelen acceder anónimamente a Internet Information Services (IIS) y, por lo tanto, no proporcionan credenciales de seguridad. En ese caso, su aplicación mantiene su propia información de inicio de sesión y la usa, en lugar de una información de usuario específica, para abrir la conexión y acceder a la base de datos.  
  
> [!IMPORTANT]
>  Guardar detalles de la cadena de conexión (como la contraseña) puede afectar a la seguridad de la aplicación. El uso de la seguridad integrada de Windows es una forma más segura de controlar el acceso a una base de datos. Para más información, consulte [Proteger la información de conexión](http://msdn.microsoft.com/library/1471f580-bcd4-4046-bdaf-d2541ecda2f4).  
  
 En aplicaciones de intranet o de varios niveles, puede aprovechar las ventajas de la opción de seguridad integrada que proporcionan Windows, IIS y SQL Server. En ese modelo, las credenciales de autenticación de un usuario para la red local también se usan para acceder a los recursos de base de datos y no se usa ningún nombre de usuario o contraseña específicos en la cadena de conexión. Normalmente, los permisos se establecen en el equipo servidor de base de datos mediante grupos, para que no tenga que establecer permisos individuales para cada usuario que pudiera acceder a la base de datos. En este modelo, no necesita almacenar la información de inicio de sesión para la conexión y no se requieren pasos adicionales para proteger la información de la cadena de conexión.  
  
 Para obtener más información sobre seguridad, vea los temas siguientes:  
  
-   [Proteger aplicaciones de ADO.NET](http://msdn.microsoft.com/library/005a1d43-6ee5-471e-ad98-1d30a44d49d5)  
  
-   [Acceso más seguro a archivos y datos en Windows Forms](http://msdn.microsoft.com/library/3cd3e55b-2f5e-40dd-835d-f50f7ce08967)  
  
## <a name="design-time-connections-in-server-explorerdatabase-explorer"></a>Conexiones en tiempo de diseño en el Explorador de servidores/Explorador de bases de datos  
 **Server Explorer/Database Explorer** proporciona una manera de crear conexiones a orígenes de datos en tiempo de diseño. Esto permite examinar los orígenes de datos disponibles, mostrar información sobre las tablas, columnas y otros elementos que contienen, y editar y crear elementos de base de datos.  
  
 La aplicación no usa directamente las conexiones disponibles en **Server Explorer/Database Explorer**. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] usa estas conexiones para trabajar con la base de datos en tiempo de diseño. Para obtener más información, consulte [Visual Database Tools](http://msdn.microsoft.com/en-us/6b145922-2f00-47db-befc-bf351b4809a1).  
  
 Por ejemplo, en tiempo de diseño podría usar **Server Explorer/Database Explorer** para crear una conexión a una base de datos. Más adelante, al diseñar un formulario, puede examinar la base de datos, seleccionar columnas de una tabla y arrastrarlas el [Diseñador de Dataset](../data-tools/creating-and-editing-typed-datasets.md). Esto crea un [TableAdapter](../data-tools/tableadapter-overview.md) del conjunto de datos. También crea un nuevo objeto de conexión, que forma parte del TableAdapter recién creado.  
  
 La información sobre las conexiones en tiempo de diseño se almacenan en el equipo local independientemente de un proyecto o solución específicos. Por lo tanto, una vez que haya establecido una conexión en tiempo de diseño mientras trabaja en una aplicación, aparece en **Server Explorer/Database Explorer** siempre que trabaje en [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], siempre que el servidor al que la conexión puntos está disponible. Para obtener más información, consulte [Cómo: conectarse a una base de datos desde el Explorador de servidores](http://msdn.microsoft.com/en-us/7c1c3067-0d77-471b-872b-639f9f50db74).  
  
 [!INCLUDE[SQLObjectExplorer](../includes/sqlobjectexplorer-md.md)]  
  
## <a name="see-also"></a>Vea también  
 [Conectarse a datos en Visual Studio](../data-tools/connecting-to-data-in-visual-studio.md)   
 [Cómo: Conectarse a los datos de una base de datos](../data-tools/how-to-connect-to-data-in-a-database.md)   
 [Tutorial: Conectarse a datos en una base de datos (formularios Windows Forms)](http://msdn.microsoft.com/library/02d39aa6-8993-4602-be13-a13536af3d1c)   
 [Mapa de contenido de acceso de datos de ASP.NET](http://msdn.microsoft.com/en-us/f9219396-a0fa-481f-894d-e3d9c67d64f2)   
 [Preparar su aplicación para recibir datos](http://msdn.microsoft.com/library/c17bdb7e-c234-4f2f-9582-5e55c27356ad)   
 [Captura de datos en la aplicación](../data-tools/fetching-data-into-your-application.md)   
 [Enlazar controles a los datos en Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [Edición de datos en la aplicación](../data-tools/editing-data-in-your-application.md)   
 [Validación de datos](http://msdn.microsoft.com/library/b3a9ee4e-5d4d-4411-9c56-c811f2b4ee7e)   
 [Guardar datos](../data-tools/saving-data.md)