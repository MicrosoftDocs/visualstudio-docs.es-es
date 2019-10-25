---
title: Compatibilidad con bases de datos
ms.date: 09/06/2017
ms.topic: conceptual
helpviewer_keywords:
- database systems
- database compatibility
- databases for Visual Studio
ms.assetid: 821de34b-eaa9-40af-b9aa-b8305de16899
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: dd469f955a24c6d3c2fb5e438d81e6b8a2db8458
ms.sourcegitcommit: 8589d85cc10710ef87e6363a2effa5ee5610d46a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2019
ms.locfileid: "72806996"
---
# <a name="compatible-database-systems-for-visual-studio"></a>Sistemas de bases de datos compatibles para Visual Studio

Para desarrollar una aplicación conectada a datos en Visual Studio, normalmente se instala el sistema de base de datos en el equipo de desarrollo local y, después, se implementa la aplicación y la base de datos en un entorno de producción cuando están listos. Visual Studio instala SQL Server Express LocalDB en el equipo como parte de la carga de trabajo de **procesamiento y almacenamiento de datos** . Esta instancia de LocalDB es útil para desarrollar aplicaciones conectadas a datos de forma rápida y sencilla.

Para que un sistema de base de datos sea accesible desde aplicaciones .NET y para que esté visible en las ventanas de Visual Studio Data Tools, debe tener un proveedor de datos ADO.NET. Un proveedor debe admitir específicamente Entity Framework Si tiene previsto utilizar Entity Data models en la aplicación .NET. Muchos proveedores se ofrecen a través del administrador de paquetes NuGet o a través de la Visual Studio Marketplace.

Si usa las API de almacenamiento de Azure, instale los emuladores de Azure Storage en el equipo local durante el desarrollo con el fin de evitar cargos hasta que esté listo para realizar la implementación en producción. Para obtener más información, vea [usar el emulador de Azure Storage para desarrollo y pruebas](/azure/storage/common/storage-use-emulator).

La lista siguiente incluye algunos de los sistemas de base de datos más populares que se pueden usar en los proyectos de Visual Studio. La lista no es exhaustiva. Para obtener una lista de proveedores de terceros que ofrecen proveedores de datos de ADO.NET que permiten una integración profunda con las herramientas de Visual Studio, consulte [proveedores de datos de ADO.net](/dotnet/framework/data/adonet/data-providers).

## <a name="microsoft-sql-server"></a>Microsoft SQL Server

SQL Server es la oferta de base de datos insignia de Microsoft. SQL Server 2016 ofrece un rendimiento innovador, seguridad avanzada y informes y análisis enriquecidos e integrados. Se distribuye en varias ediciones diseñadas para distintos usos: desde análisis de negocios altamente escalables y de alto rendimiento, para usar en un solo equipo. SQL Server Express es una edición completa de SQL Server diseñada para la redistribución e inserción.  LocalDB es una edición simplificada de SQL Server Express que no requiere ninguna configuración y que se ejecuta en el proceso de la aplicación. Puede descargar uno o ambos productos desde la [Página de descarga de SQL Server Express](https://www.microsoft.com/sql-server/sql-server-editions-express). Muchos de los ejemplos de SQL de esta sección usan SQL Server LocalDB. SQL Server Management Studio (SSMS) es una aplicación de administración de bases de datos independiente que tiene más funcionalidad de la que se proporciona en Visual Studio Explorador de objetos de SQL Server. Puede obtener SSMS desde el vínculo anterior.

## <a name="oracle"></a>Oracle

Puede descargar una edición de pago o gratuita de la base de datos de Oracle desde la página de la [red de tecnología de Oracle](https://www.oracle.com/database/technologies/oracle-database-software-downloads.html) . En cuanto a la compatibilidad en tiempo de diseño para Entity Framework y TableAdapters, necesitará [Oracle Developer Tools para Visual Studio](https://www.oracle.com/database/technologies/developer-tools/visual-studio/). Otros productos oficiales de Oracle, incluido Oracle Instant Client, están disponibles a través del administrador de paquetes NuGet. Puede descargar los esquemas de ejemplo de Oracle siguiendo las instrucciones de la [documentación en pantalla de Oracle](https://docs.oracle.com/cd/E11882_01/server.112/e10831/toc.htm).

## <a name="mysql"></a>MySQL

MySQL es un conocido sistema de base de datos de código abierto que se usa ampliamente en empresas y sitios Web. Las descargas para MySQL, MySQL para Visual Studio y productos relacionados están en [MySQL en Windows](https://www.mysql.com/why-mysql/windows/). Otros fabricantes ofrecen varias extensiones de Visual Studio y aplicaciones de administración independientes para MySQL. Puede examinar las ofertas en el administrador de paquetes NuGet (**herramientas**  > **Administrador de paquetes Nuget**  > **administrar paquetes Nuget para la solución**).

## <a name="postgresql"></a>PostgreSQL

PostgreSQL es un sistema de base de datos relacional de objetos de código abierto y gratuito. Para instalarlo en Windows, puede descargarlo desde la [Página de descarga de PostgreSQL](https://www.postgresql.org/download/windows/). También puede crear PostgreSQL a partir del código fuente. El sistema principal de PostgreSQL incluye una interfaz de lenguaje C. Muchos terceros proporcionan paquetes NuGet para usar PostgreSQL desde aplicaciones .NET. Puede examinar las ofertas en el administrador de paquetes NuGet (**herramientas**  > **Administrador de paquetes Nuget**  > **administrar paquetes Nuget para la solución**). Quizás, el paquete más popular lo proporciona [npgsql.org](http://www.npgsql.org).

## <a name="sqlite"></a>SQLite

SQLite es un motor de base de datos de SQL incrustado que se ejecuta en el propio proceso de la aplicación. Puede descargarlo desde la [Página de descarga de SQLite](https://www.sqlite.org/download.html). También están disponibles muchos paquetes NuGet de terceros para SQLite. Puede examinar las ofertas en el administrador de paquetes NuGet (**herramientas**  > **Administrador de paquetes Nuget**  > **administrar paquetes Nuget para la solución**).

## <a name="firebird"></a>Firebird

Firebird es un sistema de base de datos SQL de código abierto. Puede descargarlo desde la [Página de descarga de Firebird](http://firebirdsql.org/en/downloads/). Un proveedor de datos ADO.NET está disponible a través del administrador de paquetes NuGet.

## <a name="see-also"></a>Vea también

- [Obtener acceso a los datos en Visual Studio](../data-tools/accessing-data-in-visual-studio.md)
- [Cómo determinar la versión y la edición de SQL Server y sus componentes](https://support.microsoft.com/help/321185/how-to-determine-the-version-edition-and-update-level-of-sql-server-an)
