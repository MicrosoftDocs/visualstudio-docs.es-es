---
title: Trabajo con datos en Visual Studio
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- data [Visual Studio]
- data access [Visual Studio]
- data [C#]
- ADO.NET, data access
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 7c7aa1544f998a88424c0087fadceab63757d23b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "77272089"
---
# <a name="work-with-data-in-visual-studio"></a>Trabajo con datos en Visual Studio

En Visual Studio, puede crear aplicaciones que se conecten a datos en prácticamente cualquier producto o servicio de base de datos, en cualquier formato y en cualquier lugar: en un equipo local, en una red de área local o en una nube pública, privada o híbrida.

En el caso de las aplicaciones de JavaScript, Python, PHP, Ruby o C++, se conecta a los datos del mismo modo que hace nada más, mediante la obtención de bibliotecas y la escritura de código. En el caso de las aplicaciones .NET, Visual Studio proporciona herramientas que puede usar para explorar orígenes de datos, crear modelos de objetos para almacenar y manipular datos en memoria y enlazar datos a la interfaz de usuario. Microsoft Azure proporciona SDK para .NET, Java, Node.js, PHP, Python, Ruby y Mobile Apps, y herramientas de Visual Studio para conectarse a Azure Storage.

::: moniker range="vs-2017"
En las listas siguientes se muestran solo algunos de los diversos sistemas de base de datos y almacenamiento que se pueden usar desde Visual Studio. Las ofertas [Microsoft Azure](https://azure.microsoft.com/) son servicios de datos que incluyen todo el aprovisionamiento y la administración del almacén de datos subyacente. La carga de trabajo de **desarrollo de Azure** en [Visual Studio 2017](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) le permite trabajar con almacenes de datos de Azure directamente desde Visual Studio.
::: moniker-end
::: moniker range=">=vs-2019"
En las listas siguientes se muestran solo algunos de los diversos sistemas de base de datos y almacenamiento que se pueden usar desde Visual Studio. Las ofertas [Microsoft Azure](https://azure.microsoft.com/) son servicios de datos que incluyen todo el aprovisionamiento y la administración del almacén de datos subyacente. La carga de trabajo de **desarrollo de Azure** en [Visual Studio 2019](https://visualstudio.microsoft.com/downloads) le permite trabajar con almacenes de datos de Azure directamente desde Visual Studio.
::: moniker-end

![Carga de trabajo Desarrollo de Azure](media/azure-development-workload.png)

La mayoría de los demás productos de base de datos SQL y NoSQL que se enumeran aquí se pueden hospedar en un equipo local, en una red local o en Microsoft Azure en una máquina virtual. Si hospeda la base de datos en una máquina virtual Microsoft Azure, es responsable de administrar la propia base de datos.

**Microsoft Azure**

- SQL Database
- Azure Cosmos DB
- Almacenamiento (blobs, tablas, colas, archivos)
- SQL Data Warehouse
- SQL Server Stretch Database
- StorSimple
- Y mucho más.

**SQL**

- SQL Server 2005-2016 (incluye Express y LocalDB)
- Firebird
- MariaDB
- MySQL
- Oracle
- PostgreSQL
- SQLite
- Y mucho más.

**NoSQL**

- Apache Cassandra
- CouchDB
- MongoDB
- NDatabase
- OrientDB|
- RavenDB
- VelocityDB
- Y mucho más.

::: moniker range="vs-2017"

Muchos proveedores de bases de datos y terceros admiten la integración de Visual Studio mediante paquetes de NuGet. Puede explorar las ofertas en Nuget.org o a través del administrador de paquetes Nuget en Visual Studio (**herramientas**administrador de paquetes Nuget  >  **NuGet Package Manager**  >  **administrar paquetes Nuget para la solución**). Otros productos de base de datos se integran con Visual Studio como una extensión. Puede examinar estas ofertas en el [Visual Studio Marketplace](https://marketplace.visualstudio.com/) o desplazándose hasta **herramientas**  >  **extensiones y actualizaciones** y, a continuación, seleccionando en **línea** en el panel izquierdo del cuadro de diálogo. Para obtener más información, vea [sistemas de base de datos compatibles para Visual Studio](../data-tools/installing-database-systems-tools-and-samples.md).

::: moniker-end

::: moniker range=">=vs-2019"

Muchos proveedores de bases de datos y terceros admiten la integración de Visual Studio mediante paquetes de NuGet. Puede explorar las ofertas en Nuget.org o a través del administrador de paquetes Nuget en Visual Studio (**herramientas**administrador de paquetes Nuget  >  **NuGet Package Manager**  >  **administrar paquetes Nuget para la solución**). Otros productos de base de datos se integran con Visual Studio como una extensión. Puede examinar estas ofertas en el [Visual Studio Marketplace](https://marketplace.visualstudio.com/) o yendo a **extensiones**  >  **administrar extensiones** y seleccionando en **línea** en el panel izquierdo del cuadro de diálogo. Para obtener más información, vea [sistemas de base de datos compatibles para Visual Studio](../data-tools/installing-database-systems-tools-and-samples.md).

::: moniker-end

> [!NOTE]
> El soporte extendido de SQL Server 2005 finalizó el 12 de abril de 2016. No hay ninguna garantía de que las herramientas de datos de Visual Studio 2015 y versiones posteriores seguirán funcionando con SQL Server 2005. Para obtener más información, consulte el [anuncio de final de soporte técnico para SQL Server 2005](https://www.microsoft.com/sql-server/sql-server-2005).

## <a name="net-languages"></a>Lenguajes .NET

Todo el acceso a datos de .NET, incluido en .NET Core, se basa en ADO.NET, un conjunto de clases que define una interfaz para tener acceso a cualquier tipo de origen de datos, tanto relacionales como no relacionales. Visual Studio tiene varias herramientas y diseñadores que funcionan con ADO.NET para ayudarle a conectarse a bases de datos, manipular los datos y presentar los datos al usuario. En la documentación de esta sección se describe cómo usar esas herramientas. También puede programar directamente con los objetos de comando ADO.NET. Para obtener más información sobre cómo llamar directamente a las API de ADO.NET, consulte [ADO.net](/dotnet/framework/data/adonet/index).

Para obtener documentación sobre el acceso a datos relacionado con ASP.NET, consulte [trabajar con datos](https://www.asp.net/web-forms/overview/presenting-and-managing-data) en el sitio de ASP.net. Para ver un tutorial sobre el uso de Entity Framework con ASP.NET MVC, consulte [Introducción con Entity Framework 6 Code First con MVC 5](/aspnet/mvc/overview/getting-started/getting-started-with-ef-using-mvc/creating-an-entity-framework-data-model-for-an-asp-net-mvc-application).

Las aplicaciones Plataforma universal de Windows (UWP) en C# o Visual Basic pueden usar el Microsoft Azure SDK para .NET para tener acceso a Azure Storage y a otros servicios de Azure. La clase Windows. Web. HttpClient permite la comunicación con cualquier servicio RESTful. Para obtener más información, consulte [cómo conectarse a un servidor http mediante Windows. Web. http](https://msdn.microsoft.com/library/windows/apps/dn469430.aspx).

En el caso del almacenamiento de datos en el equipo local, el enfoque recomendado es usar SQLite, que se ejecuta en el mismo proceso que la aplicación. Si se requiere una capa de asignación relacional de objetos (ORM), puede usar Entity Framework. Para obtener más información, vea [acceso a datos](/windows/uwp/data-access/index) en el centro para desarrolladores de Windows.

Si va a conectarse a los servicios de Azure, asegúrese de descargar las últimas [herramientas de Azure SDK](https://azure.microsoft.com/downloads/).

### <a name="data-providers"></a>Proveedores de datos

Para que una base de datos se pueda usar en ADO.NET, debe tener un *proveedor de datos ADO.net* personalizado, o bien debe exponer una interfaz ODBC o OLE DB. Microsoft proporciona una [lista de proveedores de datos de ADO.net](/dotnet/framework/data/adonet/ado-net-overview) para productos SQL Server, así como proveedores de OLE DB y ODBC.

### <a name="data-modeling"></a>Modelado de datos

En .NET, dispone de tres opciones para el modelado y la manipulación de datos en la memoria después de haberlos recuperado de un origen de datos:

[Entity Framework](../data-tools/entity-data-model-tools-in-visual-studio.md) La tecnología de Microsoft ORM preferida. Puede utilizarlo para programar datos relacionales como objetos de primera clase .NET. En el caso de las aplicaciones nuevas, debe ser la primera opción predeterminada cuando se requiere un modelo. Requiere compatibilidad personalizada del proveedor ADO.NET subyacente.

[LINQ to SQL](../data-tools/linq-to-sql-tools-in-visual-studio2.md) Un asignador relacional de objetos de generación anterior. Funciona bien en escenarios menos complejos, pero ya no está en desarrollo activo.

[Conjuntos de valores](../data-tools/dataset-tools-in-visual-studio.md) La más antigua de las tres tecnologías de modelado. Está diseñado principalmente para el desarrollo rápido de aplicaciones de "formularios sobre datos" en las que no se procesan grandes cantidades de datos o se realizan consultas o transformaciones complejas. Un objeto DataSet se compone de objetos DataTable y DataRow que se parecen lógicamente a objetos de base de datos SQL, mucho más que objetos .NET. En el caso de aplicaciones relativamente sencillas basadas en orígenes de datos SQL, es posible que los conjuntos de datos sigan siendo una buena elección.

No es necesario usar ninguna de estas tecnologías. En algunos escenarios, especialmente cuando el rendimiento es crítico, puede simplemente usar un objeto DataReader para leer de la base de datos y copiar los valores que necesita en un objeto de colección como List \<T> .

## <a name="native-c"></a>C++ nativo

Las aplicaciones de C++ que se conectan a SQL Server deben usar el [controlador ODBC de Microsoft® 13,1 para SQL Server](https://www.microsoft.com/download/details.aspx?id=53339) en la mayoría de los casos. Si los servidores están vinculados, OLE DB es necesario y, para ello, se usa el [SQL Server Native Client](/sql/relational-databases/native-client/sql-server-native-client). Puede tener acceso a otras bases de datos mediante los controladores [ODBC](/sql/odbc/microsoft-open-database-connectivity-odbc?view=sql-server-2017) o OLE DB directamente. ODBC es la interfaz de base de datos estándar actual, pero la mayoría de los sistemas de base de datos proporcionan funcionalidad personalizada a la que no se puede tener acceso a través de la interfaz ODBC. OLE DB es una tecnología de acceso a datos COM heredada que todavía se admite pero no se recomienda para las nuevas aplicaciones. Para obtener más información, vea [acceso a datos en Visual C++](/cpp/data/data-access-in-cpp).

Los programas de c++ que usan servicios REST pueden usar el [SDK de C++ Rest](https://github.com/Microsoft/cpprestsdk).

Los programas de C++ que funcionan con Microsoft Azure Storage pueden utilizar el [cliente de Microsoft Azure Storage](https://www.nuget.org/packages/Microsoft.Azure.Storage.CPP).

El modelado &mdash; de datos de Visual Studio no proporciona una capa ORM para C++. [ODB](https://www.codesynthesis.com/products/odb/) es un conocido ORM de código abierto para C++.

Para obtener más información sobre cómo conectarse a bases de datos desde aplicaciones de C++, vea [Visual Studio Data Tools para c++](../data-tools/visual-studio-data-tools-for-cpp.md). Para obtener más información sobre las tecnologías de acceso a datos heredadas Visual C++, consulte [Data Access](/cpp/data/data-access-in-cpp).

## <a name="javascript"></a>JavaScript

[JavaScript en Visual Studio](/scripting/javascript/javascript-language-reference) es un lenguaje de primera clase para compilar aplicaciones multiplataforma, aplicaciones para UWP, servicios en la nube, sitios web y aplicaciones Web. Puede usar Bower, impesado, Gulp, NPM y NuGet desde Visual Studio para instalar sus bibliotecas de JavaScript y productos de base de datos favoritos. Para conectarse a Azure Storage y a los servicios, descargue los SDK desde el [sitio web de Azure](https://azure.microsoft.com/). Edge.js es una biblioteca que conecta JavaScript del lado servidor (Node.js) con los orígenes de datos de ADO.NET.

## <a name="python"></a>Python

Instale la [compatibilidad con Python en Visual Studio](../python/overview-of-python-tools-for-visual-studio.md) para crear aplicaciones de Python. La documentación de Azure incluye varios tutoriales sobre la conexión a datos, entre los que se incluyen los siguientes:

- [Django y SQL Database en Azure](/azure/app-service/app-service-web-get-started-python)
- [Django y MySQL en Azure](/azure/app-service-web/web-sites-python-ptvs-django-mysql)
- Trabajar con [blobs](/azure/storage/blobs/storage-quickstart-blobs-python), [archivos](/azure/storage/files/storage-python-how-to-use-file-storage), [colas](/azure/storage/queues/storage-python-how-to-use-queue-storage)y [tablas (Cosmo dB)](/azure/cosmos-db/table-storage-how-to-use-python).

## <a name="related-topics"></a>Temas relacionados

Plataforma de inteligencia [artificial de Microsoft](https://azure.microsoft.com/overview/ai-platform/?v=17.42w) &mdash; Proporciona una introducción a la nube inteligente de Microsoft, incluido el conjunto de análisis de Cortana y soporte para Internet de las cosas.

[Microsoft Azure Storage](/azure/storage/) &mdash; Describe Azure Storage y cómo crear aplicaciones con blobs, tablas, colas y archivos de Azure.

[Azure SQL Database](/azure/sql-database/) &mdash; Describe cómo conectarse a Azure SQL Database, una base de datos relacional como servicio.

[SQL Server Data Tools](/sql/ssdt/download-sql-server-data-tools-ssdt) &mdash; Describe las herramientas que simplifican el diseño, la exploración, las pruebas y la implementación de aplicaciones y bases de datos conectadas a datos.

[ADO.net](/dotnet/framework/data/adonet/index) &mdash; Describe la arquitectura de ADO.NET y cómo usar las clases ADO.NET para administrar datos de aplicación e interactuar con orígenes de datos y XML.

[Entity Framework ADO.net](/ef/ef6/) &mdash; Describe cómo crear aplicaciones de datos que permiten a los programadores programar con un modelo conceptual en lugar de hacerlo directamente en una base de datos relacional.

[WCF Data Services 4,5](/dotnet/framework/data/wcf/index) &mdash; Describe cómo usar [!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)] para implementar servicios de datos en Internet o en una intranet que implementa el [Open Data Protocol (OData)](https://www.odata.org/).

[Datos en soluciones](../vsto/data-in-office-solutions.md) &mdash; de Office Contiene vínculos a temas que explican cómo funcionan los datos en las soluciones de Office. Se incluye información sobre la programación orientada a esquema, el almacenamiento de datos en caché y el acceso a datos en el servidor.

[LINQ (Language-Integrated Query)](/dotnet/csharp/linq/) &mdash; Describe las funciones de consulta integradas en C# y Visual Basic, así como el modelo común para consultar bases de datos relacionales, documentos XML, conjuntos de datos y colecciones en memoria.

[Herramientas XML en Visual Studio](../xml-tools/xml-tools-in-visual-studio.md) &mdash; Describe el trabajo con datos XML, la depuración de XSLT, las características XML de .NET y la arquitectura de la consulta XML.

[Documentos y datos XML](/dotnet/standard/data/xml/index) &mdash; Proporciona información general sobre un conjunto completo e integrado de clases que funcionan con datos y documentos XML en .NET.
