---
title: Visual Studio data tools para C++ | Documentos de Microsoft
ms.custom: ''
ms.date: 2018-06-30
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3a3849d9-1bc7-47d1-805e-1755223ccba2
caps.latest.revision: 12
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: cecad69f6df283ed005afd00a6b9bedbd51c6cd5
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47580780"
---
# <a name="visual-studio-data-tools-for-c"></a>Visual Studio data tools para C++
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [Visual Studio data tools para C++](https://docs.microsoft.com/visualstudio/data-tools/visual-studio-data-tools-for-cpp).  
  
  
C++ nativo a menudo pueden proporcionar el rendimiento más rápido cuando se tiene acceso a orígenes de datos. Sin embargo, no están tan enriquecidos como para aplicaciones .NET datos herramientas para aplicaciones de C++ en Visual Studio. Por ejemplo, no se puede usar las ventanas de orígenes de datos para arrastrar y colocar los orígenes de datos a una superficie de diseño de C++. Si necesita una capa de objeto-relacional, tendrá que escribir el suyo propio, o utilizar un producto de terceros.  Lo mismo puede decirse de funcionalidad de enlace de datos, aunque las aplicaciones que usan la biblioteca Microsoft Foundation Class pueden utilizar algunas clases de base de datos, junto con los documentos y vistas, para almacenar datos en memoria y mostrarla al usuario. Para obtener más información, consulte [acceso a datos en Visual C++](https://msdn.microsoft.com/library/7wtdsdkh.aspx) .  
  
 Para conectarse a bases de datos SQL, aplicaciones nativas de C++ pueden utilizar los controladores ODBC y OLE DB y el proveedor de ADO que se incluyen con Windows.     Estos pueden conectarse a cualquier base de datos que es compatible con esas interfaces. El controlador ODBC es el estándar. OLE DB se proporciona por compatibilidad con versiones anteriores. Para obtener más información sobre estas tecnologías de datos, vea [Windows Data Access Components](https://msdn.microsoft.com/library/windows/desktop/aa968814\(v=vs.85\).aspx)  
  
 Para aprovechar la funcionalidad personalizada de SQL Server 2005 y versiones posteriores, utilice el [SQL Server Native Client](https://msdn.microsoft.com/sqlserver/aa937733). El cliente nativo también contiene el controlador ODBC de SQL Server y el proveedor OLE DB de SQL Server en una biblioteca de vínculos dinámicos (DLL). Son compatibles con las aplicaciones que usan la API de código nativo (ODBC, OLE DB y ADO) a Microsoft SQL Server.  SQL Server Native Client se instala con SQL Server Data Tools. La Guía de programación está aquí: [SQL Server Native Client Programming](https://msdn.microsoft.com/library/ms130892.aspx).  
  
## <a name="to-connect-to-localdb-through-odbc-and-sql-native-client-from-a-c-application"></a>Para conectarse a localDB mediante ODBC y SQL Native Client desde una aplicación de C++  
  
1.  Instalar SQL Server Data Tools.  
  
2.  Si necesita una base de datos SQL de ejemplo para conectarse a, descargue la base de datos Northwind y descomprímalo en una nueva ubicación.  
  
3.  Use SQL Server Management Studio para adjuntar el archivo Northwind.mdf sin comprimir en localDB. Cuando se inicia SQL Server Management Studio, conéctese a (localdb) \MSSQLLocalDB.  
  
     ![Cuadro de diálogo de conexión de SSMS](../data-tools/media/raddata-ssms-connect-dialog.png "raddata SSMS el diálogo de conexión")  
  
     A continuación, haga doble clic en el nodo de localdb en el panel izquierdo y elija **adjuntar**.  
  
     ![SSMS adjuntar base de datos](../data-tools/media/raddata-ssms-attach-database.png "SSMS adjuntar base de datos raddata")  
  
4.  Descargue el ejemplo de SDK de Windows de ODBC y descomprímalo en una nueva ubicación. Este ejemplo muestra los comandos básicos de ODBC que se usan para conectarse a una base de datos y emitir consultas y comandos. Puede aprender más acerca de esas funciones en el [Microsoft Open Database Connectivity (ODBC)](https://msdn.microsoft.com/library/windows/desktop/ms710252\(v=vs.85\).aspx). Cuando se carga primero la solución (está en la carpeta de C++), Visual Studio le sugerirá actualizar la solución a la versión actual de Visual Studio. Haga clic en **Sí**.  
  
5.  Para usar al cliente nativo, necesita su archivo de encabezado y un archivo lib. Estos archivos contienen las funciones y las definiciones específicas de SQL Server, más allá de las funciones ODBC definidas en sql.h. En **proyecto** > **propiedades** > **directorios de VC ++**, agregue el siguiente directorio de inclusión:  
  
 **\<unidad del sistema >: \Program Files\Microsoft SQL Server\110\SDK\Include** y este directorio de biblioteca:  
  
 **c:\Program Files\Microsoft SQL Server\110\SDK\Lib**  
  
6.  Agregue estas líneas odbcsql.cpp. El #define impide que las definiciones de OLE DB irrelevantes desde que se está compilando.  
  
    ```  
    #define _SQLNCLI_ODBC_  
    #include <sqlncli.h>  
    ```  
  
     Tenga en cuenta que el ejemplo no utiliza realmente ninguna funcionalidad de cliente nativo, por lo que no son necesarios para compilar y ejecutar los pasos anteriores. Pero el proyecto ahora está configurado para que usar esta funcionalidad. Para obtener más información, consulte [SQL Server Native Client Programming](https://msdn.microsoft.com/library/ms130892\(v=sql.130\).aspx).  
  
7.  Especifique qué controlador usar en el subsistema ODBC. El ejemplo pasa el atributo de cadena de conexión de controlador en como un argumento de línea de comandos. En **proyecto** > **propiedades** > **depuración**, agregue este argumento de comando:  
  
    ```  
    DRIVER="SQL Server Native Client 11.0"  
    ```  
  
8.  Presione F5 para compilar y ejecutar la aplicación. Debería ver un cuadro de diálogo desde el controlador que se le pide que escriba una base de datos. Escriba `(localdb)\MSSQLLocalDB`y compruebe **utilizar conexión de confianza**. Presione **Aceptar**. Debería ver una consola con los mensajes que indican una conexión correcta. También verá un símbolo del sistema donde puede escribir una instrucción SQL. La siguiente pantalla muestra un ejemplo de consulta y los resultados:  
  
     ![Salida de la consulta de ejemplo de ODBC](../data-tools/media/raddata-odbc-sample-query-output.png "raddata salida de la consulta de ejemplo de ODBC")  
  
## <a name="see-also"></a>Vea también  
 [Obtener acceso a los datos en Visual Studio](../data-tools/accessing-data-in-visual-studio.md)


