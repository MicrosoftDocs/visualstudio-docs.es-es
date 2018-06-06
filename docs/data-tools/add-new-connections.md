---
title: Agregar nuevas conexiones
ms.date: 11/04/2016
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: a7b580f8bd04c4fbce9518d903a568bbd0f9175a
ms.sourcegitcommit: 58052c29fc61c9a1ca55a64a63a7fdcde34668a4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/04/2018
ms.locfileid: "34747097"
---
# <a name="add-new-connections"></a>Agregar nuevas conexiones

Puede probar la conexión a una base de datos o un servicio y explorar el contenido de la base de datos y esquemas, puede utilizar **Explorador de servidores**, **Explorer nube**, o **Explorador de objetos de SQL Server**. La funcionalidad de estas ventanas se superpone hasta cierto punto. Las diferencias básicas son:

- Explorador de servidores

   Se instala de forma predeterminada en Visual Studio. Puede utilizarse para probar las conexiones y ver las bases de datos de SQL Server, las otras bases de datos que tienen instalado un proveedor ADO.NET y algunos servicios de Azure. También muestra objetos de bajo nivel, como los contadores de rendimiento de sistema y registros de eventos, colas de mensajes. Si un origen de datos no tiene ningún proveedor ADO.NET, no aparece aquí, pero todavía puede usarlo desde Visual Studio mediante la conexión mediante programación.

- Cloud Explorer

   Instalar manualmente esta ventana como una extensión de Visual Studio mediante la selección **herramientas**, **extensiones y actualizaciones**, **en línea**, **Visual Studio Markeplace**. Proporciona funciones especializadas para explorar y conectarse a los servicios de Azure.

- Explorador de objetos de SQL Server

   Instalado con SQL Server Data Tools y visibles en el **vista** menú. Si no lo ve no existe, vaya a **programas y características** en el Panel de Control, busque Visual Studio y, a continuación, seleccione **cambio** para volver a ejecutar el programa de instalación después de seleccionar la casilla de verificación para SQL Server Data Tools. Use **Explorador de objetos de SQL Server** para ver bases de datos SQL (si tienen un proveedor ADO.NET), crear nuevas bases de datos, modificar esquemas, crear procedimientos almacenados, recuperar cadenas de conexión, ver los datos y mucho más. Las bases de datos SQL que tienen instalado un proveedor de ADO.NET no aparecen aquí, pero todavía puede conectarse a ellos mediante programación.

## <a name="add-a-connection-in-server-explorer"></a>Agregar una conexión en el Explorador de servidores

Para crear una conexión a la base de datos, haga clic en el **Agregar conexión** icono en **Explorador de servidores**, o haga clic en **Explorador de servidores** en el **datos Las conexiones** nodo y seleccione **Agregar conexión**. Desde aquí, también puede conectarse a una base de datos en otro servidor, un servicio de SharePoint o un servicio de Azure.

![Icono de explorador nueva conexión de servidor](../data-tools/media/raddata-server-explorer-new-connection-icon.png)

Se abrirá la **Agregar conexión** cuadro de diálogo. En este caso, se ha introducido el nombre de la instancia de SQL Server LocalDB.

![Agregar nueva conexión](../data-tools/media/raddata-add-new-connection-dialog.png)

## <a name="change-the-provider"></a>Cambiar el proveedor

Si el origen de datos no es lo desea, haga clic en el **cambio** botón para elegir un nuevo origen de datos o un nuevo proveedor de datos ADO.NET. El nuevo proveedor podría solicitar las credenciales, en función de cómo haya configurado.

![Proveedor de datos de cambio AD0.NET](../data-tools/media/raddata-change-ad0.net-data-provider.png)

## <a name="test-the-connection"></a>Probar la conexión

Después de elegir el origen de datos, haga clic en **Probar conexión**. Si no tiene éxito, debe solucionar en función de la documentación del fabricante.

![Probar conexión](../data-tools/media/raddata-test-connection.png)

Si la prueba se realiza correctamente, está listo para crear un *origen de datos*, que es un término de Visual Studio que en realidad significa un *modelo de datos* que se basa en la base de datos o el servicio subyacente.

## <a name="see-also"></a>Vea también

- [Visual Studio Data Tools para .NET](../data-tools/visual-studio-data-tools-for-dotnet.md)