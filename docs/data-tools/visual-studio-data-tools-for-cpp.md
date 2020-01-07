---
title: Herramientas de datos paraC++
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CPP
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
- cplusplus
ms.openlocfilehash: 2be19729b61831e6f15ff40b6b4e1d7b4b0bb541
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/01/2020
ms.locfileid: "75586060"
---
# <a name="visual-studio-data-tools-for-c"></a>Visual Studio Data Tools para C++

A C++ menudo, Native puede proporcionar el rendimiento más rápido cuando se obtiene acceso a los orígenes de datos. Sin embargo, las herramientas de C++ datos para las aplicaciones de Visual Studio no son tan ricas como para las aplicaciones .net. Por ejemplo, la ventana **orígenes de datos** no se puede utilizar para arrastrar y colocar orígenes de C++ datos en una superficie de diseño. Si necesita un nivel de objeto relacional, tendrá que escribir su propio o usar un producto de terceros. Lo mismo se aplica a la funcionalidad de enlace de datos, aunque las aplicaciones que usan la biblioteca MFC (Microsoft Foundation Class) pueden utilizar algunas clases de bases de datos, junto con documentos y vistas, para almacenar datos en memoria y mostrarlos al usuario. Para obtener más información, vea [acceso a datos C++en Visual ](/cpp/data/data-access-in-cpp).

Para conectarse a las bases de datos SQL, C++ las aplicaciones nativas pueden usar los controladores ODBC y OLE DB y el proveedor de ADO que se incluyen con Windows. Estos pueden conectarse a cualquier base de datos que admita dichas interfaces. El controlador ODBC es el estándar. OLE DB se proporciona por compatibilidad con versiones anteriores. Para obtener más información sobre esas tecnologías de datos, vea [componentes de Windows Data Access](/previous-versions/windows/desktop/ms692897(v=vs.85)).

Para aprovechar las ventajas de la funcionalidad personalizada en SQL Server 2005 y versiones posteriores, use el [SQL Server Native Client](/sql/relational-databases/native-client/sql-server-native-client). Native Client también contiene el controlador ODBC de SQL Server y el proveedor de OLE DB de SQL Server en una biblioteca de vínculos dinámicos (DLL) nativa. Estos admiten aplicaciones que usan las API de código nativo (ODBC, OLE DB y ADO) para Microsoft SQL Server. SQL Server Native Client instala con SQL Server Data Tools. La guía de programación está aquí: [SQL Server la programación de cliente nativo](/sql/relational-databases/native-client/sql-server-native-client-programming).

## <a name="to-connect-to-localdb-through-odbc-and-sql-native-client-from-a-c-application"></a>Para conectarse a localDB a través de ODBC y SQL Native Client C++ desde una aplicación

1. Instale SQL Server Data Tools.

2. Si necesita una base de datos SQL de ejemplo a la que conectarse, descargue la base de datos Northwind y descomprimala en una nueva ubicación.

3. Utilice SQL Server Management Studio para adjuntar el archivo *Northwind. MDF* descomprimido a localDB. Cuando SQL Server Management Studio inicie, conéctese a (LocalDB) \MSSQLLocalDB.

   ![Cuadro de diálogo de conexión de SSMS](../data-tools/media/raddata-ssms-connect-dialog.png)

   A continuación, haga clic con el botón secundario en el nodo LocalDB en el panel izquierdo y elija **adjuntar**.

   ![Base de datos adjunta de SSMS](../data-tools/media/raddata-ssms-attach-database.png)

4. Descargue el ejemplo de Windows SDK ODBC y descomprimalo en una nueva ubicación. Este ejemplo muestra los comandos ODBC básicos que se usan para conectarse a una base de datos y emitir consultas y comandos. Puede obtener más información sobre esas funciones en [Microsoft Open Database Connectivity (ODBC)](/sql/odbc/microsoft-open-database-connectivity-odbc). La primera vez que se carga la solución (se encuentra C++ en la carpeta), Visual Studio le ofrecerá la actualización de la solución a la versión actual de Visual Studio. Haga clic en **Sí**.

5. Para usar Native Client, necesita el archivo de *encabezado* y el archivo *lib* . Estos archivos contienen funciones y definiciones específicas de SQL Server, más allá de las funciones ODBC definidas en SQL. h. En **Project** > **propiedades** > **directorios de VC + +** , agregue el siguiente directorio de inclusión:

   **%ProgramFiles%\Microsoft SQL Server\110\SDK\Include**

   Y este directorio de biblioteca:

   **%ProgramFiles%\Microsoft SQL Server\110\SDK\Lib**

6. Agregue estas líneas en *odbcsql. cpp*. La #define impide que se compilen definiciones de OLE DB irrelevantes.

   ```cpp
   #define _SQLNCLI_ODBC_
   #include <sqlncli.h>
   ```

    Tenga en cuenta que el ejemplo no utiliza realmente ninguna funcionalidad de Native Client, por lo que los pasos anteriores no son necesarios para que se compile y se ejecute. Pero el proyecto ya está configurado para que use esta funcionalidad. Para más información, vea [SQL Server Native Client Programming](/sql/relational-databases/native-client/sql-server-native-client) (Programación de SQL Server Native Client).

7. Especifique el controlador que se va a usar en el subsistema ODBC. En el ejemplo se pasa el atributo de cadena de conexión del controlador en como un argumento de la línea de comandos. En > **propiedades** del **proyecto** > **depuración**, agregue este argumento de comando:

   ```cpp
   DRIVER="SQL Server Native Client 11.0"
   ```

8. Presione **F5** para compilar y ejecutar la aplicación. Debería ver un cuadro de diálogo del controlador que le pide que escriba una base de datos. Escriba `(localdb)\MSSQLLocalDB`y active la casilla **Usar conexión de confianza**. Haga clic en **Aceptar**. Debería ver una consola con mensajes que indican una conexión correcta. También debería ver un símbolo del sistema en el que puede escribir una instrucción SQL. En la pantalla siguiente se muestra una consulta de ejemplo y los resultados:

   ![Resultado de la consulta de ejemplo de ODBC](../data-tools/media/raddata-odbc-sample-query-output.png)

## <a name="see-also"></a>Vea también

- [Obtener acceso a los datos en Visual Studio](../data-tools/accessing-data-in-visual-studio.md)
