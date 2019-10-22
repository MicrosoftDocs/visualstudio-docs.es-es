---
title: Adición de nuevas conexiones
ms.date: 11/04/2016
ms.topic: conceptual
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 0abce148194b2d88a39f6c651e6f32d0ae7b6642
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72648905"
---
# <a name="add-new-connections"></a>Adición de nuevas conexiones

Puede probar la conexión a una base de datos o servicio, y explorar el contenido y los esquemas de la base de datos mediante **Explorador de servidores**, **Cloud Explorer**o **Explorador de objetos de SQL Server**. La funcionalidad de estas ventanas se superpone hasta cierto punto. Las diferencias básicas son las siguientes:

- Explorador de servidores

   Se instala de forma predeterminada en Visual Studio. Se puede usar para probar las conexiones y ver SQL Server bases de datos, cualquier otra base de datos que tenga un proveedor de ADO.NET instalado y algunos servicios de Azure. También muestra objetos de bajo nivel, como contadores de rendimiento del sistema, registros de eventos y colas de mensajes. Si un origen de datos no tiene ningún proveedor ADO.NET, no aparecerá aquí, pero puede seguir utilizándolo desde Visual Studio conectándose mediante programación.

- Cloud Explorer

   Instale esta ventana manualmente como una extensión de Visual Studio desde [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=ms-azuretools.CloudExplorerForVS). Proporciona funcionalidad especializada para explorar y conectarse a los servicios de Azure.

- Explorador de objetos de SQL Server

   Instalado con SQL Server Data Tools y visible en el menú **Ver** . Si no lo ve allí, vaya a **programas y características** en el panel de control, busque Visual Studio y, luego, seleccione **cambiar** para volver a ejecutar el instalador después de activar la casilla de SQL Server Data Tools. Use **Explorador de objetos de SQL Server** para ver las bases de datos SQL (si tienen un proveedor ADO.net), crear nuevas bases de datos, modificar esquemas, crear procedimientos almacenados, recuperar cadenas de conexión, ver los datos, etc. Las bases de datos SQL que no tienen ningún proveedor ADO.NET instalado no se mostrarán aquí, pero todavía puede conectarse a ellas mediante programación.

## <a name="add-a-connection-in-server-explorer"></a>Agregar una conexión en Explorador de servidores

Para crear una conexión a la base de datos, haga clic en el icono **Agregar conexión** en **Explorador de servidores**, o haga clic con el botón derecho en **Explorador de servidores** en el nodo **conexiones de datos** y seleccione **Agregar conexión**. Desde aquí, también puede conectarse a una base de datos de otro servidor, un servicio de SharePoint o un servicio de Azure.

![Explorador de servidores icono de nueva conexión](../data-tools/media/raddata-server-explorer-new-connection-icon.png)

Se abrirá el cuadro de diálogo **Agregar conexión** . Aquí, hemos escrito el nombre de la instancia SQL Server LocalDB.

![Adición de una nueva conexión](../data-tools/media/raddata-add-new-connection-dialog.png)

## <a name="change-the-provider"></a>Cambiar el proveedor

Si el origen de datos no es lo que desea, haga clic en el botón **cambiar** para elegir un nuevo origen de datos o un nuevo proveedor de datos ADO.net. El nuevo proveedor puede solicitar sus credenciales, en función de cómo se haya configurado.

![Cambiar el proveedor de datos AD0.NET](../data-tools/media/raddata-change-ad0.net-data-provider.png)

## <a name="test-the-connection"></a>Prueba de la conexión

Después de elegir el origen de datos, haga clic en **probar conexión**. Si no se realiza correctamente, tendrá que solucionar los problemas en función de la documentación del proveedor.

![Probar conexión](../data-tools/media/raddata-test-connection.png)

Si la prueba se realiza correctamente, está listo para crear un *origen de datos*, que es un término de Visual Studio que realmente hace referencia a un *modelo de datos* basado en la base de datos o el servicio subyacente.

## <a name="see-also"></a>Vea también

- [Visual Studio Data Tools para .NET](../data-tools/visual-studio-data-tools-for-dotnet.md)
