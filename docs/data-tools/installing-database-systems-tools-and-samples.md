---
title: Compatibilidad de base de datos de Visual Studio
ms.date: 09/06/2017
ms.topic: conceptual
helpviewer_keywords:
- database systems
- database compatibility
- databases for Visual Studio
ms.assetid: 821de34b-eaa9-40af-b9aa-b8305de16899
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 6cb532ee53e61842eb9f36ae0ecd437ef8fe0e0f
ms.sourcegitcommit: e9d1018a01af62c3dc5aeb6b325faba7e20bd496
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/28/2018
ms.locfileid: "37089200"
---
# <a name="compatible-database-systems-for-visual-studio"></a>Sistemas de base de datos compatible para Visual Studio

Para desarrollar una aplicación conectada a datos en Visual Studio, normalmente se instala el sistema de base de datos en el equipo de desarrollo local y, a continuación, implementar la aplicación y la base de datos en un entorno de producción cuando estén listas. Visual Studio instala SQL Server Express LocalDB en el equipo como parte de la **procesamiento y almacenamiento de datos** carga de trabajo. Esta instancia de LocalDB es útil para desarrollar aplicaciones de datos conectados de forma rápida y sencilla.

Para que un sistema de base de datos sean accesibles desde aplicaciones .NET y a ser visibles en las ventanas de herramientas de datos de Visual Studio, debe tener un proveedor de datos ADO.NET. Un proveedor debe admitir específicamente Entity Framework si va a usar Entity data Model en la aplicación. NET. Muchos proveedores se ofrecen a través del Administrador de paquetes de NuGet o a través de Visual Studio Marketplace.

Si usa API de Azure storage, instale los emuladores de almacenamiento de Azure en el equipo local durante el desarrollo con el fin de evitar cargos hasta que esté listo para implementarse en producción. Para obtener más información, consulte [usar el emulador de almacenamiento de Azure para desarrollo y pruebas](/azure/storage/common/storage-use-emulator).

En la lista siguiente incluye algunos de los sistemas de base de datos más populares que se pueden usar en proyectos de Visual Studio. La lista no es exhaustiva. Para obtener una lista de proveedores de terceros que ofrecen los proveedores de datos ADO.NET que permiten la integración profunda con herramientas de Visual Studio, consulte [proveedores de datos de ADO.NET](/dotnet/framework/data/adonet/data-providers).

## <a name="microsoft-sql-server"></a>Microsoft SQL Server

SQL Server es la base de datos de estrella de Microsoft que ofrece. SQL Server 2016 ofrece un rendimiento, seguridad avanzada y enriquecida e integrada de informes y análisis. Se distribuye en varias ediciones que están diseñadas para usos diferentes: de análisis empresarial altamente escalable y de alto rendimiento, para usar en un único equipo. SQL Server Express es una edición completa de SQL Server que se adapta para redistribución y de inserción.  LocalDB es una edición simplificada de SQL Server Express que no requiere configuración y se ejecuta en proceso de la aplicación. Puede descargar uno o ambos productos desde el [página de descarga de SQL Server Express](https://www.microsoft.com/sql-server/sql-server-editions-express). Muchos de los ejemplos SQL en esta sección usan SQL Server LocalDB. SQL Server Management Studio (SSMS) es una aplicación de administración de base de datos independiente que tiene más funcionalidad que lo que se proporciona en el Explorador de objetos de servidor de SQL de Visual Studio. Puede obtener SSMS desde el vínculo anterior.

## <a name="oracle"></a>Oracle

Puede descargar una edición de pagada o gratuita de la base de datos de Oracle desde el [red de tecnología de Oracle](http://www.oracle.com/technetwork/database/enterprise-edition/downloads/index-092322.html) página. Compatibilidad con el tiempo de diseño de Entity Framework y los TableAdapters, necesitará el [herramientas de desarrollo de Oracle para Visual Studio](http://www.oracle.com/technetwork/developer-tools/visual-studio/overview/index.html). Otros productos de Oracle oficiales, incluido al cliente Oracle Instant, están disponibles a través del Administrador de paquetes de NuGet. Puede descargar los esquemas de Oracle de ejemplo siguiendo las instrucciones de la [documentación en línea de Oracle](http://docs.oracle.com/cd/E11882_01/server.112/e10831/toc.htm).

## <a name="mysql"></a>MySQL

MySQL es un sistema de base de datos de código abierto más populares que se usa ampliamente en las empresas y los sitios Web. Descargas de MySQL, MySQL para Visual Studio y productos relacionados están en [MySQL en Windows](http://www.mysql.com/why-mysql/windows/). Otros fabricantes ofrecen varias extensiones de Visual Studio y aplicaciones de administración independiente para MySQL. Puede examinar las ofertas en el Administrador de paquetes de NuGet (**herramientas** > **Administrador de paquetes de NuGet** > **administrar paquetes de NuGet para solución**) .

## <a name="postgresql"></a>PostgreSQL

PostgreSQL es un sistema de base de datos relacional de objetos gratuito, código abierto. Para instalarlo en Windows, puede descargarlo desde el [página de descarga de PostgreSQL](http://www.postgresql.org/download/windows/). También puede compilar PostgreSQL desde el código fuente. El sistema de PostgreSQL core incluye una interfaz de lenguaje C. Muchos otros proveedores proporcionan paquetes de NuGet para usar PostgreSQL desde las aplicaciones. NET. Puede examinar las ofertas en el Administrador de paquetes de NuGet (**herramientas** > **Administrador de paquetes de NuGet** > **administrar paquetes de NuGet para solución**) . Quizás, proporciona el paquete más popular [npgsql.org](http://www.npgsql.org).

## <a name="sqlite"></a>SQLite

SQLite es un motor de base de datos SQL incrustado que se ejecuta en el proceso de la aplicación. Puede descargarlo desde el [página de descarga de SQLite](http://www.sqlite.org/download.html). Muchos paquetes de NuGet de terceros para SQLite también están disponibles. Puede examinar las ofertas en el Administrador de paquetes de NuGet (**herramientas** > **Administrador de paquetes de NuGet** > **administrar paquetes de NuGet para solución**) .

## <a name="firebird"></a>Firebird

Firebird es un sistema de base de datos SQL de código abierto. Puede descargarlo desde el [página de descarga de pájaro de fuego](http://firebirdsql.org/en/downloads/). Un proveedor de datos ADO.NET está disponible a través del Administrador de paquetes de NuGet.

## <a name="see-also"></a>Vea también

- [Obtener acceso a los datos en Visual Studio](../data-tools/accessing-data-in-visual-studio.md)
- [Cómo determinar la versión y edición de SQL Server y sus componentes](http://support.microsoft.com/kb/321185)