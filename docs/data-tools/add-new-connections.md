---
title: Agregar nuevas conexiones | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
caps.latest.revision: "14"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.workload: data-storage
ms.openlocfilehash: 26a45e8fe44e2e0945a105711ae84b1082d5c891
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
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

![Icono de explorador nueva conexión de servidor](../data-tools/media/raddata-server-explorer-new-connection-icon.png "raddata icono de explorador nueva conexión de servidor")

Se abrirá la **Agregar conexión** cuadro de diálogo. En este caso, se ha introducido el nombre de la instancia de SQL Server LocalDB.  

![Agregar nueva conexión](../data-tools/media/raddata-add-new-connection-dialog.png "raddata el cuadro de diálogo de agregar nueva conexión")  

## <a name="change-the-provider"></a>Cambiar el proveedor

Si el origen de datos no es lo desea, haga clic en el **cambio** botón para elegir un nuevo origen de datos o un nuevo proveedor de datos ADO.NET. El nuevo proveedor podría solicitar las credenciales, en función de cómo haya configurado.

![Cambiar el proveedor de datos de AD0.NET](../data-tools/media/raddata-change-ad0.net-data-provider.png "raddata proveedor de datos de cambio AD0.NET")

## <a name="test-the-connection"></a>Probar la conexión

Después de elegir el origen de datos, haga clic en **Probar conexión**. Si no tiene éxito, debe solucionar en función de la documentación del fabricante.

![Probar conexión](../data-tools/media/raddata-test-connection.png "raddata Probar conexión")

Si la prueba se realiza correctamente, está listo para crear un *origen de datos*, que es un término de Visual Studio que en realidad significa un *modelo de datos* que se basa en la base de datos o el servicio subyacente.

## <a name="see-also"></a>Vea también

[Visual Studio Data Tools para .NET](../data-tools/visual-studio-data-tools-for-dotnet.md)