---
title: 'Cómo: conectarse a la base de datos Northwind | Microsoft Docs'
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
- connections [Visual Studio], Northwind database
- Northwind sample database
ms.assetid: cc6cb79f-d035-41f8-b398-8d4a45922bfb
caps.latest.revision: 29
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: 2b4393758b4c246af0da830b6ed8d8e20eb8ff40
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49191131"
---
# <a name="how-to-connect-to-the-northwind-database"></a>Cómo: Conectar con la base de datos Northwind
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

A medida que aprende cómo crear aplicaciones de base de datos mediante Visual Studio, deberá conectarse a la base de datos Northwind para seguir muchos de los ejemplos de la documentación de ese producto. Dependiendo del ejemplo que esté siguiendo, se conectará a la base de datos en SQL Server o en un archivo de base de datos, como uno de Microsoft Access o SQL Server.  
  
## <a name="creating-data-connections-to-the-northwind-database"></a>Crear conexiones a la base de datos Northwind  
 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]  
  
#### <a name="to-create-a-data-connection-to-the-northwind-database-sql-server"></a>Para crear una conexión de datos a la base de datos Northwind (SQL Server)  
  
1.  En el **vista** menú, elija **Explorador de servidores**/**Database Explorer**.  
  
2.  En **Explorador de servidores**/**Database Explorer**, abra el menú contextual para **conexiones de datos** y elija **Agregar conexión**.  
  
     Después de elegir **Agregar conexión**, ya sea el **Elegir origen de datos** cuadro de diálogo o la **Agregar conexión** aparecerá el cuadro de diálogo.  
  
3.  Si el **Elegir origen de datos** aparece el cuadro de diálogo, seleccione **Microsoft SQL Server**y, a continuación, elija **Aceptar**.  
  
     Si el **Agregar conexión** aparece el cuadro de diálogo y el **origen de datos** no **Microsoft SQL Server (SqlClient)**, elija el **cambio** botón para abrir el **cambiar origen de datos** cuadro de diálogo, seleccione **Microsoft SQL Server**y, a continuación, elija el **Aceptar** botón.  
  
4.  En el **nombre del servidor** lista, especifique el nombre del servidor en el que se encuentra la base de datos Northwind.  
  
5.  Dependiendo de los requisitos de la versión de SQL Server y la base de datos Northwind, elija **utilizar autenticación de Windows** o elija **utilizar autenticación de SQL Server** y escriba un nombre de usuario y contraseña para iniciar sesión en el equipo que ejecuta SQL Server.  
  
6.  Elija la base de datos Northwind en el **seleccione o escriba un nombre de base de datos** lista.  
  
7.  Elija **Probar conexión** para comprobar la conectividad a la base de datos Northwind.  
  
8.  Elija **Aceptar**.  
  
     Se agrega una conexión de datos a la base de datos de Northwind a **Explorador de servidores**/**Database Explorer**.  
  
 Además de realizar la conexión a una instancia remota de una base de datos de SQL Server, también puede conectar directamente a los archivos reales que contienen la base de datos. Esto permite agregar directamente los archivos de base de datos en un proyecto donde se pueden implementar como parte de la aplicación. Actualmente se admiten los siguientes archivos de base de datos local: archivos de base de datos de SQL Server Compact (.sdf), [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] y archivos de base de datos de SQL Server Express (.mdf) y archivos de base de datos de Microsoft Access (.mdb o .accdb).  
  
#### <a name="to-create-a-data-connection-to-the-northwind-databasesql-server-database-file-mdf"></a>Para crear una conexión de datos a la base de datos Northwind: archivo de base de datos de SQL Server (.mdf)  
  
1.  En el **vista** menú, elija **Explorador de servidores**/**Database Explorer**.  
  
2.  En **Explorador de servidores**/**Database Explorer**, abra el menú contextual para **conexiones de datos** y elija **Agregar conexión**.  
  
     Después de elegir **Agregar conexión**, ya sea el **Agregar conexión** cuadro de diálogo o la **Elegir origen de datos** aparecerá el cuadro de diálogo.  
  
3.  Si el **Elegir origen de datos** aparece el cuadro de diálogo, seleccione **el archivo de base de datos de Microsoft SQL Server**y, a continuación, elija el **Aceptar**.  
  
4.  Si el **Agregar conexión** aparece el cuadro de diálogo, compruebe que la **origen de datos** está establecido en **archivo de base de datos de Microsoft SQL Server (SqlClient)**. Si no está establecido en **archivo de base de datos de Microsoft SQL Server (SqlClient)**, elija **cambio** para abrir el **cambiar origen de datos** diálogo cuadro, elija **Microsoft SQL Archivo de base de datos de servidor**y, a continuación, elija el **Aceptar** botón.  
  
5.  Elija **examinar** para buscar el archivo .mdf que contiene la base de datos Northwind.  
  
6.  Dependiendo de los requisitos de la versión de la base de datos Northwind, elija **utilizar autenticación de Windows** o elija **autenticación de SQL Server** y escriba un nombre de usuario y una contraseña para iniciar sesión en el equipo que ejecuta SQL Server.  
  
7.  Elija el botón **Aceptar** .  
  
     Se agrega una conexión de datos a la base de datos de Northwind a **Explorador de servidores**/**Database Explorer**.  
  
> [!NOTE]
>  [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)] tiene cambios que se aplican al archivo de base de datos Northwind (.mdf). Para obtener información, consulte [Cómo: instalar bases de datos de ejemplo](../data-tools/how-to-install-sample-databases.md).  
  
#### <a name="to-create-a-data-connection-to-the-northwind-databaseaccess-database-file-mdb-or-accdb"></a>Para crear una conexión de datos a la base de datos Northwind: archivo de base de datos de Access (.mdb o .accdb)  
  
1.  En el **vista** menú, elija **Explorador de servidores**/**Database Explorer**.  
  
2.  En **Explorador de servidores**/**Database Explorer**, abra el menú contextual para **conexiones de datos** y elija **Agregar conexión**.  
  
     Después de elegir **Agregar conexión**, ya sea el **Agregar conexión** cuadro de diálogo o la **Elegir origen de datos** aparecerá el cuadro de diálogo.  
  
3.  Si el **Elegir origen de datos** aparece el cuadro de diálogo, seleccione **el archivo de base de datos de Microsoft Access**y, a continuación, elija **Aceptar**.  
  
4.  Si el **Agregar conexión** aparece el cuadro de diálogo, compruebe que la **origen de datos** está establecido en **el archivo de base de datos de Microsoft Access**. Si no está establecido en **el archivo de base de datos de Microsoft Access**, elija **cambio** para abrir el **cambiar origen de datos** cuadro de diálogo, seleccione **base de datos de Microsoft Access Archivo**y, a continuación, elija el **Aceptar** botón.  
  
5.  Elija **examinar** para buscar el archivo .mdb o .accdb que contiene la base de datos Northwind.  
  
6.  Escriba un nombre de usuario y una contraseña si la versión de la base de datos Northwind lo requiere.  
  
7.  Elija **Aceptar**.  
  
     Se agrega una conexión de datos a la base de datos de Northwind a **Explorador de servidores**/**Database Explorer**.  
  
## <a name="see-also"></a>Vea también  
 [Cómo: instalar bases de datos de ejemplo](../data-tools/how-to-install-sample-databases.md)   
 [Programación de datos con Microsoft Access 2010](http://msdn.microsoft.com/library/office/ff965871.aspx)   
 [Tutoriales de datos](http://msdn.microsoft.com/library/15a88fb8-3bee-4962-914d-7a1f8bd40ec4)