---
title: 'Cómo: instalar bases de datos de ejemplo | Microsoft Docs'
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
- sample databases, Adventure Works
- data [Visual Studio], sample databases
- sample databases, Northwind
- Northwind sample database
- Adventure Works sample database
ms.assetid: ed1291f6-604c-4972-ae22-0345c6dea12e
caps.latest.revision: 56
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: d3ffe88fb54da26468ca510a2f1a7ab6170d88db
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49881727"
---
# <a name="how-to-install-sample-databases"></a>Cómo: Instalar bases de datos de ejemplo
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Muchos ejemplos de datos requieren la capacidad de conectarse a las bases de datos de ejemplo Northwind, Pubs y AdventureWorks. Puede realizar la instalación y conexión de estas bases de datos mediante los procedimientos siguientes.  
  
 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]  
  
## <a name="installing-databases"></a>Instalar bases de datos  
 Muchos ejemplos de datos requieren la disponibilidad de bases de datos de ejemplo que pueden descargarse de sitios web. Las bases de datos de ejemplo incluyen las bases de datos AdventureWorks, Northwind y Pubs.  
  
#### <a name="to-install-the-northwind-and-pubs-sample-databases-for-sql-server"></a>Para instalar las bases de datos de ejemplo Northwind y Pubs de SQL Server  
  
1.  Vaya a la [bases de datos de ejemplo Pubs y Northwind](http://go.microsoft.com/fwlink?linkid=64296) sitio web.  
  
2.  Descargue y ejecute el instalador.  
  
     El instalador agrega una carpeta **SQL Server 2000 Sample Databases** a la carpeta raíz en el equipo. (Por ejemplo: **C:\SQL Server 2000 Sample Databases**).  
  
3.  Busque el script SQL para la base de datos que desea, Northwind o Pubs.  
  
    > [!WARNING]
    >  El archivo de base de datos .MDF no se puede convertir fácilmente a un formato que se pueda utilizar en las versiones actuales de SQL Server, por lo que se recomienda utilizar el script para crear la base de datos.  
  
4.  En **Explorador de servidores**, cree una conexión a una instancia de SQL Server donde desea instalar la base de datos. Si no tiene un servidor de SQL Server concreto que desee utilizar, puede utilizar la base de datos que se instala automáticamente con Visual Studio. Para ello, especifique `(localdb)\v11.0` como el nombre del servidor.  
  
     Para crear la conexión, siga estos pasos.  
  
    ###### <a name="to-create-a-connection-to-an-instance-of-sql-server"></a>Para crear una conexión a una instancia de SQL Server  
  
    1.  En **Explorador de servidores**, abra el menú contextual para el **conexiones de datos** nodo y elija **Agregar conexión**.  
  
         El **Agregar conexión** aparece el cuadro de diálogo.  
  
    2.  Escriba el nombre del servidor de SQL Server donde desee crear la base de datos Northwind o Pubs o escriba (localdb)\v11.0.  
  
    3.  En **seleccione o escriba un nombre de base de datos**, elija cualquier base de datos en la lista, por ejemplo, tempdb.  
  
    4.  Elija la **Probar conexión** botón para comprobar que todo funciona y, a continuación, elija el **Aceptar** botón.  
  
         Aparece un nuevo nodo de conexión en **Explorador de servidores**.  
  
5.  En el menú contextual del nodo de conexión para el servidor y, a continuación, elija el **nueva consulta** botón.  
  
     Se abre una ventana del editor y se muestra un archivo de script .sql vacío.  
  
6.  Pegue el contenido de instnwnd.sql o instpubs.sql en la ventana del editor.  
  
7.  Seleccione el botón de ejecución de la consulta (el icono de triángulo verde abierto que hay en la parte superior derecha de la ventana de consulta).  
  
     Si la consulta se realiza correctamente, el mensaje **comandos completados correctamente** aparece. Esto significa que se ha creado la base de datos Northwind o Pubs.  
  
     Todavía es necesario agregar una conexión a la base de datos de ejemplo. En **Explorador de servidores**, abra el menú contextual para el **conexiones de datos** nodo y elija **Agregar conexión**.  
  
8.  Elija el mismo servidor que eligió anteriormente, pero esta vez, en, seleccione la base de datos o escriba un nombre de base de datos, elija la base de datos Northwind o pubs y elija el **Aceptar** botón.  
  
     Aparece un nuevo nodo en Conexiones de datos que se corresponde con la base de datos de ejemplo.  
  
9. Cierre la ventana del editor y confirme que no desea guardar el archivo de consulta. Una vez creada la base de datos, no es necesario guardar el script de creación de base de datos.  
  
#### <a name="to-install-the-adventureworks-sample-databases"></a>Para instalar la base de datos de ejemplo AdventureWorks  
  
-   Descargar las bases de datos de ejemplo AdventureWorks desde el [sitio Web de CodePlex](http://go.microsoft.com/fwlink/?linkid=87843).  
  
#### <a name="to-install-the-northwind-sample-database-for-microsoft-access"></a>Para instalar la base de datos de ejemplo Northwind para Microsoft Access  
  
1. En Microsoft Access 2010 o posterior, busque las plantillas en línea de Northwind y elija **base de datos Desktop Northwind 2007**.  
  
2. En Microsoft Access, guarde el archivo de base de datos como Northwind.accdb.  
  
   La nueva extensión para las bases de datos de Access es .accdb. Consulte [programación de datos con Microsoft Access 2010](http://msdn.microsoft.com/library/office/ff965871.aspx). Para conectarse a la base de datos Northwind mediante Access, consulte [Cómo: conectarse a la base de datos Northwind](../data-tools/how-to-connect-to-the-northwind-database.md).  
  
## <a name="net-framework-security"></a>Seguridad de .NET Framework  
 Las bases de datos de ejemplo se proporcionan con fines ilustrativos exclusivamente y no muestran necesariamente los mejores prácticas de seguridad.  
  
## <a name="see-also"></a>Vea también  
 [Cómo determinar la versión y edición de SQL Server y sus componentes](http://support.microsoft.com/kb/321185)   
 [Crear una base de datos SQL mediante un diseñador](../data-tools/create-a-sql-database-by-using-a-designer.md)   
 [Cómo: Conectar con la base de datos Northwind](../data-tools/how-to-connect-to-the-northwind-database.md)