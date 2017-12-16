---
title: Acceso a datos en Visual Studio | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: "80025080"
helpviewer_keywords:
- data [Visual Studio]
- data access [Visual Studio]
- data [C#]
- ADO.NET, data access
caps.latest.revision: "100"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.openlocfilehash: da7176d3fd64591064bfd33a0780ba7939621182
ms.sourcegitcommit: f0ddee934713ea9126fa107018a57a94a05eafd3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/12/2017
---
# <a name="accessing-data-in-visual-studio"></a>Acceso a datos en Visual Studio

En Visual Studio, puede crear aplicaciones que se conectan a los datos en prácticamente cualquier producto de base de datos o el servicio, en cualquier formato, en cualquier lugar, en un equipo local, en una red de área local o en una nube pública, privada o híbrida.

Para las aplicaciones en JavaScript, Python, PHP, Ruby o C++, conectarse a los datos como que hace nada más, puede obtener bibliotecas y escribir código. Para aplicaciones. NET, Visual Studio proporciona herramientas que puede usar para explorar los orígenes de datos, crear modelos de objeto para almacenar y manipular datos en memoria y enlazar datos a la interfaz de usuario. Microsoft Azure proporciona SDK para. NET, Java, Node.js, PHP, Python, Ruby y aplicaciones móviles y herramientas en Visual Studio para conectarse al almacenamiento de Azure.

Las listas siguientes muestran algunos de los muchos sistemas de base de datos y almacenamiento que se pueden usar desde Visual Studio. El [Microsoft Azure](https://azure.microsoft.com/) ofertas son servicios de datos que incluyen todas las de aprovisionamiento y administración de almacén de datos subyacente.  [Azure Tools para Visual Studio](https://www.visualstudio.com/features/azure-tools-vs.aspx) es un componente opcional que le permite trabajar con almacenes de datos de Azure directamente desde Visual Studio. La mayoría de los otros SQL y NoSQL base de datos productos que aparecen aquí se puede hospedar en un equipo local, en una red local o en Microsoft Azure en una máquina virtual. En este escenario, usted es responsable de administrar la base de datos.

**Microsoft Azure**

||||
|-|-|-|
|Base de datos SQL|Documentos|Almacenamiento (blobs, tablas, colas, archivos)|
|Almacenamiento de datos SQL|Base de datos SQL Server Stretch|StorSimple|

Y mucho más...

**SQL**

||||
|-|-|-|
|SQL Server 2005-2016, incluidos Express y LocalDB|Pájaro de fuego|MariaDB|
|MySQL|Oracle|PostgreSQL|
|SQLite|||

Y mucho más...

**NoSQL**

||||
|-|-|-|
|Apache Casandra|CouchDB|MongoDB|
|Datos|OrientDB|RavenDB|
|VelocityDB|||

Y mucho más...

Muchos proveedores de base de datos y otros fabricantes admiten la integración de Visual Studio mediante paquetes de NuGet. Puede explorar las ofertas en nuget.org o mediante el Administrador de paquetes de NuGet en Visual Studio (**herramientas** > **Administrador de paquetes de NuGet** > **administrar paquetes NuGet Paquetes para la solución**). Otros productos de base de datos se integran con Visual Studio como una extensión. Puede examinar estas ofertas de Visual Studio Marketplace, vaya a **herramientas**, **extensiones y actualizaciones** y, a continuación, seleccione **Online** en el panel izquierdo de la cuadro de diálogo. Para obtener más información, consulte [sistemas de base de datos Compatible con Visual Studio](../data-tools/installing-database-systems-tools-and-samples.md).

> [!NOTE]
> Finalizó el soporte extendido de SQL Server 2005 de 12 de abril de 2016. No hay ninguna garantía de que las herramientas de datos en Visual Studio 2015 y versiones posteriores continuarán funcionando con SQL Server 2005 después de esta fecha. Para obtener más información, consulte el [anuncio de finalización del soporte para SQL Server 2005](https://www.microsoft.com/server-cloud/products/sql-server-2005/).

## <a name="net-languages"></a>Lenguajes de .NET

Todos los accesos de datos. NET, incluido en .NET Core, se basan en ADO.NET, un conjunto de clases que define una interfaz para tener acceso a cualquier tipo de origen de datos relacional y no relacionales. Visual Studio dispone de varias herramientas y diseñadores que funcionan con ADO.NET para conectarse a bases de datos, manipular los datos y presentar los datos al usuario. La documentación de esta sección describe cómo usar estas herramientas. También puede programar directamente con los objetos de comando ADO.NET. Para obtener más información sobre cómo llamar directamente a las APIs ADO.NET, vea [ADO.NET](/dotnet/framework/data/adonet/index).

Para obtener documentación de acceso a datos relacionada específicamente con ASP.NET, vea [trabajar con datos](http://www.asp.net/web-forms/overview/presenting-and-managing-data) en el sitio ASP.NET. Para obtener un tutorial sobre el uso de Entity Framework con ASP.NET MVC, consulte [Introducción a Entity Framework 6 Code First con MVC 5](http://www.asp.net/mvc/overview/getting-started/getting-started-with-ef-using-mvc/creating-an-entity-framework-data-model-for-an-asp-net-mvc-application).

Las aplicaciones universales de plataforma de Windows (UWP) en C# o Visual Basic pueden usar el SDK de Microsoft Azure para .NET para tener acceso a almacenamiento de Azure y otros servicios de Azure. La clase Windows.Web.HttpClient permite la comunicación con cualquier servicio RESTful. Para obtener más información, consulte [cómo conectarse a un servidor HTTP mediante Windows.Web.Http](https://msdn.microsoft.com/library/windows/apps/dn469430.aspx).

Para el almacenamiento de datos en el equipo local, el enfoque recomendado es usar el código, que se ejecuta en el mismo proceso que la aplicación. Si no se requiere un nivel de asignación relacional de objetos (ORM), puede usar Entity Framework. Para obtener más información, consulte [acceso a datos](https://msdn.microsoft.com/windows/uwp/data-access/index) en el centro de desarrollo de Windows.

Si se conecta a servicios de Azure, asegúrese de descargar la versión más reciente [herramientas de Azure SDK](https://azure.microsoft.com/downloads/).

### <a name="data-providers"></a>Proveedores de datos

Para que una base de datos poder usarse en ADO.NET, debe tener un personalizado *proveedor de datos ADO.NET* o else debe exponer una interfaz OLE DB u ODBC. Microsoft proporciona un [lista de proveedores de datos ADO.NET](https://msdn.microsoft.com/data/dd363565) para productos de SQL Server, así como los proveedores de OLE DB y ODBC.

### <a name="data-modeling"></a>Modelado de datos

En. NET, tiene tres opciones para modelar y manipular datos en memoria después de que se han recuperado de un origen de datos:

[Entity Framework](../data-tools/entity-data-model-tools-in-visual-studio.md)  
La tecnología de Microsoft ORM preferida. Puede usar para programar con datos relacionales como objetos de primera clase. NET. Para las aplicaciones nuevas, debe ser la primera opción predeterminada cuando se necesita un modelo. Requiere compatibilidad personalizada del proveedor de ADO.NET subyacente.

[LINQ to SQL](../data-tools/linq-to-sql-tools-in-visual-studio2.md)  
Un asignador relacional de objetos de generaciones anteriores. Funciona bien para escenarios menos complejos, pero ya no está en desarrollo activo.

[Conjuntos de datos](../data-tools/dataset-tools-in-visual-studio.md)  
El más antiguo de las tres tecnologías de modelado. Está diseñado principalmente para el desarrollo rápido de aplicaciones de "formularios sobre datos" en el que no se procesar grandes cantidades de datos o realizar consultas complejas o transformaciones. Un objeto de conjunto de datos está formado por objetos DataTable y DataRow lógicamente similares mucho más que los objetos .NET a objetos de base de datos SQL. Para aplicaciones relativamente simples basadas en orígenes de datos SQL, conjuntos de datos todavía podrían ser una buena elección.

No hay ningún requisito para usar cualquiera de estas tecnologías. En algunos casos, especialmente cuando el rendimiento es crítico, puede simplemente usar un objeto DataReader para leer de la base de datos y copie los valores que necesita en un objeto de colección como lista\<T >.

## <a name="native-c"></a>C++ nativo

Las aplicaciones de C++ que se conectan a SQL Server deben utilizar el [Microsoft® ODBC Driver 13.1 para SQL Server](https://www.microsoft.com/download/details.aspx?id=53339) en la mayoría de los casos. Si los servidores están vinculados, OLE DB es necesaria y para que use la [SQL Server Native Client](/sql/relational-databases/native-client/sql-server-native-client). Puede tener acceso a otras bases de datos mediante [ODBC](https://msdn.microsoft.com/library/ms710252\(v=vs.85\).aspx) o controladores de OLE DB directamente. ODBC es la interfaz estándar de la base de datos actual, pero la mayoría de los sistemas de base de datos proporciona la funcionalidad personalizada que no se puede tener acceso a través de la interfaz ODBC. OLE DB es una tecnología de acceso a datos de COM heredada que se sigue admitiendo, pero no se recomienda para las aplicaciones nuevas. Para obtener más información, consulte [acceso a datos en Visual C++](/cpp/data/data-access-in-cpp).

Pueden usar programas de C++ que consumen servicios REST de la [C++ REST SDK](https://github.com/Microsoft/cpprestsdk).

Pueden usar programas de C++ que funcionan con almacenamiento de Microsoft Azure el [cliente de almacenamiento de Microsoft Azure](http://www.nuget.org/packages/wastorage).

Modelado de datos&mdash;Visual Studio no proporciona una capa ORM para C++. [ODBC](http://www.codesynthesis.com/products/odb/) es un ORM popular de código abierto para C++.

Para más información sobre cómo conectarse a bases de datos de aplicaciones de C++, vea [herramientas de datos de Visual Studio para C++](../data-tools/visual-studio-data-tools-for-cpp.md). Para obtener más información acerca de las tecnologías de acceso a datos heredadas de Visual C++, vea [acceso a datos](/cpp/data/data-access-in-cpp).

## <a name="javascript"></a>JavaScript

[JavaScript en Visual Studio](/scripting/javascript/javascript-language-reference) es un lenguaje de primera clase para crear aplicaciones multiplataforma, las aplicaciones de UWP, servicios en la nube, sitios Web y aplicaciones web. Puede utilizar Bower, Grunt, Gulp, npm y NuGet desde dentro de Visual Studio para instalar los favoritos bibliotecas de JavaScript y los productos de base de datos. Conectarse a almacenamiento de Azure y servicios mediante la descarga de SDK desde la [sitio Web de Azure](https://azure.microsoft.com/). Edge.js es una biblioteca que se conecta el servidor JavaScript (Node.js) a los orígenes de datos ADO.NET.

## <a name="python"></a>Python

Instalar [Python Tools para Visual Studio](http://microsoft.github.io/PTVS/) junto con el marco de Python favorito para crear aplicaciones de CPython o IronPython (. NET). Las herramientas Python para el sitio Web de Visual Studio tiene varios tutoriales sobre cómo conectarse a datos, incluida la [Django y base de datos de SQL en Azure](https://github.com/Microsoft/PTVS/wiki/Django-and-SQL-Database-on-Azure), [Django y MySQL en Azure](https://github.com/Microsoft/PTVS/wiki/Django-and-MySQL-on-Azure) y [Bottle y MongoDB en Azure](https://github.com/Microsoft/PTVS/wiki/Bottle-and-MongoDB-on-Azure).

## <a name="related-topics"></a>Temas relacionados

[Datos, dispositivos y análisis](https://msdn.microsoft.com/data-and-devices)  
Proporciona una introducción a la nube inteligente de Microsoft, incluidos los Cortana Analytics Suite y soporte técnico para Internet de las cosas.

[Almacenamiento de Microsoft Azure](https://azure.microCsoft.com/documentation/services/storage/)  
Describe cómo crear aplicaciones mediante el uso de archivos, tablas, colas y blobs de Azure y almacenamiento de Azure.

[Base de datos SQL Azure](https://azure.microsoft.com/documentation/services/sql-database/)  
Describe cómo conectarse a la base de datos de SQL de Azure, una base de datos relacional como un servicio.

[SQL Server Data Tools](/sql/ssdt/download-sql-server-data-tools-ssdt)  
Describe las herramientas que simplifican el diseño, la exploración, prueba e implementación de bases de datos y aplicaciones de datos conectados.

[ADO.NET](/dotnet/framework/data/adonet/index)  
Describe la arquitectura de ADO.NET y cómo usar las clases de ADO.NET para administrar los datos de aplicación e interactuar con orígenes de datos y XML.

[ADO.NET Entity Framework](https://msdn.microsoft.com/data/ef)  
Describe cómo crear aplicaciones de datos que permiten a los desarrolladores programar con un modelo conceptual, en lugar de hacerlo directamente en una base de datos relacional.

[Servicios de datos de WCF 4.5](/dotnet/framework/data/wcf/index)  
Describe cómo usar [!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)] para implementar servicios de datos en la web o en una intranet que implementan la [Open Data Protocol (OData)](http://go.microsoft.com/fwlink/?LinkID=182204).

[Datos en las soluciones de Office](/office-dev/office-dev/data-in-office-solutions)  
Contiene vínculos a temas que explican cómo funcionan los datos en soluciones de Office. Se incluye información sobre la programación orientada a esquema, el almacenamiento de datos en caché y el acceso a datos en el servidor.

[LINQ (Language Integrated Query)](/dotnet/csharp/linq/)  
Se describen las eficaces funciones de consulta integradas en C# y Visual Basic, así como el modelo común para consultar bases de datos relacionales, documentos XML, conjuntos de datos y colecciones en memoria.

[Herramientas XML en Visual Studio](../xml-tools/xml-tools-in-visual-studio.md)  
Describe el trabajo con características XML de .NET Framework XML datos, depuración de XSLT y la arquitectura de las consultas XML.

[Documentos y datos XML](/dotnet/standard/data/xml/index)  
Proporciona información general sobre un conjunto completo e integrado de clases que funcionan con documentos XML y datos en .NET Framework.