---
title: Visual Studio Data Tools para C++ | Microsoft Docs
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.date: 11/15/2016
ms.topic: conceptual
ms.assetid: 3a3849d9-1bc7-47d1-805e-1755223ccba2
caps.latest.revision: 12
author: jillre
ms.author: jillfra
manager: jillfra
robots: noindex,nofollow
ms.openlocfilehash: ec68d54ced85737d66c64ca2dbf7942ca81e5314
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "72621207"
---
# <a name="visual-studio-data-tools-for-c"></a>Visual Studio Data Tools para C++
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

A menudo, C++ nativo puede proporcionar el rendimiento más rápido cuando se obtiene acceso a los orígenes de datos. Sin embargo, las herramientas de datos para las aplicaciones de C++ en Visual Studio no son tan ricas como para las aplicaciones de .NET. Por ejemplo, las ventanas de orígenes de datos no se pueden usar para arrastrar y colocar orígenes de datos en una superficie de diseño de C++. Si necesita un nivel de objeto relacional, tendrá que escribir su propio o usar un producto de terceros.  Lo mismo se aplica a la funcionalidad de enlace de datos, aunque las aplicaciones que usan la biblioteca MFC (Microsoft Foundation Class) pueden utilizar algunas clases de bases de datos, junto con documentos y vistas, para almacenar datos en memoria y mostrarlos al usuario. Para obtener más información, vea [acceso a datos en Visual C++](https://msdn.microsoft.com/library/7wtdsdkh.aspx) .

 Para conectarse a las bases de datos SQL, las aplicaciones de C++ nativas pueden usar los controladores ODBC y OLE DB y el proveedor de ADO que se incluyen con Windows.     Estos pueden conectarse a cualquier base de datos que admita dichas interfaces. El controlador ODBC es el estándar. OLE DB se proporciona por compatibilidad con versiones anteriores. Para obtener más información sobre esas tecnologías de datos, vea [componentes de Windows Data Access](https://msdn.microsoft.com/library/windows/desktop/aa968814\(v=vs.85\).aspx) .

 Para aprovechar las ventajas de la funcionalidad personalizada en SQL Server 2005 y versiones posteriores, use el [SQL Server Native Client](https://msdn.microsoft.com/sqlserver/aa937733). Native Client también contiene el controlador ODBC de SQL Server y el proveedor de OLE DB de SQL Server en una biblioteca de vínculos dinámicos (DLL) nativa. Estos admiten aplicaciones que usan las API de código nativo (ODBC, OLE DB y ADO) para Microsoft SQL Server.  SQL Server Native Client instala con SQL Server Data Tools. La guía de programación está aquí: [SQL Server Native Client Programming](https://msdn.microsoft.com/library/ms130892.aspx).

## <a name="to-connect-to-localdb-through-odbc-and-sql-native-client-from-a-c-application"></a>Para conectarse a localDB a través de ODBC y SQL Native Client desde una aplicación de C++

1. Instale SQL Server Data Tools.

2. Si necesita una base de datos SQL de ejemplo a la que conectarse, descargue la base de datos Northwind y descomprimala en una nueva ubicación.

3. Utilice SQL Server Management Studio para adjuntar el archivo Northwind. MDF descomprimido a localDB. Cuando SQL Server Management Studio inicie, conéctese a (LocalDB) \MSSQLLocalDB.

    ![Cuadro de diálogo de conexión de SSMS](../data-tools/media/raddata-ssms-connect-dialog.png "raddata cuadro de diálogo de conexión de SSMS")

    A continuación, haga clic con el botón secundario en el nodo LocalDB en el panel izquierdo y elija **adjuntar**.

    ![Base de datos adjunta de SSMS](../data-tools/media/raddata-ssms-attach-database.png "base de datos adjuntar raddata SSMS")

4. Descargue el ejemplo de Windows SDK ODBC y descomprimalo en una nueva ubicación. Este ejemplo muestra los comandos ODBC básicos que se usan para conectarse a una base de datos y emitir consultas y comandos. Puede obtener más información sobre esas funciones en [Microsoft Open Database Connectivity (ODBC)](https://msdn.microsoft.com/library/windows/desktop/ms710252\(v=vs.85\).aspx). La primera vez que se carga la solución (se encuentra en la carpeta de C++), Visual Studio le ofrecerá la actualización de la solución a la versión actual de Visual Studio. Haga clic en **Sí**.

5. Para usar Native Client, necesita el archivo de encabezado y el archivo lib. Estos archivos contienen funciones y definiciones específicas de SQL Server, más allá de las funciones ODBC definidas en SQL. h. En propiedades del **proyecto**  >  **Properties**  >  , en**directorios de VC + +**, agregue el siguiente directorio de inclusión:

   ** \<system drive> : \Archivos de Programa\microsoft SQL Server\110\SDK\Include** y este directorio de biblioteca:

   **C:\Archivos de Programa\microsoft SQL Server\110\SDK\Lib**

6. Agregue estas líneas en odbcsql. cpp. La #define impide que se compilen definiciones de OLE DB irrelevantes.

   ```
   #define _SQLNCLI_ODBC_
   #include <sqlncli.h>
   ```

    Tenga en cuenta que el ejemplo no utiliza realmente ninguna funcionalidad de Native Client, por lo que los pasos anteriores no son necesarios para que se compile y se ejecute. Pero el proyecto ya está configurado para que use esta funcionalidad. Para obtener más información, consulte [Programación de SQL Server Native Client](https://msdn.microsoft.com/library/ms130892\(v=sql.130\).aspx).

7. Especifique el controlador que se va a usar en el subsistema ODBC. En el ejemplo se pasa el atributo de cadena de conexión del controlador en como un argumento de la línea de comandos. En propiedades del **proyecto**  >  **Properties**  >  ,**depurar**, agregue este argumento de comando:

   ```
   DRIVER="SQL Server Native Client 11.0"
   ```

8. Presione F5 para compilar y ejecutar la aplicación. Debería ver un cuadro de diálogo del controlador que le pide que escriba una base de datos. Escriba `(localdb)\MSSQLLocalDB` y Active **Usar conexión de confianza**. Haga clic en **Aceptar**. Debería ver una consola con mensajes que indican una conexión correcta. También debería ver un símbolo del sistema en el que puede escribir una instrucción SQL. En la pantalla siguiente se muestra una consulta de ejemplo y los resultados:

    ![Resultado de la consulta de ejemplo de ODBC](../data-tools/media/raddata-odbc-sample-query-output.png "resultado de la consulta de ejemplo ODBC de raddata")

## <a name="see-also"></a>Consulte también
 [Obtener acceso a datos en Visual Studio](../data-tools/accessing-data-in-visual-studio.md)
