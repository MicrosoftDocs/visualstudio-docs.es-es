---
title: "Informaci&#243;n general de datos locales | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
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
  - "Access, archivos .mdb en Visual Studio"
  - "datos [Visual Studio], locales"
  - "acceso a datos [Visual Studio], solucionar problemas"
  - "datos locales"
  - "LocalDB"
  - "SQL Express"
  - "SQL Server Compact"
  - "SQL Server Express"
  - "SQL Server LocalDB"
  - "SQL Server, datos locales"
  - "SQLEXPRESS"
ms.assetid: d6afa5ac-2bb8-49f2-a50e-f71f611ed506
caps.latest.revision: 71
caps.handback.revision: 66
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
robots: noindex,nofollow
---
# Informaci&#243;n general de datos locales
Cuando utilice datos locales, conecte la aplicación a un archivo de base de datos en el equipo local, en lugar de conectarla a una base de datos en un servidor diferente.  Por ejemplo, puede conectar una aplicación que esté desarrollando en Visual Studio a los siguientes archivos de la base de datos local:  
  
-   Archivos de base de datos de SQL Server Express LocalDB \(.mdf\)  
  
-   Archivos de base de datos de SQL Server Express \(.mdf\)  
  
-   Archivos de base de datos de Microsoft Access \(.mdb\)  
  
 La tabla siguiente proporciona vínculos a temas que describen cómo conectar la aplicación a datos locales:  
  
|Tema|Descripción|  
|----------|-----------------|  
|[Tutorial: Crear un archivo de base de datos local en Visual Studio](../data-tools/create-a-sql-database-by-using-a-designer.md)|Proporciona instrucciones paso a paso para crear un archivo de base de datos local que se puede usar para probar las características de datos y crear aplicaciones.|  
|[Tutorial: Conectar con los datos de un archivo de base de datos local \(Windows Forms\)](../data-tools/walkthrough-connecting-to-data-in-a-local-database-file-windows-forms.md)|Proporciona instrucciones paso a paso para conectar con una base de datos de SQL Server Express LocalDB cuando se crea una aplicación Windows simple.|  
|[Tutorial: Conectar a los datos en una base de datos de Access \(Windows Forms\)](../data-tools/connect-to-data-in-an-access-database-windows-forms.md)|Proporciona instrucciones paso a paso para la conexión con una base de datos de Microsoft Access.|  
|[Cómo: Conectar con la base de datos Northwind](../data-tools/how-to-connect-to-the-northwind-database.md)|Proporciona instrucciones para conectar con la base de datos de ejemplo Northwind en [!INCLUDE[ssNoVersion](../data-tools/includes/ssnoversion_md.md)], SQL Server Compact, SQL Server Express y Access.|  
  
 Después de crear un origen de datos y configurarlo para que obtenga acceso a un archivo de datos local, trabaje con los datos utilizando las mismas tecnologías y objetos que utilizaría para trabajar con datos de cualquier otro origen.  Para obtener más información, vea [Crear aplicaciones de datos](../data-tools/creating-data-applications.md).  
  
## Integración de la base de datos en la aplicación  
 Si se conecta a datos locales, no solo puede conectarse a un archivo de base de datos, sino también integrarlo en la aplicación.  Por ejemplo, puede abrir el menú **Proyecto**, buscar un archivo sdf, .mdf o .mdb existente y, a continuación, agregarlo al proyecto.  
  
 Si agrega archivos de datos locales, se creará un conjunto de datos con tipo y una cadena de conexión dinámica que apunta al archivo de base de datos de la aplicación.  Cuando agregue un archivo de base de datos al proyecto, utilice el **Asistente para configuración de orígenes de datos** para especificar los objetos que se van a incluir.  
  
> [!NOTE]
>  Puede configurar automáticamente su conexión e iniciar el **Asistente para configuración de orígenes de datos** arrastrando un archivo .sdf, .mdf o .mdb desde el Explorador de archivos al **Explorador de soluciones**.  A continuación, puede especificar los objetos que usará en la aplicación.  
  
 Si utiliza el **Asistente para configuración de orígenes de datos** para crear el origen de datos de un archivo de datos local, se le preguntará si desea incluir el archivo en el proyecto.  Si no lo incluye, la aplicación solo contendrá la cadena de conexión que indica la ruta de acceso en el código y no el archivo de datos real.  Para obtener más información, vea [Cómo: Administrar archivos de datos locales en los proyectos](../data-tools/how-to-manage-local-data-files-in-your-project.md).  
  
 Después de completar el asistente, el archivo de base de datos y el conjunto de datos aparecen en el **Explorador de soluciones**\/**Explorador de bases de datos** y los objetos de base de datos especificados aparecen en la ventana **Orígenes de datos**.  Puede arrastrar elementos de la ventana **Orígenes de datos** al formulario para crear controles enlazados a los datos subyacentes.  Para abrir la ventana **Orígenes de datos**, abra el menú **Datos** y, a continuación, elija **Mostrar orígenes de datos**.  Para obtener más información, vea [Enlazar controles a los datos en Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md).  
  
## Utilizar un archivo de base de datos  
 Antes de poder usar un archivo de base de datos existente \(.mdf\) en Visual Studio, probablemente deba convertir el archivo en un archivo de base de datos de [!INCLUDE[sql_Denali_short](../data-tools/includes/sql_denali_short_md.md)].  Cuando se conecte a un archivo de base de datos existente, un cuadro de mensaje le preguntará si desea actualizar.  
  
> [!IMPORTANT]
>  Si actualiza el archivo de base de datos \(.mdf\), no podrá abrirlo en una versión anterior de SQL Server.  
  
 No es necesario convertir el archivo de base de datos \(.mdf\) si **Nombre de la instancia de SQL Server** está establecido en SQLEXPRESS y SQL Server 2008 Express está instalado.  SQL Server 2008 Express se instala si Visual Studio 2010 está instalado.  Para cambiar el nombre de instancia de este archivo de base de datos, abra Visual Studio, abra el cuadro de diálogo **Agregar conexión**, especifique `.\SQLEXPRESS` como nombre de servidor y especifique la base de datos o el nombre de archivo de base de datos.  
  
## SQL Server Express LocalDB y SQL Server Express  
 Puede agregar un archivo de base de datos basado en servicios \(.mdf\) a cualquier proyecto en Visual Studio.  Puede usar diseñadores de Visual Studio para diseñar las tablas y otros objetos de base de datos, así como ejecutar consultas.  
  
 Al crear una base de datos basada en Visual Studio, utiliza el motor de SQL Server Express LocalDB para obtener acceso al archivo de base de datos \(.mdf\), donde las versiones anteriores de Visual Studio utilizaban el motor de SQL Server Express.  
  
 SQL Server Express LocalDB es una versión ligera de SQL Server que se puede programar casi de la misma manera que una base de datos de SQL Server.  SQL Server Express LocalDB se ejecuta en modo usuario y se puede instalar más rápidamente con menos requisitos previos y sin configuración.  
  
> [!NOTE]
>  Para obtener más información sobre SQL Server Express LocalDB, vea [Introducing LocalDB, an Improved SQL Express](http://go.microsoft.com/fwlink/?LinkId=234375) y [LocalDB: Where is My Database?](http://go.microsoft.com/fwlink/?LinkId=234376) en el sitio web de Microsoft.  
  
 En Visual Studio, puede utilizar SQL Server Express de forma predeterminada en lugar de SQL Server Express LocalDB.  En la barra de menús, elija **Herramientas**, **Opciones**.  Bajo el nodo **Herramientas para bases de datos**, elija **Conexiones de datos**.  En el cuadro de texto **Nombre de la instancia de SQL Server**, escriba `SQLEXPRESS`.  Como alternativa, puede escribir otros valores para el nombre de la instancia de SQL Server \(por ejemplo, `SQL2008`\).  
  
 La tabla siguiente describe las diferencias entre los motores de SQL Server Express LocalDB y SQL Server Express.  
  
||SQL Server Express LocalDB|SQL Server Express|  
|-|--------------------------------|------------------------|  
|Tipo de base de datos al crear una base de datos basada en servicios|En [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)] y [!INCLUDE[vs_dev12](../data-tools/includes/vs_dev12_md.md)], SQL Server Express LocalDB|En Visual Studio 2010 y anteriores, SQL Server Express|  
|Nombre de la instancia de SQL Server en Herramientas \/ Opciones|\(LocalDB\)\\v11.0|SQLEXPRESS|  
|Valor de origen de datos en la cadena de conexión|\(LocalDB\)\\v11.0|.\\SQLEXPRESS|  
|Valor de AttachDbFilename en la cadena de conexión|file path|file path|  
|Se requiere instancia de usuario \("User Instance\=True" en la cadena de conexión\)|No|Sí|  
|Extensión de archivo de base de datos|.mdf|.mdf|  
  
## Ventajas de SQL Server Express LocalDB  
  
-   SQL Server Express LocalDB es compatible con las ediciones basadas en servicios de SQL Server para las características que habilita SQL Server Express LocalDB.  En SQL Server, puede mover cualquier base de datos o código de Transact\-SQL de SQL Server Express LocalDB a SQL Server o SQL Azure sin ningún paso de actualización.  Por consiguiente, puede utilizar SQL Server Express LocalDB para desarrollar aplicaciones destinadas a todas las ediciones de SQL Server.  
  
-   SQL Server Express LocalDB admite el mismo optimizador de consultas y procesador de consultas que ediciones superiores de SQL Server.  
  
## Cada proyecto contiene dos copias de la base de datos  
 Al compilar un proyecto, el archivo de base de datos podría copiarse de la carpeta de proyecto de raíz en la carpeta de salida \(**bin**\).  Este comportamiento depende de la propiedad **Copiar en el directorio de salida** del archivo y el valor predeterminado de esa propiedad depende del tipo de archivo de base de datos que se use.  
  
 Para ver la carpeta **bin** en el **Explorador de soluciones**, elija el botón **Mostrar todos los archivos** en la barra de herramientas.  
  
> [!NOTE]
>  El comportamiento de la propiedad **Copiar en el directorio de salida** no se aplica a proyectos web o C\+\+.  
  
 El archivo de base de datos de la carpeta raíz del proyecto se modifica únicamente cuando se edita el esquema o los datos de la base de datos mediante el **Explorador de servidores**\/**Explorador de bases de datos** u otra herramienta de [Visual Database Tools](http://msdn.microsoft.com/es-es/6b145922-2f00-47db-befc-bf351b4809a1).  
  
 Al cambiar datos durante el desarrollo de la aplicación, se modifica la base de datos de la carpeta **bin**.  Por ejemplo, si elige la tecla F5 para depurar la aplicación, se conectará a la base de datos de esa carpeta.  
  
|Valor de la propiedad **Copiar en el directorio de salida**|Comportamiento|  
|-----------------------------------------------------------------|--------------------|  
|**Copiar si es posterior** \(valor predeterminado para los archivos .sdf\)|El archivo de base de datos se copia del directorio de proyecto al directorio **bin** la primera vez que se compila el proyecto.  La propiedad **Fecha de modificación** de los archivos se compara entonces cada vez que se compila de nuevo el proyecto.  Si el archivo en la carpeta de proyecto es posterior, se copia en la carpeta **bin** y reemplaza el archivo previo.  De lo contrario, no se copia ningún archivo. **Caution:**  No se recomienda este valor para archivos .mdb o .mdf.  El archivo de base de datos puede cambiar aunque los datos no cambien.  El archivo se puede marcar como más reciente con solo abrir una conexión \(por ejemplo, expanda el nodo **Tablas** en el **Explorador de servidores**\).|  
|**Copiar siempre** \(valor predeterminado para los archivos .mdf y .mdb\)|El archivo de base de datos se copia del directorio de proyecto al directorio **bin** cada vez que se compila la aplicación.  Cualquier cambio realizado en el archivo de datos de la carpeta de resultados se sobrescribirá la próxima vez que se ejecute la aplicación.|  
|**No copiar**|El sistema nunca sobrescribe el archivo del directorio **bin**.  La aplicación crea una cadena de conexión dinámica que señala al archivo de base de datos en el directorio de salida.  Por consiguiente, debe copiar manualmente el archivo en el directorio de salida si desea que los datos del directorio de salida coincidan con los datos del directorio de proyecto.|  
  
## Problemas comunes con los datos locales  
 La tabla siguiente explica problemas comunes que puede encontrar cuando trabaje con archivos de datos locales.  
  
|Problema|Explicación|  
|--------------|-----------------|  
|Cada vez que pruebo mi aplicación y modifico datos, mis cambios no aparecen la próxima vez que ejecuto mi aplicación.|El valor de la propiedad **Copiar en el directorio de salida** es **Copiar si es posterior** o **Copiar siempre**.  La base de datos de la carpeta de salida \(la base de datos que se modifica al probar la aplicación\) se sobrescribe cada vez que se compila el proyecto.  Para obtener más información, vea [Cómo: Administrar archivos de datos locales en los proyectos](../data-tools/how-to-manage-local-data-files-in-your-project.md).|  
|Aparece un mensaje que indica que el archivo de datos está bloqueado.|Access \(archivos .mdb\): compruebe que el archivo no está abierto en otro programa, tal como Access.<br /><br /> SQL Server Express \(archivos .mdf\): SQL Express bloquea el archivo de datos si se intenta copiar, mover o cambiar su nombre fuera del IDE de Visual Studio.|  
|El acceso se deniega cuando más de un usuario intentan obtener acceso a la misma base de datos simultáneamente.|Visual Studio utiliza las *instancias de usuario*, una característica de SQL Server Express que crea una instancia independiente de SQL Server para cada usuario.  Después de que un usuario obtenga acceso al archivo, ningún usuario posterior puede conectar.  Este problema puede ocurrir, por ejemplo, si intenta ejecutar una aplicación web en el servidor de desarrollo de ASP.NET y en IIS a la vez, ya que generalmente IIS se ejecuta con una cuenta diferente.|  
  
## Vea también  
 [Tutorial: Conectar con los datos de un archivo de base de datos local \(Windows Forms\)](../data-tools/walkthrough-connecting-to-data-in-a-local-database-file-windows-forms.md)   
 [Tutorial: Conectar a los datos en una base de datos de Access \(Windows Forms\)](../data-tools/connect-to-data-in-an-access-database-windows-forms.md)