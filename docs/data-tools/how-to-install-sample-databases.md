---
title: "C&#243;mo: Instalar bases de datos de ejemplo | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
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
  - "Adventure Works (base de datos de ejemplo)"
  - "datos [Visual Studio], bases de datos de ejemplo"
  - "Northwind (base de datos de ejemplo)"
  - "bases de datos de ejemplo, Adventure Works"
  - "bases de datos de ejemplo, Northwind"
ms.assetid: ed1291f6-604c-4972-ae22-0345c6dea12e
caps.latest.revision: 56
caps.handback.revision: 56
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
robots: noindex,nofollow
---
# C&#243;mo: Instalar bases de datos de ejemplo
Muchos ejemplos de datos requieren la capacidad de conectarse a las bases de datos de ejemplo Northwind, Pubs y AdventureWorks.  Puede realizar la instalación y conexión de estas bases de datos mediante los procedimientos siguientes.  
  
 [!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
## Instalar bases de datos  
 Muchos ejemplos de datos requieren la disponibilidad de bases de datos de ejemplo que pueden descargarse de sitios web.  Las bases de datos de ejemplo incluyen las bases de datos AdventureWorks, Northwind y Pubs.  
  
#### Para instalar las bases de datos de ejemplo Northwind y Pubs de SQL Server  
  
1.  Vaya al sitio web de las [bases de datos de ejemplo Northwind y Pubs](http://go.microsoft.com/fwlink?linkid=64296).  
  
2.  Descargue y ejecute el instalador.  
  
     El instalador agrega una carpeta **Bases de datos de ejemplo de SQL Server 2000** a la carpeta raíz del equipo.  \(Por ejemplo: **C:\\SQL Server 2000 Sample Databases**\).  
  
3.  Busque el script SQL para la base de datos que desea, Northwind o Pubs.  
  
    > [!WARNING]
    >  El archivo de base de datos .MDF no se puede convertir fácilmente a un formato que se pueda utilizar en las versiones actuales de SQL Server, por lo que se recomienda utilizar el script para crear la base de datos.  
  
4.  En el **Explorador de servidores**, cree una conexión a una instancia de SQL Server donde desea instalar la base de datos.  Si no tiene un servidor de SQL Server concreto que desee utilizar, puede utilizar la base de datos que se instala automáticamente con Visual Studio.  Para ello, especifique `(localdb) \v11.0` como nombre de servidor.  
  
     Para crear la conexión, siga estos pasos.  
  
    ###### Para crear una conexión a una instancia de SQL Server  
  
    1.  En el **Explorador de servidores**, abra el acceso directo al nodo **Conexiones de datos** y elija **Agregar conexión**.  
  
         Aparecerá el cuadro de diálogo **Agregar conexión**.  
  
    2.  Escriba el nombre del servidor de SQL Server donde desee crear la base de datos Northwind o Pubs o escriba \(localdb\)\\v11.0.  
  
    3.  En **Seleccione o escriba el nombre de la base de datos**, elija cualquier base de datos de la lista, por ejemplo, tempdb.  
  
    4.  Elija el botón **Probar conexión** para comprobar que todo funciona y, a continuación, elija el botón **Aceptar**.  
  
         En el **Explorador de servidores** aparece un nuevo nodo de conexión.  
  
5.  En el menú contextual del nodo de conexión del servidor y, a continuación, elija el botón **Nueva consulta**.  
  
     Se abre una ventana del editor y se muestra un archivo de script .sql vacío.  
  
6.  Pegue el contenido de instnwnd.sql o instpubs.sql en la ventana del editor.  
  
7.  Seleccione el botón de ejecución de la consulta \(el icono de triángulo verde abierto que hay en la parte superior derecha de la ventana de consulta\).  
  
     Si la consulta se realiza correctamente, aparecerá un mensajeque indica que los comandos se han completado correctamente.  Esto significa que se ha creado la base de datos Northwind o Pubs.  
  
     Todavía es necesario agregar una conexión a la base de datos de ejemplo.  En el **Explorador de servidores**, abra el acceso directo al nodo **Conexiones de datos** y elija **Agregar conexión**.  
  
8.  Elija el mismo servidor de base de datos que eligió antes pero, esta vez, seleccione la base de datos Northwind o Pubs en Seleccione o escriba el nombre de la base de datos y, luego, seleccione el botón **Aceptar**.  
  
     Aparece un nuevo nodo en Conexiones de datos que se corresponde con la base de datos de ejemplo.  
  
9. Cierre la ventana del editor y confirme que no desea guardar el archivo de consulta.  Una vez creada la base de datos, no es necesario guardar el script de creación de base de datos.  
  
#### Para instalar la base de datos de ejemplo AdventureWorks  
  
-   Descargue las bases de datos de ejemplo de AdventureWorks del [sitio web de CodePlex](http://go.microsoft.com/fwlink/?linkid=87843).  
  
#### Para instalar la base de datos de ejemplo Northwind para Microsoft Access  
  
1.  En Microsoft Access 2010 o posterior, busque las plantillas en línea de Northwind y elija la **base de datos Desktop Northwind 2007**.  
  
2.  En Microsoft Access, guarde el archivo de base de datos como Northwind.accdb.  
  
 La nueva extensión para las bases de datos de Access es .accdb.  Vea [Programación de datos con Microsoft Access 2010](http://msdn.microsoft.com/library/office/ff965871.aspx).  Para conectarse a la base de datos Northwind mediante Access, vea [Cómo: Conectar con la base de datos Northwind](../data-tools/how-to-connect-to-the-northwind-database.md).  
  
## Seguridad de .NET Framework  
 Las bases de datos de ejemplo se proporcionan con fines ilustrativos exclusivamente y no muestran necesariamente los mejores prácticas de seguridad.  
  
## Vea también  
 [Cómo determinar la versión y edición de SQL Server y sus componentes](http://support.microsoft.com/kb/321185)   
 [Tutorial: Crear un archivo de base de datos local en Visual Studio](../data-tools/create-a-sql-database-by-using-a-designer.md)   
 [Cómo: Conectar con la base de datos Northwind](../data-tools/how-to-connect-to-the-northwind-database.md)