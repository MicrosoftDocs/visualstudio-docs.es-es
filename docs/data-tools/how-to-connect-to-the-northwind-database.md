---
title: "C&#243;mo: Conectar con la base de datos Northwind | Microsoft Docs"
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
  - "conexiones [Visual Studio], Northwind (base de datos)"
  - "Northwind (base de datos de ejemplo)"
ms.assetid: cc6cb79f-d035-41f8-b398-8d4a45922bfb
caps.latest.revision: 29
caps.handback.revision: 29
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
robots: noindex,nofollow
---
# C&#243;mo: Conectar con la base de datos Northwind
A medida que aprende cómo crear aplicaciones de base de datos mediante Visual Studio, deberá conectarse a la base de datos Northwind para seguir muchos de los ejemplos de la documentación de ese producto.  Dependiendo del ejemplo que esté siguiendo, se conectará a la base de datos en SQL Server o en un archivo de base de datos, como uno de Microsoft Access o SQL Server.  
  
## Crear conexiones a la base de datos Northwind  
 [!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
#### Para crear una conexión de datos a la base de datos Northwind \(SQL Server\)  
  
1.  En el menú **Ver**, elija **Explorador de servidores**\/**Explorador de bases de datos**.  
  
2.  En **Explorador de servidores**\/**Explorador de bases de datos**, abra el menú contextual **Conexiones de datos** y elija **Agregar conexión**.  
  
     Después de elegir **Agregar conexión**, aparece el cuadro de diálogo **Elegir origen de datos** o el cuadro de diálogo **Agregar conexión**.  
  
3.  Si aparece el cuadro de diálogo **Elegir origen de datos**, seleccione **Microsoft SQL Server** y, a continuación, elija **Aceptar**.  
  
     Si aparece el cuadro de diálogo **Agregar conexión** y no está **Origen de datos** en **Microsoft SQL Server \(SqlClient\)**, elija el botón **Cambiar** para abrir el cuadro de diálogo **Cambiar origen de datos**, seleccione **Microsoft SQL Server** y, a continuación, elija **Aceptar**.  
  
4.  En la lista **Nombre del servidor**, especifique el nombre del servidor en el que se encuentra la base de datos Northwind.  
  
5.  Dependiendo de los requisitos de la versión de SQL Server y la base de datos Northwind, elija **Usar autenticación de Windows** o **Usar autenticación de SQL Server** y escriba un nombre de usuario y contraseña para iniciar sesión en el equipo en que se ejecuta SQL Server.  
  
6.  En la lista **Seleccionar o escribir nombre de base de datos**, elija la base de datos Northwind.  
  
7.  Elija **Probar conexión** para comprobar la conectividad a la base de datos Northwind.  
  
8.  Elija **Aceptar**.  
  
     Se agrega una conexión de datos a la base de datos Northwind al **Explorador de servidores**\/**Explorador de bases de datos**.  
  
 Además de realizar la conexión a una instancia remota de una base de datos de SQL Server, también puede conectar directamente a los archivos reales que contienen la base de datos.  Esto permite agregar directamente los archivos de base de datos en un proyecto donde se pueden implementar como parte de la aplicación.  Actualmente se admiten los siguientes archivos de base de datos locales: archivos de base de datos de SQL Server Compact \(.sdf\), [!INCLUDE[ssNoVersion](../data-tools/includes/ssnoversion_md.md)] y archivos de base de datos de SQL Server Express \(.mdf\), así como archivos de base de datos de Microsoft Access \(.mdb o .accdb\).  
  
#### Para crear una conexión de datos a la base de datos Northwind: archivo de base de datos de SQL Server \(.mdf\)  
  
1.  En el menú **Ver**, elija **Explorador de servidores**\/**Explorador de bases de datos**.  
  
2.  En **Explorador de servidores**\/**Explorador de bases de datos**, abra el menú contextual **Conexiones de datos** y elija **Agregar conexión**.  
  
     Después de elegir **Agregar conexión**, aparece el cuadro de diálogo **Agregar conexión** o el cuadro de diálogo **Elegir origen de datos**.  
  
3.  Si aparece el cuadro de diálogo **Elegir origen de datos**, seleccione **Archivo de base de datos de Microsoft SQL Server** y, a continuación, elija el botón **Aceptar**.  
  
4.  Si aparece el cuadro de diálogo **Agregar conexión**, compruebe que **Origen de datos** está establecido en **Archivo de base de datos de Microsoft SQL Server \(SqlClient\)**.  Si no está establecido en **Archivo de base de datos de Microsoft SQL Server \(SqlClient\)**, elija **Cambiar** para abrir el cuadro de diálogo **Cambiar origen de datos**, elija **Archivo de base de datos de Microsoft SQL Server** y, a continuación, elija el botón **Aceptar**.  
  
5.  Elija **Examinar** para buscar el archivo .mdf que contiene la base de datos Northwind.  
  
6.  Dependiendo de los requisitos de la versión de la base de datos Northwind, elija **Utilizar autenticación de Windows** o **Autenticación de SQL Server** y escriba un nombre de usuario y contraseña para iniciar sesión en el equipo en que se ejecuta SQL Server.  
  
7.  Elija el botón **Aceptar**.  
  
     Se agrega una conexión de datos a la base de datos Northwind al **Explorador de servidores**\/**Explorador de bases de datos**.  
  
> [!NOTE]
>  [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)] tiene cambios que se aplican al archivo de base de datos Northwind \(.mdf\).  Para obtener más información, vea [Cómo: Instalar bases de datos de ejemplo](../data-tools/how-to-install-sample-databases.md).  
  
#### Para crear una conexión de datos a la base de datos Northwind: archivo de base de datos de Access \(.mdb o .accdb\)  
  
1.  En el menú **Ver**, elija **Explorador de servidores**\/**Explorador de bases de datos**.  
  
2.  En **Explorador de servidores**\/**Explorador de bases de datos**, abra el menú contextual **Conexiones de datos** y elija **Agregar conexión**.  
  
     Después de elegir **Agregar conexión**, aparece el cuadro de diálogo **Agregar conexión** o el cuadro de diálogo **Elegir origen de datos**.  
  
3.  Si aparece el cuadro de diálogo **Elegir origen de datos**, seleccione **Archivo de base de datos de Microsoft Access** y, a continuación, elija **Aceptar**.  
  
4.  Si aparece el cuadro de diálogo **Agregar conexión**, compruebe que **Origen de datos** está establecido en **Archivo de base de datos de Microsoft Access**.  Si no está establecido en **Archivo de base de datos de Microsoft Access**, elija **Cambiar** para abrir el cuadro de diálogo **Cambiar origen de datos**, elija **Archivo de base de datos de Microsoft Access** y, a continuación, elija el botón **Aceptar**.  
  
5.  Elija **Examinar** para buscar el archivo .mdb o .accdb que contiene la base de datos Northwind.  
  
6.  Escriba un nombre de usuario y una contraseña si la versión de la base de datos Northwind lo requiere.  
  
7.  Elija **Aceptar**.  
  
     Se agrega una conexión de datos a la base de datos Northwind al **Explorador de servidores**\/**Explorador de bases de datos**.  
  
## Vea también  
 [Cómo: Instalar bases de datos de ejemplo](../data-tools/how-to-install-sample-databases.md)   
 [Programación de datos con Microsoft Access 2010](http://msdn.microsoft.com/library/office/ff965871.aspx)   
 [Tutoriales sobre datos](../Topic/Data%20Walkthroughs.md)