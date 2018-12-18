---
title: Instalación de sistemas de base de datos, herramientas y ejemplos | Microsoft Docs
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
- sample databases
- databases, samples
ms.assetid: 821de34b-eaa9-40af-b9aa-b8305de16899
caps.latest.revision: 31
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: f18ace9a18eefd0758e581b83001b85c3f48a3da
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49244288"
---
# <a name="installing-database-systems-tools-and-samples"></a>Instalación de sistemas de base de datos, herramientas y ejemplos
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Visual Studio no incluye los sistemas de bases de datos distintos a los que se usa internamente. Para desarrollar una aplicación conectada a datos en Visual Studio, normalmente se instala el sistema de base de datos en el equipo de desarrollo local y, a continuación, implementar la aplicación y la base de datos en un entorno de producción cuando estén listas. Para que el sistema de base de datos sean accesibles desde aplicaciones .NET y a ser visibles en las ventanas de herramientas de datos de Visual Studio, debe tener un proveedor de datos ADO.NET. Un proveedor debe admitir específicamente Entity Framework si va a usar Entity data Model en la aplicación. NET.     Muchos proveedores se ofrecen a través del Administrador de paquetes de NuGet o a través de la Galería de Visual Studio.  
  
 Para el desarrollo de SQL, asegúrese de que tiene SQL Server Data Tools instalado en Visual Studio. Haga clic en el **vista** menú. Si no ve el Explorador de objetos de SQL Server, vaya al Panel de Control y cambie a Visual Studio. En el instalador, seleccione **Microsoft SQL Server Data Tools**.  
  
 Si usa las API de almacenamiento de Azure, instale los emuladores de almacenamiento de Azure en el equipo local durante el desarrollo con el fin de evitar cargos hasta que esté listo para implementarse en producción. Para obtener más información, consulte [usar el emulador de almacenamiento de Azure para desarrollo y pruebas](https://azure.microsoft.com/en-us/documentation/articles/storage-use-emulator/).  
  
 En la lista siguiente incluye algunos de los sistemas de base de datos más populares que se pueden usar en proyectos de Visual Studio. La lista no es exhaustiva. Para obtener una lista de proveedores de terceros que ofrecen los proveedores de datos ADO.NET que permiten la integración profunda con herramientas de Visual Studio, consulte [proveedores de datos de ADO.NET](https://msdn.microsoft.com/library/dd363565.aspx).  
  
### <a name="microsoft-sql-server"></a>Microsoft SQL Server  
 SQL Server es la base de datos de estrella de Microsoft que ofrece. SQL Server 2016 ofrece un rendimiento, seguridad avanzada y enriquecida e integrada de informes y análisis. Se distribuye en varias ediciones que están diseñadas para usos diferentes: de análisis empresarial altamente escalable y de alto rendimiento, para usar en un único equipo. SQL Server Express es una edición completa de SQL Server que se adapta para redistribución y de inserción.  LocalDB es una edición simplificada de SQL Server Express que no requiere configuración y se ejecuta en proceso de la aplicación. Puede descargar uno o ambos productos de [la página de descarga de SQL Server Express](https://www.microsoft.com/en-us/server-cloud/Products/sql-server-editions/sql-server-express.aspx).    Muchos de los ejemplos SQL en esta sección usan SQL Server LocalDB. SQL Server Management Studio (SSMS) es una aplicación de administración de base de datos independiente que tiene más funcionalidad que lo que se proporciona en el Explorador de objetos de servidor de SQL de Visual Studio. Puede obtener SSMS desde el vínculo anterior.  
  
### <a name="oracle"></a>Oracle  
 Puede descargar una edición de pagada o gratuita de la base de datos de Oracle desde el [Oracle Technology Network](http://www.oracle.com/technetwork/database/enterprise-edition/downloads/index-092322.html) página. Compatibilidad con el tiempo de diseño de Entity Framework y los TableAdapters, necesitará el [Oracle Developer Tools para Visual Studio](http://www.oracle.com/technetwork/developer-tools/visual-studio/overview/index.html). Otros productos de Oracle oficiales, incluido al cliente Oracle Instant, están disponibles a través del Administrador de paquetes de NuGet.  Puede descargar los esquemas de Oracle de ejemplo siguiendo las instrucciones de la [documentación en línea de Oracle](http://docs.oracle.com/cd/E11882_01/server.112/e10831/toc.htm).  
  
### <a name="mysql"></a>MySQL  
 MySQL es un sistema de base de datos de código abierto más populares que se usa ampliamente en las empresas y los sitios Web. Descargas de MySQL, MySQL para Visual Studio y productos relacionados están en [MySQL en Windows](http://www.mysql.com/why-mysql/windows/).  Otros fabricantes ofrecen varias extensiones de Visual Studio y aplicaciones de administración independiente para MySQL. Puede examinar las ofertas en el Administrador de paquetes de NuGet (**herramientas** > **Administrador de paquetes de NuGet** > **administrar paquetes de NuGet para solución**) .  
  
### <a name="postgresql"></a>PostgreSQL  
 PostgreSQL es un sistema de base de datos relacional de objetos gratuito, código abierto. Para instalarlo en Windows, puede descargarlo desde el [página de descarga de PostgreSQL](http://www.postgresql.org/download/windows/).  También puede compilar PostgreSQL desde el código fuente.  El sistema de PostgreSQL core incluye una interfaz de lenguaje C. Muchos otros proveedores proporcionan paquetes de NuGet para usar PostgreSQL desde las aplicaciones. NET.  Puede examinar las ofertas en el Administrador de paquetes de NuGet (**herramientas** > **Administrador de paquetes de NuGet** > **administrar paquetes de NuGet para solución**) . Quizás el más popular paquete se proporciona por [npgsql.org](http://www.npgsql.org).  
  
### <a name="sqlite"></a>SQLite  
 SQLite es un motor de base de datos SQL incrustado que se ejecuta en el proceso de la aplicación. Puede descargarlo desde el [página de descarga de SQLite](http://www.sqlite.org/download.html). Muchos paquetes de NuGet de terceros para SQLite también están disponibles. Puede examinar las ofertas en el Administrador de paquetes de NuGet (**herramientas** > **Administrador de paquetes de NuGet** > **administrar paquetes de NuGet para solución**) .  
  
### <a name="firebird"></a>Firebird  
 Firebird es un sistema de base de datos SQL de código abierto. Puede descargarlo desde el [página de descarga de pájaro de fuego](http://firebirdsql.org/en/downloads/). Un proveedor de datos ADO.NET está disponible a través del Administrador de paquetes de NuGet.  
  
## <a name="see-also"></a>Vea también  
 [Cómo determinar la versión y edición de SQL Server y sus componentes](http://support.microsoft.com/kb/321185)

