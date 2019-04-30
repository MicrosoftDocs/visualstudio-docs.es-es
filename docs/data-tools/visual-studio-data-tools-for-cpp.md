---
title: Data tools paraC++
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CPP
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- data-storage
- cplusplus
ms.openlocfilehash: 5157f1d6a851e0784e79dfbfe5b94aef0490a026
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62565237"
---
# <a name="visual-studio-data-tools-for-c"></a>Visual Studio Data Tools para C++

C++ nativo a menudo pueden proporcionar el rendimiento más rápido cuando se tiene acceso a orígenes de datos. Sin embargo, no están tan enriquecidos como para aplicaciones .NET datos herramientas para aplicaciones de C++ en Visual Studio. Por ejemplo, el **orígenes de datos** ventana no se puede usar para arrastrar y colocar los orígenes de datos en un C++ superficie de diseño. Si necesita una capa de objeto-relacional, tendrá que escribir el suyo propio, o utilizar un producto de terceros. Lo mismo puede decirse de funcionalidad de enlace de datos, aunque las aplicaciones que usan la biblioteca Microsoft Foundation Class pueden utilizar algunas clases de base de datos, junto con los documentos y vistas, para almacenar datos en memoria y mostrarla al usuario. Para obtener más información, consulte [acceso a datos en Visual C++](/cpp/data/data-access-in-cpp).

Para conectarse a bases de datos SQL, aplicaciones nativas de C++ pueden utilizar los controladores ODBC y OLE DB y el proveedor de ADO que se incluyen con Windows. Estos pueden conectarse a cualquier base de datos que es compatible con esas interfaces. El controlador ODBC es el estándar. OLE DB se proporciona por compatibilidad con versiones anteriores. Para obtener más información sobre estas tecnologías de datos, vea [Windows Data Access Components](/previous-versions/windows/desktop/ms692897(v=vs.85)).

Para aprovechar la funcionalidad personalizada de SQL Server 2005 y versiones posteriores, utilice el [cliente nativo de SQL Server](/sql/relational-databases/native-client/sql-server-native-client). El cliente nativo también contiene el controlador ODBC de SQL Server y el proveedor OLE DB de SQL Server en una biblioteca de vínculos dinámicos (DLL). Son compatibles con las aplicaciones que usan la API de código nativo (ODBC, OLE DB y ADO) a Microsoft SQL Server. SQL Server Native Client se instala con SQL Server Data Tools. La Guía de programación se encuentra aquí: [Programación de cliente nativo de SQL Server](/sql/relational-databases/native-client/sql-server-native-client-programming).

## <a name="to-connect-to-localdb-through-odbc-and-sql-native-client-from-a-c-application"></a>Para conectarse a localDB mediante ODBC y SQL Native Client desde una aplicación de C++

1. Instale SQL Server Data Tools.

2. Si necesita una base de datos SQL de ejemplo para conectarse a, descargue la base de datos Northwind y descomprímalo en una nueva ubicación.

3. Usar SQL Server Management Studio para adjuntar la descomprime *Northwind.mdf* archivo a localDB. Cuando se inicia SQL Server Management Studio, conéctese a (localdb) \MSSQLLocalDB.

   ![Cuadro de diálogo de conexión de SSMS](../data-tools/media/raddata-ssms-connect-dialog.png)

   A continuación, haga doble clic en el nodo de localdb en el panel izquierdo y elija **adjuntar**.

   ![SSMS adjuntar la base de datos](../data-tools/media/raddata-ssms-attach-database.png)

4. Descargue el ejemplo de SDK de Windows de ODBC y descomprímalo en una nueva ubicación. Este ejemplo muestra los comandos básicos de ODBC que se usan para conectarse a una base de datos y emitir consultas y comandos. Puede aprender más acerca de esas funciones en el [Microsoft Open Database Connectivity (ODBC)](/sql/odbc/microsoft-open-database-connectivity-odbc). Cuando se carga primero la solución (está en la carpeta de C++), Visual Studio le sugerirá actualizar la solución a la versión actual de Visual Studio. Haga clic en **Sí**.

5. Para usar el cliente nativo, necesitará su *encabezado* archivo y *lib* archivo. Estos archivos contienen las funciones y las definiciones específicas de SQL Server, más allá de las funciones ODBC definidas en sql.h. En **proyecto** > **propiedades** > **directorios de VC ++**, agregue el siguiente directorio de inclusión:

   **%ProgramFiles%\Microsoft SQL Server\110\SDK\Include**

   Y este directorio de biblioteca:

   **%ProgramFiles%\Microsoft SQL Server\110\SDK\Lib**

6. Agregue estas líneas en *odbcsql.cpp*. El #define impide que las definiciones de OLE DB irrelevantes desde que se está compilando.

   ```cpp
   #define _SQLNCLI_ODBC_
   #include <sqlncli.h>
   ```

    Tenga en cuenta que el ejemplo no utiliza realmente ninguna funcionalidad de cliente nativo, por lo que no son necesarios para compilar y ejecutar los pasos anteriores. Pero el proyecto ahora está configurado para que usar esta funcionalidad. Para más información, vea [SQL Server Native Client Programming](/sql/relational-databases/native-client/sql-server-native-client) (Programación de SQL Server Native Client).

7. Especifique qué controlador usar en el subsistema ODBC. El ejemplo pasa el atributo de cadena de conexión de controlador en como un argumento de línea de comandos. En **proyecto** > **propiedades** > **depuración**, agregue este argumento de comando:

   ```cpp
   DRIVER="SQL Server Native Client 11.0"
   ```

8. Presione **F5** para compilar y ejecutar la aplicación. Debería ver un cuadro de diálogo desde el controlador que se le pide que escriba una base de datos. Escriba `(localdb)\MSSQLLocalDB`y compruebe **utilizar conexión de confianza**. Haga clic en **Aceptar**. Debería ver una consola con los mensajes que indican una conexión correcta. También verá un símbolo del sistema donde puede escribir una instrucción SQL. La siguiente pantalla muestra un ejemplo de consulta y los resultados:

   ![Salida de consulta de ejemplo ODBC](../data-tools/media/raddata-odbc-sample-query-output.png)

## <a name="see-also"></a>Vea también

- [Obtener acceso a los datos en Visual Studio](../data-tools/accessing-data-in-visual-studio.md)