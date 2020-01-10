---
title: Acceso a datos
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
f1_keywords:
- "80025080"
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- data [Visual Studio]
- data access [Visual Studio]
- data [C#]
- ADO.NET, data access
ms.assetid: 9812a6d5-23d2-4427-8b98-70a2abfec3bc
caps.latest.revision: 103
author: jillre
ms.author: jillfra
manager: jillfra
robots: noindex,nofollow
ms.openlocfilehash: 065a6ae3901f2426db6556cb19e80f543cb8a78f
ms.sourcegitcommit: c150d0be93b6f7ccbe9625b41a437541502560f5
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/10/2020
ms.locfileid: "75846665"
---
# <a name="accessing-data-in-visual-studio"></a>Acceso a datos en Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

En Visual Studio, puede crear aplicaciones que se conecten a datos en prácticamente cualquier producto o servicio de base de datos, en cualquier formato y en cualquier lugar: en un equipo local, en una red de área local o en una nube pública, privada o híbrida.

 En el caso de las aplicaciones de JavaScript, Python, PHP C++, Ruby o, se conecta a los datos de la misma forma que hace nada más, mediante la obtención de bibliotecas y la escritura de código. En el caso de las aplicaciones .NET, Visual Studio proporciona herramientas que puede usar para explorar orígenes de datos, crear modelos de objetos para almacenar y manipular datos en memoria y enlazar datos a la interfaz de usuario.     Microsoft Azure proporciona SDK para .NET, Java, node. js, PHP, Python, Ruby y Mobile Apps, y herramientas de Visual Studio para conectarse a Azure Storage.

 En las listas siguientes se muestran solo algunos de los diversos sistemas de base de datos y almacenamiento que se pueden usar desde Visual Studio. Las ofertas [Microsoft Azure](https://azure.microsoft.com/) son servicios de datos que incluyen todo el aprovisionamiento y la administración del almacén de datos subyacente.  [Azure Tools para Visual Studio](https://www.visualstudio.com/features/azure-tools-vs.aspx) es un componente opcional que le permite trabajar con almacenes de datos de Azure directamente desde Visual Studio. La mayoría de los demás productos de base de datos SQL y NoSQL que se enumeran aquí se pueden hospedar en un equipo local, en una red local o en Microsoft Azure en una máquina virtual. En este escenario, usted es responsable de administrar la base de datos.

 **Microsoft Azure**

||||
|-|-|-|
|Base de datos SQL|DocumentDB|Almacenamiento (blobs, tablas, colas, archivos)|
|SQL Data Warehouse|SQL Server Stretch Database|StorSimple|

 Y mucho más...

 **SQL**

||||
|-|-|-|
|SQL Server 2005 – 2016, incluido Express y LocalDB|Firebird|MariaDB|
|MySQL|Oracle|PostgreSQL|
|SQLite|||

 Y mucho más...

 **NoSQL**

||||
|-|-|-|
|Apache Cassandra|CouchDB|MongoDB|
|NDatabase|OrientDB|RavenDB|
|VelocityDB|||

 Y mucho más...

 Muchos proveedores de bases de datos y terceros admiten la integración de Visual Studio mediante paquetes de NuGet. Puede explorar las ofertas en nuget.org o a través del administrador de paquetes NuGet en Visual Studio (**herramientas** > **Administrador de paquetes Nuget** > **administrar paquetes Nuget para la solución**). Otros productos de base de datos se integran con Visual Studio como una extensión.   Puede examinar estas ofertas en la galería de Visual Studio; para ello, vaya a **herramientas** > **extensiones y actualizaciones** y, a continuación, seleccione **en línea** en el panel izquierdo del cuadro de diálogo.  Para obtener más información, vea [instalar sistemas de base de datos, herramientas y ejemplos](../data-tools/installing-database-systems-tools-and-samples.md).

> [!NOTE]
> El soporte extendido de SQL Server 2005 finalizó el 12 de abril de 2016.   No hay ninguna garantía de que las herramientas de datos de Visual Studio 2015 y versiones posteriores seguirán funcionando con SQL Server 2005 después de esta fecha. Para obtener más información, consulte el [anuncio de final de soporte técnico para SQL Server 2005](https://www.microsoft.com/sql-server/sql-server-2005).

### <a name="net-languages"></a>Lenguajes .NET
 Todo el acceso a datos de .NET, incluido en .NET Core, se basa en ADO.NET, un conjunto de clases que define una interfaz para tener acceso a cualquier tipo de origen de datos, tanto relacionales como no relacionales. Visual Studio tiene varias herramientas y diseñadores que funcionan con ADO.NET para ayudarle a conectarse a bases de datos, manipular los datos y presentar los datos al usuario. En la documentación de esta sección se describe cómo usar esas herramientas. También puede programar directamente con los objetos de comando ADO.NET. Para obtener más información sobre cómo llamar a las API de ADO.NET directamente, vea [ADO.net](https://msdn.microsoft.com/library/e80y5yhx\(v=vs.110\).aspx) en MSDN Library.

 Para obtener documentación sobre el acceso a datos relacionada específicamente con ASP.NET, consulte [trabajar con datos](https://docs.microsoft.com/aspnet/web-forms/overview/presenting-and-managing-data/) en el sitio de ASP.net. Para ver un tutorial sobre el uso de Entity Framework con ASP.NET MVC, consulte [Introducción con Entity Framework 6 Code First con MVC 5](https://docs.microsoft.com/aspnet/mvc/overview/getting-started/getting-started-with-ef-using-mvc/creating-an-entity-framework-data-model-for-an-asp-net-mvc-application).

 Las aplicaciones Plataforma universal de Windows (UWP) C# en o Visual Basic pueden usar el Microsoft Azure SDK para .net para acceder a Azure Storage y a otros servicios de Azure. La clase Windows. Web. HttpClient permite la comunicación con cualquier servicio RESTful. Para obtener más información, consulte [cómo conectarse a un servidor http mediante Windows. Web. http](https://msdn.microsoft.com/library/windows/apps/dn469430.aspx).

 En el caso del almacenamiento de datos en el equipo local, el enfoque recomendado es usar SQLite, que se ejecuta en el mismo proceso que la aplicación. Si se requiere una capa de asignación relacional de objetos (ORM), puede usar Entity Framework. Para obtener más información, vea [acceso a datos](https://msdn.microsoft.com/windows/uwp/data-access/index) en el centro para desarrolladores de Windows.

 Si va a conectarse a los servicios de Azure, asegúrese de descargar las últimas [herramientas de Azure SDK](https://azure.microsoft.com/downloads/).

#### <a name="data-providers"></a>Proveedores de datos
 Para que una base de datos se pueda usar en ADO.NET, debe tener un *proveedor de datos ADO.net* personalizado, o bien debe exponer una interfaz ODBC o OLE DB. Microsoft proporciona una [lista de proveedores de datos de ADO.net](https://msdn.microsoft.com/data/dd363565) para productos SQL Server, así como proveedores de OLE DB y ODBC.

#### <a name="data-modeling"></a>Modelado de datos
 En .NET, dispone de tres opciones para el modelado y la manipulación de datos en la memoria después de haberlos recuperado de un origen de datos:

 Entity Framework la tecnología de Microsoft ORM preferida. Puede utilizarlo para programar datos relacionales como objetos de primera clase .NET. En el caso de las aplicaciones nuevas, debe ser la primera opción predeterminada cuando se requiere un modelo. Requiere compatibilidad personalizada del proveedor ADO.NET subyacente.

 LINQ to SQL un asignador relacional de objetos de generación anterior. Funciona bien en escenarios menos complejos, pero ya no está en desarrollo activo.

 Establece la configuración más antigua de las tres tecnologías de modelado. Está diseñado principalmente para el desarrollo rápido de aplicaciones de "formularios sobre datos" en las que no se procesan grandes cantidades de datos o se realizan consultas o transformaciones complejas. Un objeto DataSet se compone de objetos DataTable y DataRow que se parecen lógicamente a objetos de base de datos SQL, mucho más que objetos .NET. En el caso de aplicaciones relativamente sencillas basadas en orígenes de datos SQL, es posible que los conjuntos de datos sigan siendo una buena elección.

 No es necesario usar ninguna de estas tecnologías. En algunos escenarios, especialmente en los que el rendimiento es crítico, puede simplemente usar un objeto DataReader para leer de la base de datos y copiar los valores que necesita en un objeto de colección, como List\<T >.

### <a name="native-c"></a>C++ nativo
 C++las aplicaciones que se conectan a SQL Server deben usar el [SQL Server Native Client](https://msdn.microsoft.com/sqlserver/aa937733.aspx). Puede tener acceso a otras bases de datos mediante los controladores [ODBC](https://msdn.microsoft.com/library/ms710252\(v=vs.85\).aspx) o OLE DB directamente. ODBC es la interfaz de base de datos estándar actual, pero la mayoría de los sistemas de base de datos proporcionan funcionalidad personalizada a la que no se puede tener acceso a través de la interfaz ODBC.  OLE DB es una tecnología de acceso a datos COM heredada que todavía se admite pero no se recomienda para las nuevas aplicaciones.  Para obtener más información, vea [acceso a datos](https://msdn.microsoft.com/library/a9455752-39c4-4457-b14e-197772d3df0b).

 C++los programas que consumen servicios REST pueden usar el [ C++ SDK de REST](https://github.com/Microsoft/cpprestsdk).

 C++los programas que funcionan con Microsoft Azure Storage pueden utilizar el [cliente de Microsoft Azure Storage](https://www.nuget.org/packages/wastorage).

#### <a name="data-modeling"></a>Modelado de datos
 Visual Studio no proporciona una capa ORM para C++.  [ODB](https://www.codesynthesis.com/products/odb/) es un conocido ORM de código abierto para C++.

 Para obtener más información sobre las C++ tecnologías de acceso a datos de Visual heredado, vea [acceso a datos](https://msdn.microsoft.com/library/a9455752-39c4-4457-b14e-197772d3df0b)

### <a name="javascript"></a>JavaScript
 [JavaScript en Visual Studio](https://msdn.microsoft.com/library/hh334522.aspx) es un lenguaje de primera clase para compilar aplicaciones multiplataforma, aplicaciones para UWP, servicios en la nube, sitios web y aplicaciones Web. Puede usar Bower, impesado, Gulp, NPM y NuGet desde Visual Studio para instalar sus bibliotecas de JavaScript y productos de base de datos favoritos. Para conectarse a Azure Storage y a los servicios, descargue los SDK desde el [sitio web de Azure](https://azure.microsoft.com/).  Edge. js es una biblioteca que conecta JavaScript del lado servidor (node. js) con los orígenes de datos de ADO.NET.

### <a name="python"></a>Plantillas de
 Instale [herramientas de Python para Visual Studio](http://microsoft.github.io/PTVS/) junto con su marco de Python favorito para crear aplicaciones de CPython o IronPython (.net).  El sitio web de Herramientas de Python para Visual Studio tiene varios tutoriales sobre la conexión a datos, como [Django y SQL Database en Azure](https://github.com/Microsoft/PTVS/wiki/Django-and-SQL-Database-on-Azure), [Django y MySQL en Azure](https://github.com/Microsoft/PTVS/wiki/Django-and-MySQL-on-Azure) y [en biberón y MongoDB en Azure](https://github.com/Microsoft/PTVS/wiki/Bottle-and-MongoDB-on-Azure).

## <a name="in-this-section"></a>En esta sección
 [Instalación de sistemas de base de datos, herramientas y ejemplos](../data-tools/installing-database-systems-tools-and-samples.md) Describe cómo obtener los productos de base de datos y las extensiones o controladores de Visual Studio que los admiten, y dónde buscar las bases de datos de ejemplo para fines de experimentación y aprendizaje.

 [Visual Studio Data Tools para .net](https://msdn.microsoft.com/6b145922-2f00-47db-befc-bf351b4809a1) Describe cómo usar las ventanas de herramientas de Visual Studio para conectarse a orígenes de datos, crear conjuntos de datos o modelos de Entity Framework y enlazar los datos a controles de interfaz de usuario.

## <a name="related-topics"></a>Temas relacionados
 [Datos, dispositivos y análisis](https://msdn.microsoft.com/data-and-devices) Proporciona una introducción a la nube inteligente de Microsoft, incluido el conjunto de análisis de Cortana y soporte para Internet de las cosas.

 [Microsoft Azure Storage](/azure/storage/) Describe Azure Storage y cómo crear aplicaciones con blobs, tablas, colas y archivos de Azure.

 [Azure SQL Database](https://azure.microsoft.com/documentation/services/sql-database/) Describe cómo conectarse a Azure SQL Database, una base de datos relacional como servicio.

 [SQL Server Data Tools](https://msdn.microsoft.com/library/hh272686\(v=vs.103\).aspx) Describe las herramientas que simplifican el diseño, la exploración, las pruebas y la implementación de aplicaciones y bases de datos conectadas a datos.

 [ADO.net](https://msdn.microsoft.com/library/5b96ed06-9759-4966-a797-a1d5f6ee50ca) Describe la arquitectura de ADO.NET y cómo usar las clases ADO.NET para administrar datos de aplicación e interactuar con orígenes de datos y XML.

 [Entity Framework ADO.net](https://msdn.microsoft.com/data/ef) Describe cómo crear aplicaciones de datos que permiten a los programadores programar con un modelo conceptual en lugar de hacerlo directamente en una base de datos relacional.

 [WCF Data Services 4,5](https://msdn.microsoft.com/library/73d2bec3-7c92-4110-b905-11bb0462357a) Describe cómo usar [!INCLUDE[ssAstoria](../includes/ssastoria-md.md)] para implementar servicios de datos en Internet o en una intranet que implementa el [Open Data Protocol (OData)](https://www.odata.org/).

 [Datos en soluciones de Office](https://msdn.microsoft.com/library/8478c095-864b-4ed3-8a70-1fc19b411c6a) Contiene vínculos a temas que explican cómo funcionan los datos en las soluciones de Office. Se incluye información sobre la programación orientada a esquema, el almacenamiento de datos en caché y el acceso a datos en el servidor.

 [LINQ (Language-Integrated Query)](https://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d) Describe las funciones de consulta integradas en C# y Visual Basic, así como el modelo común para consultar bases de datos relacionales, documentos XML, conjuntos de datos y colecciones en memoria.

 [Herramientas XML en Visual Studio](../xml-tools/xml-tools-in-visual-studio.md) Explica cómo trabajar con datos XML, depurar XSLT, .NET Framework características XML y la arquitectura de la consulta XML.

 [Documentos y datos XML](https://msdn.microsoft.com/library/e695047f-3c0f-4045-8708-5baea91cc380) Proporciona información general sobre un conjunto completo e integrado de clases que funcionan con datos y documentos XML en el .NET Framework.
