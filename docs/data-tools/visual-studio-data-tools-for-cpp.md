---
title: Herramientas de datos para C++
description: Explore las herramientas de datos de Visual Studio para C++. Conéctese a localDB a través de ODBC y el cliente nativo de SQL desde una aplicación de C++.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: overview
dev_langs:
- CPP
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- data-storage
- cplusplus
ms.openlocfilehash: 4cf316e0d892e8c6ba229a7a46ee0439797d032f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99866351"
---
# <a name="visual-studio-data-tools-for-c"></a>Visual Studio Data Tools para C++

A menudo, C++ nativo puede proporcionar el rendimiento más rápido cuando se accede a orígenes de datos. Pero las herramientas de datos para las aplicaciones de C++ en Visual Studio no son tan completas como para las aplicaciones de .NET. Por ejemplo, no se puede usar la ventana **Orígenes de datos** para arrastrar y colocar orígenes de datos en una superficie de diseño de C++. Si necesita una capa de objetos relacionales, tendrá que escribir una propia o usar un producto de terceros. Lo mismo se aplica a la funcionalidad de enlace de datos, aunque las aplicaciones que usan la biblioteca MFC (Microsoft Foundation Class) pueden utilizar algunas clases de bases de datos, junto con documentos y vistas, para almacenar datos en memoria y mostrarlos al usuario. Para obtener más información, vea [Acceso a datos en Visual C++](/cpp/data/data-access-in-cpp).

Para conectarse a las bases de datos SQL, las aplicaciones nativas de C++ pueden usar los controladores ODBC y OLE DB, y el proveedor ADO que se incluyen con Windows. Estos se pueden conectar a cualquier base de datos que admita esas interfaces. El controlador ODBC es el estándar. OLE DB se proporciona para mantener la compatibilidad con versiones anteriores. Para obtener más información sobre esas tecnologías de datos, vea [Componentes de acceso a datos de Windows](/previous-versions/windows/desktop/ms692897(v=vs.85)).

Para aprovechar las ventajas de la funcionalidad personalizada en SQL Server 2005 y versiones posteriores, use el [cliente nativo de SQL Server](/sql/relational-databases/native-client/sql-server-native-client). El cliente nativo también combina el controlador ODBC y el proveedor OLE DB de SQL Server en una biblioteca de vínculos dinámicos (DLL) nativa. Admiten aplicaciones en las que se usan API de código nativo (ODBC, OLE DB y ADO) para Microsoft SQL Server. SQL Server Native Client se instala con SQL Server Data Tools. La guía de programación está aquí: [Programación de SQL Server Native Client](/sql/relational-databases/native-client/sql-server-native-client-programming).

## <a name="to-connect-to-localdb-through-odbc-and-sql-native-client-from-a-c-application"></a>Para conectarse a localDB a través de ODBC y SQL Native Client desde una aplicación de C++

1. Instale SQL Server Data Tools.

2. Si necesita una base de datos SQL de ejemplo a la que conectarse, descargue la base de datos Northwind y descomprímala en una nueva ubicación.

3. Use SQL Server Management Studio para adjuntar el archivo descomprimido *Northwind.mdf* a localDB. Cuando se inicie SQL Server Management Studio, conéctese a (localdb)\MSSQLLocalDB.

   ![Cuadro de diálogo de conexión de SSMS](../data-tools/media/raddata-ssms-connect-dialog.png)

   Después, haga clic con el botón derecho en el nodo localdb en el panel izquierdo y elija **Adjuntar**.

   ![Adjuntar base de datos en SSMS](../data-tools/media/raddata-ssms-attach-database.png)

4. Descargue el ejemplo de ODBC Windows SDK y descomprímalo en una nueva ubicación. En este ejemplo se muestran los comandos ODBC básicos que se usan para conectarse a una base de datos y emitir consultas y comandos. Puede obtener más información sobre esas funciones en [Microsoft Open Database Connectivity (ODBC)](/sql/odbc/microsoft-open-database-connectivity-odbc). La primera vez que cargue la solución (se encuentra en la carpeta de C++), Visual Studio le ofrecerá actualizarla a la versión actual de Visual Studio. Haga clic en **Sí**.

5. Para usar el cliente nativo, necesita sus archivos *header* y *lib*. Estos archivos contienen funciones y definiciones específicas de SQL Server, más allá de las funciones de ODBC definidas en sql.h. En **Proyecto** > **Propiedades** > **Directorios de VC++** , agregue el directorio de inclusión siguiente:

   **%ProgramFiles%\Microsoft SQL Server\110\SDK\Include**

   Y este directorio de biblioteca:

   **%ProgramFiles%\Microsoft SQL Server\110\SDK\Lib**

6. Agregue estas líneas en *odbcsql.cpp*. #define impide que se compilen definiciones de OLE DB irrelevantes.

   ```cpp
   #define _SQLNCLI_ODBC_
   #include <sqlncli.h>
   ```

    Tenga en cuenta que en el ejemplo no se usa realmente ninguna funcionalidad del cliente nativo, por lo que no se necesitan los pasos anteriores para compilarlo y ejecutarlo. Pero el proyecto ya está configurado para que use esta funcionalidad. Para más información, vea [SQL Server Native Client Programming](/sql/relational-databases/native-client/sql-server-native-client) (Programación de SQL Server Native Client).

7. Especifique el controlador que se va a usar en el subsistema ODBC. En el ejemplo se pasa el atributo de cadena de conexión DRIVER como un argumento de la línea de comandos. En **Proyecto** > **Propiedades** > **Depuración**, agregue este argumento de comando:

   ```cpp
   DRIVER="SQL Server Native Client 11.0"
   ```

8. Presione **F5** para compilar y ejecutar la aplicación. Debería ver un cuadro de diálogo del controlador que le pide que escriba una base de datos. Escriba `(localdb)\MSSQLLocalDB` y active **Usar conexión de confianza**. Haga clic en **Aceptar**. Debería ver una consola con mensajes que indican que la conexión se ha realizado correctamente. También debería ver un símbolo del sistema en el que puede escribir una instrucción SQL. En la pantalla siguiente se muestra una consulta de ejemplo y los resultados:

   ![Resultado de la consulta de ejemplo de ODBC](../data-tools/media/raddata-odbc-sample-query-output.png)

## <a name="see-also"></a>Vea también

- [Obtener acceso a los datos en Visual Studio](../data-tools/accessing-data-in-visual-studio.md)
