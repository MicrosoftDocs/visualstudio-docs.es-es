---
title: Información general sobre los datos locales | Documentos de Microsoft
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
- SQL Server Express
- local data
- SQL Server LocalDB
- LocalDB
- SQLEXPRESS
- SQL Server, local data
- SQL Express
- SQL Server Compact
- data access [Visual Studio], troubleshooting
- Access, .mdb files in Visual Studio
- data [Visual Studio], local
ms.assetid: d6afa5ac-2bb8-49f2-a50e-f71f611ed506
caps.latest.revision: 71
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: 94b3f066a66a380875609b4f6485d56a19ebde3e
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49885582"
---
# <a name="local-data-overview"></a>Información general de datos locales
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Al desarrollar aplicaciones de datos, es preferible utilizar una copia local de una base de datos, para que no presentan errores en los datos de producción. Incluso compartir una base de datos de prueba con otros desarrolladores crea posibles problemas si dos desarrolladores producir errores que interactúan de formas difíciles de detectar. Puede evitar todos estos problemas mediante el uso de sus propios datos de prueba en su propio equipo local. La mayoría, si no todos los sistemas de base de datos permiten crear archivos de datos locales. Para los proyectos. NET, Visual Studio proporciona compatibilidad especial para los archivos de base de datos de SQL Server locales (.mdf) y archivos de base de datos de Microsoft Access (.mdb).  
  
 Visual Studio admite estos escenarios:  
  
1.  
  
2.  
  
- 
  
- 
  
- Crear un proyecto de base de datos de SQL Server, al hacer clic en el nodo de la solución en el Explorador de soluciones y elija **agregar &#124; nuevo proyecto**.  En el panel izquierdo, elija **SQL Server &#124; base de datos** del proyecto y haga clic en Aceptar. En el Explorador de soluciones, haga clic con el botón derecho en el nodo de proyecto de base de datos para importar un archivo de base de datos local y luego desarrollar la aplicación que se conecta a la base de datos generado por el proyecto. Es útil cuando se desarrolla y modificación del esquema de base de datos al mismo tiempo que está desarrollando la aplicación.  
  
   ![Importar base de datos en el proyecto de base de datos](../data-tools/media/raddata-import-database-into-database-project.png "raddata Importar base de datos en el proyecto de base de datos")  
  
- Si va a crear una nueva base de datos, primero agregue un **el archivo de base de datos basada en servicio** al proyecto (**proyecto &#124; Agregar nuevo elemento)**. Esto crea un nuevo archivo .mdf que está asociado a la instancia de SQL Server de forma predeterminada en el equipo local, cuyo valor predeterminado es \MSSQLocalDB (localdb). La base de datos debe aparecer en el Explorador de servidores. Expanda el nodo y haga doble clic en los nodos para agregar nuevos objetos de base de datos como tablas, vistas, funciones y así sucesivamente.  
  
  Para obtener más información acerca de SQL Server Express LocalDB, vea [Introducing LocalDB, SQL Express mejorado](http://go.microsoft.com/fwlink/?LinkId=234375) y [LocalDB: Where is My Database?](http://go.microsoft.com/fwlink/?LinkId=234376) en el sitio Web de Microsoft.  
  
  La tabla siguiente proporciona vínculos a temas que describen cómo conectar la aplicación a datos locales:  
  
|Tema|Descripción|  
|-----------|-----------------|  
|[Crear una base de datos SQL mediante un diseñador](../data-tools/create-a-sql-database-by-using-a-designer.md)|Proporciona instrucciones paso a paso para crear un archivo de base de datos local que se puede usar para probar las características de datos y crear aplicaciones.|  
|[Tutorial: Conectar con los datos de un archivo de base de datos local (Windows Forms)](../data-tools/walkthrough-connecting-to-data-in-a-local-database-file-windows-forms.md)|Proporciona instrucciones paso a paso para conectar con una base de datos de SQL Server Express LocalDB cuando se crea una aplicación Windows simple.|  
|[Conectar a los datos en una base de datos de Access (Windows Forms)](../data-tools/connect-to-data-in-an-access-database-windows-forms.md)|Proporciona instrucciones paso a paso para la conexión con una base de datos de Microsoft Access.|  
|[Cómo: Conectar con la base de datos Northwind](../data-tools/how-to-connect-to-the-northwind-database.md)|Proporciona instrucciones para conectar con la base de datos de ejemplo Northwind en [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], SQL Server Compact, SQL Server Express y Access.|  
  
## <a name="use-the-connection-string"></a>Utilice la cadena de conexión  
 Este es el enfoque más sencillo y es una buena elección cuando la aplicación solo lee desde la base de datos y al usar bases de datos de terceros. El archivo de base de datos puede encontrarse en cualquier lugar en el equipo local que la aplicación tiene permiso para acceder y que admite el sistema de base de datos.  
  
1.  (Opcional) Crear una nueva conexión, como se describe en [agregar nuevas conexiones](../data-tools/add-new-connections.md). Para las bases de datos de otros fabricantes y los archivos .mdf para el que ya conoce la cadena de conexión y no se realiza el enlace de datos o utilizando un origen de datos como clases de Entity Framework o conjuntos de datos, este paso no es necesario. Usar la cadena de conexión para conectarse al archivo local. Los archivos .mdf, vea [actualizar archivos .mdf](../data-tools/upgrade-dot-mdf-files.md) y [establecer la conexión](https://msdn.microsoft.com/en-us/library/ms254507.aspx).  
  
2.  (Opcional) Si usa conjuntos de datos, Entity Framework o LINQ to SQL, crear, a continuación, el origen de datos mediante el Asistente para configuración de orígenes de datos. Para obtener más información, vea [Agregar nuevos orígenes de datos](../data-tools/add-new-data-sources.md).  
  
## <a name="add-an-existing-mdf-to-your-project"></a>Agregar un .mdf existente al proyecto  
 Si la aplicación se pueden insertar, eliminar o actualizar datos y desea conservar una copia del archivo original disponible, considere la posibilidad de agregar el archivo al proyecto. Al hacerlo, puede establecer la propiedad del elemento en él para **Copy to Output Directory** a **copiar siempre** o **copiar si es posterior**y desarrollar la aplicación. Cada vez que compile la aplicación, la base de datos original se copia en la carpeta de salida y los cambios de la aplicación se realizan en la copia. De este modo siempre tienen una copia limpia de los datos originales.  
  
1.  Use **Explorador de archivos de Windows** para arrastrar y colocar el archivo .mdf desde su ubicación actual en el nodo del proyecto en el Explorador de soluciones en Visual Studio.  Si el archivo ya está asociado a una instancia de localDB, desconéctelo primero. Después de colocarlo en el proyecto, Visual Studio se reasociará automáticamente a la instancia localDB predeterminada.  
  
2.  Haga doble clic en el nuevo nodo de base de datos y elija Propiedades. Seleccione el comportamiento de copia, bien **copiar siempre** o **copiar si es posterior**.  
  
## <a name="create-a-sql-server-database-project-and-import-your-database"></a>Crear un proyecto de base de datos de SQL Server e importar la base de datos  
 Esto es una buena opción si va a desarrollar la base de datos, quizás agregando columnas o tablas, o cambiando los tipos de datos.  
  
## <a name="each-project-contains-two-copies-of-the-database"></a>Cada proyecto contiene dos copias de la base de datos  
 Cuando compila un proyecto, el archivo de base de datos podría copiarse de la carpeta raíz del proyecto en la salida, **bin**, carpeta. Este comportamiento depende del **Copy to Output Directory** propiedad del archivo y el valor predeterminado de esa propiedad dependen del tipo de archivo de base de datos que esté usando.  
  
 Para ver el **bin** carpeta **el Explorador de soluciones**, elija el **mostrar todos los archivos** en la barra de herramientas.  
  
> [!NOTE]
>  El **Copy to Output Directory** propiedad no se aplica a proyectos web o C++.  
  
 El archivo de base de datos en la carpeta raíz del proyecto se cambia únicamente cuando se edición el esquema de base de datos o los datos mediante el uso de **Explorador de servidores**/**Database Explorer** u otros [Visual Herramientas de base de datos](http://msdn.microsoft.com/en-us/6b145922-2f00-47db-befc-bf351b4809a1).  
  
 A medida que cambian datos durante el desarrollo de aplicaciones, que está cambiando la base de datos en el **bin** carpeta. Por ejemplo, si elige la tecla F5 para depurar la aplicación, se conectará a la base de datos de esa carpeta.  
  
|Valor de **Copy to Output Directory** propiedad|Comportamiento|  
|----------------------------------------------------|--------------|  
|**Copiar si es posterior** (valor predeterminado para los archivos .sdf)|El archivo de base de datos se copia desde el directorio de proyecto para el **bin** directorio la primera vez que se compila el proyecto. El **fecha de modificación** propiedad de los archivos, a continuación, se compara cada vez que se compila el proyecto nuevo. Si el archivo en la carpeta del proyecto es más reciente, se copia en el **bin** carpeta, reemplace el archivo anterior. De lo contrario, no se copia ningún archivo. **Precaución:** no se recomienda este valor para los archivos .mdb o .mdf. El archivo de base de datos puede cambiar aunque los datos no cambien. El archivo se puede marcar como más reciente con solo abrir una conexión (por ejemplo, expanda el **tablas** nodo **Explorador de servidores**).|  
|**Copiar siempre** (valor predeterminado para los archivos .mdf y .mdb)|El archivo de base de datos se copia desde el directorio de proyecto para el **bin** directory cada vez que compila la aplicación. Cualquier cambio realizado en el archivo de datos de la carpeta de resultados se sobrescribirá la próxima vez que se ejecute la aplicación.|  
|**No copiar**|El sistema nunca sobrescribe el archivo en el **bin** directory. La aplicación crea una cadena de conexión dinámica que señala al archivo de base de datos en el directorio de salida. Por consiguiente, debe copiar manualmente el archivo en el directorio de salida si desea que los datos del directorio de salida coincidan con los datos del directorio de proyecto.|  
  
## <a name="common-issues-with-local-data"></a>Problemas comunes con los datos locales  
 La tabla siguiente explica problemas comunes que puede encontrar cuando trabaje con archivos de datos locales.  
  
|Problema|Explicación|  
|-----------|-----------------|  
|Cada vez que pruebo mi aplicación y modifico datos, mis cambios no aparecen la próxima vez que ejecuto mi aplicación.|El valor de la **Copy to Output Directory** propiedad es **copiar si es posterior** o **copiar siempre**. La base de datos de la carpeta de salida (la base de datos que se modifica al probar la aplicación) se sobrescribe cada vez que se compila el proyecto. Para obtener más información, consulte [Cómo: administrar archivos de datos locales en el proyecto](../data-tools/how-to-manage-local-data-files-in-your-project.md).|  
|Aparece un mensaje que indica que el archivo de datos está bloqueado.|Access (archivos .mdb): compruebe que el archivo no está abierto en otro programa, tal como Access.<br /><br /> SQL Server Express (archivos .mdf): SQL Express bloquea el archivo de datos si se intenta copiar, mover o cambiar su nombre fuera del IDE de Visual Studio.|  
|El acceso se deniega cuando más de un usuario intentan obtener acceso a la misma base de datos simultáneamente.|Visual Studio aprovecha *las instancias de usuario*, que es una característica de SQL Server Express que crea una instancia independiente de SQL Server para cada usuario. Después de que un usuario obtenga acceso al archivo, ningún usuario posterior puede conectar. Este problema puede ocurrir, por ejemplo, si intenta ejecutar una aplicación web en el servidor de desarrollo de ASP.NET y en IIS a la vez, ya que generalmente IIS se ejecuta con una cuenta diferente.|  
  
## <a name="see-also"></a>Vea también  
 [Tutorial: Conectarse a datos en un archivo de base de datos Local (formularios Windows Forms)](../data-tools/walkthrough-connecting-to-data-in-a-local-database-file-windows-forms.md)   
 [Conectar a los datos en una base de datos de Access (Windows Forms)](../data-tools/connect-to-data-in-an-access-database-windows-forms.md)