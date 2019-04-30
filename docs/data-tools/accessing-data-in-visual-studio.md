---
title: Acceso a datos y herramientas
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- "80025080"
helpviewer_keywords:
- data [Visual Studio]
- data access [Visual Studio]
- data [C#]
- ADO.NET, data access
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 16cbdb0a673f503dcee49b7a323d1453ee93532a
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62818233"
---
# <a name="access-data-in-visual-studio"></a>Acceder a datos en Visual Studio

En Visual Studio, puede crear aplicaciones que se conectan a los datos de prácticamente cualquier producto de base de datos o servicio, en cualquier formato, en cualquier lugar: en un equipo local, en una red de área local o en una nube pública, privada o híbrida.

Para las aplicaciones en JavaScript, Python, PHP, Ruby o C++, conéctese a datos como hace con cualquier otra cosa, obtención de bibliotecas y escribiendo código. Para aplicaciones. NET, Visual Studio proporciona herramientas que puede usar para explorar los orígenes de datos, crear modelos de objeto para almacenar y manipular los datos en memoria y enlazar datos a la interfaz de usuario. Microsoft Azure proporciona SDK para. NET, Java, Node.js, PHP, Python, Ruby y las aplicaciones móviles y herramientas de Visual Studio para conectarse a Azure Storage.

Las listas siguientes muestran algunos de los muchos sistemas de base de datos y almacenamiento que se pueden usar desde Visual Studio. El [Microsoft Azure](https://azure.microsoft.com/) ofertas son servicios de datos que incluyen todos los de aprovisionamiento y administración de almacén de datos subyacente. El **desarrollo de Azure** carga de trabajo en [Visual Studio 2017](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) le permite trabajar con almacenes de datos de Azure directamente desde Visual Studio.

![Carga de trabajo Desarrollo de Azure](media/azure-development-workload.png)

La mayoría de los otros productos SQL y NoSQL base de datos que se enumeran aquí puede hospedarse en un equipo local, en una red local o en Microsoft Azure en una máquina virtual. Si hospeda la base de datos en una máquina virtual de Microsoft Azure, usted es responsable de administrar la base de datos.

**Microsoft Azure**

- SQL Database
- Azure Cosmos DB
- Almacenamiento (blobs, tablas, colas, archivos)
- SQL Data Warehouse
- SQL Server Stretch Database
- StorSimple
- Y mucho más...

**SQL**

- SQL Server 2005-2016 (incluye Express y LocalDB)
- Firebird
- MariaDB
- MySQL
- Oracle
- PostgreSQL
- SQLite
- Y mucho más...

**NoSQL**

- Apache Cassandra
- CouchDB
- MongoDB
- NDatabase
- OrientDB|
- RavenDB
- VelocityDB
- Y mucho más...

::: moniker range="vs-2017"

Muchos proveedores de base de datos y de terceros admiten la integración de Visual Studio mediante paquetes de NuGet. Puede explorar las ofertas en nuget.org o mediante el Administrador de paquetes de NuGet en Visual Studio (**herramientas** > **Administrador de paquetes de NuGet** > **administrar paquetes NuGet Paquetes para la solución**). Otros productos de base de datos se integran con Visual Studio como una extensión. Puede examinar estas ofertas en el [Visual Studio Marketplace](https://marketplace.visualstudio.com/) o yendo a **herramientas** > **extensiones y actualizaciones** y, a continuación, seleccione  **Online** en el panel izquierdo del cuadro de diálogo. Para obtener más información, consulte [sistemas de base de datos Compatible para Visual Studio](../data-tools/installing-database-systems-tools-and-samples.md).

::: moniker-end

::: moniker range=">=vs-2019"

Muchos proveedores de base de datos y de terceros admiten la integración de Visual Studio mediante paquetes de NuGet. Puede explorar las ofertas en nuget.org o mediante el Administrador de paquetes de NuGet en Visual Studio (**herramientas** > **Administrador de paquetes de NuGet** > **administrar paquetes NuGet Paquetes para la solución**). Otros productos de base de datos se integran con Visual Studio como una extensión. Puede examinar estas ofertas en el [Visual Studio Marketplace](https://marketplace.visualstudio.com/) o yendo a **extensiones** > **administrar extensiones** y, a continuación, seleccione  **Online** en el panel izquierdo del cuadro de diálogo. Para obtener más información, consulte [sistemas de base de datos Compatible para Visual Studio](../data-tools/installing-database-systems-tools-and-samples.md).

::: moniker-end

> [!NOTE]
> El soporte extendido de SQL Server 2005 finalizó el 12 de abril de 2016. No hay ninguna garantía de que las herramientas de datos en Visual Studio 2015 y versiones posteriores seguirán funcionando con SQL Server 2005. Para obtener más información, consulte el [anuncio de fin de soporte para SQL Server 2005](https://www.microsoft.com/sql-server/sql-server-2005).

## <a name="net-languages"></a>Lenguajes de .NET

Todos los accesos de datos. NET, incluidas en .NET Core, se basa en ADO.NET, un conjunto de clases que define una interfaz para tener acceso a cualquier tipo de origen de datos relacional y no relacionales. Visual Studio tiene varias herramientas y diseñadores que funcionan con ADO.NET para conectarse a bases de datos, manipular los datos y presentarlos al usuario. La documentación de esta sección describe cómo usar estas herramientas. También puede programar directamente con los objetos de comando ADO.NET. Para obtener más información sobre cómo llamar directamente a las APIs ADO.NET, vea [ADO.NET](/dotnet/framework/data/adonet/index).

Para obtener documentación de acceso a datos relacionados con ASP.NET, consulte [trabajar con datos](https://www.asp.net/web-forms/overview/presenting-and-managing-data) en el sitio de ASP.NET. Para ver un tutorial sobre el uso de Entity Framework con ASP.NET MVC, consulte [Introducción a Entity Framework 6 Code First con MVC 5](/aspnet/mvc/overview/getting-started/getting-started-with-ef-using-mvc/creating-an-entity-framework-data-model-for-an-asp-net-mvc-application).

Aplicaciones universales de Windows Platform (UWP) en C# o Visual Basic pueden usar el SDK de Microsoft Azure para .NET para tener acceso a Azure Storage y otros servicios de Azure. La clase Windows.Web.HttpClient permite la comunicación con cualquier servicio RESTful. Para obtener más información, consulte [cómo conectarse a un servidor HTTP con Windows.Web.Http](https://msdn.microsoft.com/library/windows/apps/dn469430.aspx).

Para el almacenamiento de datos en el equipo local, el enfoque recomendado es usar SQLite, que se ejecuta en el mismo proceso que la aplicación. Si se necesita una capa de asignación relacional de objetos (ORM), puede usar Entity Framework. Para obtener más información, consulte [acceso a datos](/windows/uwp/data-access/index) en el Centro para desarrolladores de Windows.

Si se conecta a servicios de Azure, asegúrese de descargar la versión más reciente [herramientas de Azure SDK](https://azure.microsoft.com/downloads/).

### <a name="data-providers"></a>Proveedores de datos

Para que una base de datos poder usarse en ADO.NET, debe tener un personalizado *proveedor de datos ADO.NET* o de lo contrario, debe exponer una interfaz OLE DB u ODBC. Microsoft proporciona un [lista de proveedores de datos ADO.NET](https://docs.microsoft.com/dotnet/framework/data/adonet/ado-net-overview) para productos de SQL Server, así como los proveedores OLE DB y ODBC.

### <a name="data-modeling"></a>Modelado de datos

En. NET, tiene tres opciones para modelar y manipular datos en memoria que haya recuperado desde un origen de datos:

[Entity Framework](../data-tools/entity-data-model-tools-in-visual-studio.md) la tecnología Microsoft ORM preferida. Puede usar para programar con datos relacionales como objetos de primera clase. NET. Para las aplicaciones nuevas, debería ser la primera opción predeterminada cuando se necesita un modelo. Requiere soporte técnico personalizado desde el proveedor ADO.NET subyacente.

[LINQ to SQL](../data-tools/linq-to-sql-tools-in-visual-studio2.md) un mapeador relacional de objetos de generaciones anteriores. Funciona bien para escenarios menos complejos, pero ya no está en desarrollo activo.

[Los conjuntos de datos](../data-tools/dataset-tools-in-visual-studio.md) el más antiguo de las tres tecnologías de modelado. Está diseñado principalmente para el desarrollo rápido de aplicaciones de "formularios sobre datos" en el que no se procesar grandes cantidades de datos o realizar consultas complejas o transformaciones. Un objeto de conjunto de datos consta de objetos DataTable y DataRow que lógicamente se parecen mucho más que los objetos .NET a objetos de base de datos SQL. Para aplicaciones relativamente simples basadas en orígenes de datos SQL, conjuntos de datos todavía podrían ser una buena elección.

No hay ningún requisito para utilizar cualquiera de estas tecnologías. En algunos escenarios, especialmente cuando el rendimiento es crítico, puede simplemente usar un objeto DataReader para leer de la base de datos y copiar los valores que necesita en un objeto de colección como lista\<T >.

## <a name="native-c"></a>C++ nativo

Las aplicaciones de C++ que se conectan a SQL Server deben usar el [Microsoft® ODBC Driver 13.1 para SQL Server](https://www.microsoft.com/download/details.aspx?id=53339) en la mayoría de los casos. Si los servidores vinculados, a continuación, es necesario OLE DB y para que utilice el [SQL Server Native Client](/sql/relational-databases/native-client/sql-server-native-client). Puede tener acceso a otras bases de datos mediante el uso de [ODBC](https://docs.microsoft.com/sql/odbc/microsoft-open-database-connectivity-odbc?view=sql-server-2017) o controladores de OLE DB directamente. ODBC es la interfaz estándar de la base de datos actual, pero la mayoría de los sistemas de base de datos proporciona una funcionalidad personalizada que no se puede acceder a través de la interfaz ODBC. OLE DB es una tecnología de acceso a datos de COM heredada que se sigue admitiendo, pero no se recomienda para las aplicaciones nuevas. Para obtener más información, consulte [acceso a datos en Visual C++](/cpp/data/data-access-in-cpp).

Pueden usar programas de C++ que consumen servicios REST el [C++ REST SDK](https://github.com/Microsoft/cpprestsdk).

Pueden usar programas de C++ que funcionan con Microsoft Azure Storage los [cliente de Microsoft Azure Storage](https://www.nuget.org/packages/Microsoft.Azure.Storage.CPP).

Modelado de datos&mdash;Visual Studio no proporciona una capa ORM para C++. [ODB](https://www.codesynthesis.com/products/odb/) es un ORM popular de código abierto de C++.

Para más información sobre cómo conectarse a bases de datos de las aplicaciones de C++, vea [Visual Studio data tools para C++](../data-tools/visual-studio-data-tools-for-cpp.md). Para obtener más información acerca de las tecnologías de acceso a datos heredadas de Visual C++, vea [acceso a datos](/cpp/data/data-access-in-cpp).

## <a name="javascript"></a>JavaScript

[JavaScript en Visual Studio](/scripting/javascript/javascript-language-reference) es un lenguaje de primera clase para la creación de aplicaciones entre plataformas, aplicaciones para UWP, servicios en la nube, sitios Web y aplicaciones web. Puede usar Bower, Grunt, Gulp, npm y NuGet desde dentro de Visual Studio para instalar sus bibliotecas favoritas de JavaScript y productos de base de datos. Conectarse a Azure storage y servicios mediante la descarga de SDK desde la [sitio Web de Azure](https://azure.microsoft.com/). Edge.js es una biblioteca que se conecta el JavaScript del lado servidor (Node.js) a los orígenes de datos ADO.NET.

## <a name="python"></a>Python

Instalar [compatibilidad con Python en Visual Studio](../python/overview-of-python-tools-for-visual-studio.md) para crear aplicaciones de Python. La documentación de Azure tiene varios tutoriales sobre cómo conectarse a datos, incluidos los siguientes:

- [Django y SQL Database en Azure](/azure/app-service/app-service-web-get-started-python)
- [Django y MySQL en Azure](/azure/app-service-web/web-sites-python-ptvs-django-mysql)
- Trabajar con [blobs](/azure/storage/blobs/storage-quickstart-blobs-python), [archivos](/azure/storage/files/storage-python-how-to-use-file-storage), [colas](/azure/storage/queues/storage-python-how-to-use-queue-storage), y [tablas (COSMOS DB)](/azure/cosmos-db/table-storage-how-to-use-python).

## <a name="related-topics"></a>Temas relacionados

[Plataforma de AI Microsoft](https://azure.microsoft.com/overview/ai-platform/?v=17.42w)&mdash;proporciona una introducción a la nube inteligente de Microsoft, como Cortana Analytics Suite y soporte técnico para Internet de las cosas.

[Microsoft Azure Storage](/azure/storage/)&mdash;describe el almacenamiento de Azure y cómo crear aplicaciones con Azure blobs, tablas, colas y archivos.

[La base de datos de SQL Azure](/azure/sql-database/)&mdash;describe cómo conectarse a Azure SQL Database, una base de datos relacional como servicio.

[SQL Server Data Tools](/sql/ssdt/download-sql-server-data-tools-ssdt)&mdash;describe las herramientas que simplifican el diseño, exploración, prueba e implementación de aplicaciones de datos conectados y las bases de datos.

[ADO.NET](/dotnet/framework/data/adonet/index)&mdash;Describe la arquitectura de ADO.NET y cómo usar las clases de ADO.NET para administrar los datos de aplicación e interactuar con orígenes de datos y XML.

[ADO.NET Entity Framework](https://docs.microsoft.com/ef/ef6/)&mdash;se describe cómo crear aplicaciones de datos que permiten a los desarrolladores programar en un modelo conceptual en lugar de directamente en una base de datos relacional.

[Servicios de datos de WCF 4.5](/dotnet/framework/data/wcf/index)&mdash;se describe cómo usar [!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)] para implementar servicios de datos en la web o en una intranet que implementan la [Open Data Protocol (OData)](https://www.odata.org/).

[Datos en soluciones de Office](../vsto/data-in-office-solutions.md)&mdash;contiene vínculos a temas que explican cómo funcionan los datos en soluciones de Office. Se incluye información sobre la programación orientada a esquema, el almacenamiento de datos en caché y el acceso a datos en el servidor.

[LINQ (Language-Integrated Query)](/dotnet/csharp/linq/)&mdash;describe las capacidades de consulta integradas en C# y Visual Basic y el modelo común para consultar bases de datos relacionales, documentos XML, conjuntos de datos y colecciones en memoria.

[Herramientas XML en Visual Studio](../xml-tools/xml-tools-in-visual-studio.md)&mdash;explica cómo trabajar con las características XML de .NET Framework de datos, la depuración de XSLT, XML y la arquitectura de las consultas XML.

[Documentos y datos XML](/dotnet/standard/data/xml/index)&mdash;proporciona información general sobre un conjunto completo e integrado de clases que funcionan con documentos XML y datos de .NET Framework.
