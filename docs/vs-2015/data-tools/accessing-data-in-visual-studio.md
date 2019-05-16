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
author: gewarren
ms.author: gewarren
manager: jillfra
robots: noindex,nofollow
ms.openlocfilehash: 7f13a97adbec1da1bd0f279e14cf510532b9c62f
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/15/2019
ms.locfileid: "65688624"
---
# <a name="accessing-data-in-visual-studio"></a>Acceso a datos en Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

En Visual Studio, puede crear aplicaciones que se conectan a los datos de prácticamente cualquier producto de base de datos o servicio, en cualquier formato, en cualquier lugar: en un equipo local, en una red de área local o en una nube pública, privada o híbrida.

 Para las aplicaciones en JavaScript, Python, PHP, Ruby o C++, conéctese a datos como hace con cualquier otra cosa, obtención de bibliotecas y escribiendo código. Para aplicaciones. NET, Visual Studio proporciona herramientas que puede usar para explorar los orígenes de datos, crear modelos de objeto para almacenar y manipular los datos en memoria y enlazar datos a la interfaz de usuario.     Microsoft Azure proporciona SDK para. NET, Java, Node.js, PHP, Python, Ruby y las aplicaciones móviles y herramientas de Visual Studio para conectarse a Azure Storage.

 Las listas siguientes muestran algunos de los muchos sistemas de base de datos y almacenamiento que se pueden usar desde Visual Studio. El [Microsoft Azure](https://azure.microsoft.com/) ofertas son servicios de datos que incluyen todos los de aprovisionamiento y administración de almacén de datos subyacente.  [Azure Tools para Visual Studio](https://www.visualstudio.com/features/azure-tools-vs.aspx) es un componente opcional que le permite trabajar con almacenes de datos de Azure directamente desde Visual Studio. La mayoría de los otros productos SQL y NoSQL base de datos que se enumeran aquí puede hospedarse en un equipo local, en una red local o en Microsoft Azure en una máquina virtual. En este escenario, usted es responsable de administrar la base de datos.

 **Microsoft Azure**

||||
|-|-|-|
|SQL Database|DocumentDB|Almacenamiento (blobs, tablas, colas, archivos)|
|SQL Data Warehouse|SQL Server Stretch Database|StorSimple|

 Y mucho más...

 **SQL**

||||
|-|-|-|
|SQL Server 2005 – 2016, incluida Express y LocalDB|Firebird|MariaDB|
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

 Muchos proveedores de base de datos y de terceros admiten la integración de Visual Studio mediante paquetes de NuGet. Puede explorar las ofertas en nuget.org o mediante el Administrador de paquetes de NuGet en Visual Studio (**herramientas** > **Administrador de paquetes de NuGet** > **administrar paquetes NuGet Paquetes para la solución**). Otros productos de base de datos se integran con Visual Studio como una extensión.   Puede examinar estas ofertas en la Galería de Visual Studio, vaya a **herramientas** > **extensiones y actualizaciones** y, a continuación, seleccione **Online** en la izquierda panel del cuadro de diálogo.  Para obtener más información, consulte [instalar sistemas de base de datos, herramientas y ejemplos](../data-tools/installing-database-systems-tools-and-samples.md).

> [!NOTE]
> El soporte extendido de SQL Server 2005 finalizó el 12 de abril de 2016.   No hay ninguna garantía de que las herramientas de datos en Visual Studio 2015 y versiones posteriores seguirán funcionando con SQL Server 2005 después de esta fecha. Para obtener más información, consulte el [anuncio de fin de soporte para SQL Server 2005](https://www.microsoft.com/sql-server/sql-server-2005).

### <a name="net-languages"></a>Lenguajes de .NET
 Todos los accesos de datos. NET, incluidas en .NET Core, se basa en ADO.NET, un conjunto de clases que define una interfaz para tener acceso a cualquier tipo de origen de datos relacional y no relacionales. Visual Studio tiene varias herramientas y diseñadores que funcionan con ADO.NET para conectarse a bases de datos, manipular los datos y presentarlos al usuario. La documentación de esta sección describe cómo usar estas herramientas. También puede programar directamente con los objetos de comando ADO.NET. Para obtener más información sobre cómo llamar directamente a las APIs ADO.NET, vea [ADO.NET](https://msdn.microsoft.com/library/e80y5yhx\(v=vs.110\).aspx) en MSDN Library.

 Para obtener documentación de acceso a datos relacionados específicamente con ASP.NET, consulte [trabajar con datos](http://www.asp.net/web-forms/overview/presenting-and-managing-data) en el sitio de ASP.NET. Para ver un tutorial sobre el uso de Entity Framework con ASP.NET MVC, consulte [Introducción a Entity Framework 6 Code First con MVC 5](http://www.asp.net/mvc/overview/getting-started/getting-started-with-ef-using-mvc/creating-an-entity-framework-data-model-for-an-asp-net-mvc-application).

 Aplicaciones universales de Windows Platform (UWP) en C# o Visual Basic pueden usar el SDK de Microsoft Azure para .NET para tener acceso a Azure Storage y otros servicios de Azure. La clase Windows.Web.HttpClient permite la comunicación con cualquier servicio RESTful. Para obtener más información, consulte [cómo conectarse a un servidor HTTP con Windows.Web.Http](https://msdn.microsoft.com/library/windows/apps/dn469430.aspx).

 Para el almacenamiento de datos en el equipo local, el enfoque recomendado es usar SQLite, que se ejecuta en el mismo proceso que la aplicación. Si se necesita una capa de asignación relacional de objetos (ORM), puede usar Entity Framework. Para obtener más información, consulte [acceso a datos](https://msdn.microsoft.com/windows/uwp/data-access/index) en el Centro para desarrolladores de Windows.

 Si se conecta a servicios de Azure, asegúrese de descargar la versión más reciente [herramientas de Azure SDK](https://azure.microsoft.com/downloads/).

#### <a name="data-providers"></a>Proveedores de datos
 Para que una base de datos poder usarse en ADO.NET, debe tener un personalizado *proveedor de datos ADO.NET* o de lo contrario, debe exponer una interfaz OLE DB u ODBC. Microsoft proporciona un [lista de proveedores de datos ADO.NET](https://msdn.microsoft.com/data/dd363565) para productos de SQL Server, así como los proveedores OLE DB y ODBC.

#### <a name="data-modeling"></a>Modelado de datos
 En. NET, tiene tres opciones para modelar y manipular datos en memoria que haya recuperado desde un origen de datos:

 La tecnología Microsoft ORM preferida de Entity Framework. Puede usar para programar con datos relacionales como objetos de primera clase. NET. Para las aplicaciones nuevas, debería ser la primera opción predeterminada cuando se necesita un modelo. Requiere soporte técnico personalizado desde el proveedor ADO.NET subyacente.

 LINQ para SQL un mapeador relacional de objetos de generaciones anteriores. Funciona bien para escenarios menos complejos, pero ya no está en desarrollo activo.

 Los conjuntos de datos más antiguo de las tres tecnologías de modelado. Está diseñado principalmente para el desarrollo rápido de aplicaciones de "formularios sobre datos" en el que no se procesar grandes cantidades de datos o realizar consultas complejas o transformaciones. Un objeto de conjunto de datos consta de objetos DataTable y DataRow que lógicamente se parecen mucho más que los objetos .NET a objetos de base de datos SQL. Para aplicaciones relativamente simples basadas en orígenes de datos SQL, conjuntos de datos todavía podrían ser una buena elección.

 No hay ningún requisito para utilizar cualquiera de estas tecnologías. En algunos escenarios, especialmente cuando el rendimiento es crítico, puede simplemente usar un objeto DataReader para leer de la base de datos y copiar los valores que necesita en un objeto de colección como lista\<T >.

### <a name="native-c"></a>C++ nativo
 Las aplicaciones de C++ que se conectan a SQL Server deben usar el [SQL Server Native Client](https://msdn.microsoft.com/sqlserver/aa937733.aspx). Puede tener acceso a otras bases de datos mediante el uso de [ODBC](https://msdn.microsoft.com/library/ms710252\(v=vs.85\).aspx) o controladores de OLE DB directamente. ODBC es la interfaz estándar de la base de datos actual, pero la mayoría de los sistemas de base de datos proporciona una funcionalidad personalizada que no se puede acceder a través de la interfaz ODBC.  OLE DB es una tecnología de acceso a datos de COM heredada que se sigue admitiendo, pero no se recomienda para las aplicaciones nuevas.  Para obtener más información, consulte [acceso a datos](https://msdn.microsoft.com/library/a9455752-39c4-4457-b14e-197772d3df0b).

 Pueden usar programas de C++ que consumen servicios REST el [C++ REST SDK](https://github.com/Microsoft/cpprestsdk).

 Pueden usar programas de C++ que funcionan con Microsoft Azure Storage los [cliente de Microsoft Azure Storage](http://www.nuget.org/packages/wastorage).

#### <a name="data-modeling"></a>Modelado de datos
 Visual Studio no proporciona una capa ORM para C++.  [ODB](http://www.codesynthesis.com/products/odb/) es un ORM popular de código abierto de C++.

 Para obtener más información acerca de las tecnologías de acceso a datos heredadas de Visual C++, vea [acceso a datos](https://msdn.microsoft.com/library/a9455752-39c4-4457-b14e-197772d3df0b)

### <a name="javascript"></a>JavaScript
 [JavaScript en Visual Studio](https://msdn.microsoft.com/library/hh334522.aspx) es un lenguaje de primera clase para la creación de aplicaciones entre plataformas, aplicaciones para UWP, servicios en la nube, sitios Web y aplicaciones web. Puede usar Bower, Grunt, Gulp, npm y NuGet desde dentro de Visual Studio para instalar sus bibliotecas favoritas de JavaScript y productos de base de datos. Conectarse a Azure storage y servicios mediante la descarga de SDK desde la [sitio Web de Azure](https://azure.microsoft.com/).  Edge.js es una biblioteca que se conecta el JavaScript del lado servidor (Node.js) a los orígenes de datos ADO.NET.

### <a name="python"></a>Python
 Instalar [Python Tools para Visual Studio](http://microsoft.github.io/PTVS/) junto con su marco de Python favorito para crear aplicaciones de CPython o IronPython (. NET).  Las herramientas de Python para el sitio Web de Visual Studio tiene varios tutoriales sobre cómo conectarse a datos, incluidos [Django y SQL Database en Azure](https://github.com/Microsoft/PTVS/wiki/Django-and-SQL-Database-on-Azure), [Django y MySQL en Azure](https://github.com/Microsoft/PTVS/wiki/Django-and-MySQL-on-Azure) y [Bottle y MongoDB en Azure](https://github.com/Microsoft/PTVS/wiki/Bottle-and-MongoDB-on-Azure).

## <a name="in-this-section"></a>En esta sección
 [Instalación de sistemas de base de datos, herramientas y ejemplos](../data-tools/installing-database-systems-tools-and-samples.md) se explica cómo obtener productos de base de datos y las extensiones de Visual Studio o controladores que los respaldan y dónde encontrar las bases de datos de ejemplo para fines de aprendizaje y experimentación.

 [Visual Studio data tools para .NET](https://msdn.microsoft.com/6b145922-2f00-47db-befc-bf351b4809a1) se describe cómo usar ventanas de herramientas de Visual Studio para conectarse a orígenes de datos, crear conjuntos de datos o modelos de Entity Framework y enlazar los datos a controles de interfaz de usuario.

## <a name="related-topics"></a>Temas relacionados
 [Datos, dispositivos y análisis](https://msdn.microsoft.com/data-and-devices) proporciona una introducción a la nube inteligente de Microsoft, como Cortana Analytics Suite y soporte técnico para Internet de las cosas.

 [Microsoft Azure Storage](/azure/storage/) describe el almacenamiento de Azure y cómo crear aplicaciones con Azure blobs, tablas, colas y archivos.

 [La base de datos de SQL Azure](https://azure.microsoft.com/documentation/services/sql-database/) describe cómo conectarse a Azure SQL Database, una base de datos relacional como servicio.

 [SQL Server Data Tools](https://msdn.microsoft.com/library/hh272686\(v=vs.103\).aspx) describe las herramientas que simplifican el diseño, exploración, prueba e implementación de aplicaciones de datos conectados y las bases de datos.

 [ADO.NET](https://msdn.microsoft.com/library/5b96ed06-9759-4966-a797-a1d5f6ee50ca) describe la arquitectura de ADO.NET y cómo usar las clases de ADO.NET para administrar datos de aplicación e interactuar con orígenes de datos y XML.

 [ADO.NET Entity Framework](https://msdn.microsoft.com/data/ef) se describe cómo crear aplicaciones de datos que permiten a los desarrolladores programar en un modelo conceptual en lugar de directamente en una base de datos relacional.

 [Servicios de datos de WCF 4.5](https://msdn.microsoft.com/library/73d2bec3-7c92-4110-b905-11bb0462357a) se describe cómo usar [!INCLUDE[ssAstoria](../includes/ssastoria-md.md)] para implementar servicios de datos en la web o en una intranet que implementan la [Open Data Protocol (OData)](http://go.microsoft.com/fwlink/?LinkID=182204).

 [Datos en soluciones de Office](https://msdn.microsoft.com/library/8478c095-864b-4ed3-8a70-1fc19b411c6a) contiene vínculos a temas que explican cómo funcionan los datos en soluciones de Office. Se incluye información sobre la programación orientada a esquema, el almacenamiento de datos en caché y el acceso a datos en el servidor.

 [LINQ (Language-Integrated Query)](https://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d) describe las capacidades de consulta integradas en C# y Visual Basic y el modelo común para consultar bases de datos relacionales, documentos XML, conjuntos de datos y colecciones en memoria.

 [Herramientas XML en Visual Studio](../xml-tools/xml-tools-in-visual-studio.md) explica cómo trabajar con las características XML de .NET Framework de datos, la depuración de XSLT, XML y la arquitectura de las consultas XML.

 [Documentos y datos XML](https://msdn.microsoft.com/library/e695047f-3c0f-4045-8708-5baea91cc380) proporciona información general sobre un conjunto completo e integrado de clases que funcionan con documentos XML y datos de .NET Framework.
