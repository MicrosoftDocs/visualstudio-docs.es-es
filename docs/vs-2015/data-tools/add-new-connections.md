---
title: Agregar nuevas conexiones | Documentos de Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8a93c287-2834-4a83-a590-bdc3fe8d293f
caps.latest.revision: 17
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 03407962b4ea8160d492971367f121835fa39aae
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49218515"
---
# <a name="add-new-connections"></a>Agregar nuevas conexiones
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Puede probar la conexión a una base de datos o un servicio y explorar el contenido de la base de datos y esquemas, mediante el uso de **Explorador de servidores**, **Cloud Explorer**, o **Explorador de objetos de SQL Server**. La funcionalidad de estas ventanas se superpone en cierta medida. Las diferencias básicas son:  
  
 Explorador de servidores  
 Se instala de forma predeterminada en Visual Studio. Puede utilizarse para probar las conexiones y ver bases de datos de SQL Server, las otras bases de datos que tienen instalado un proveedor de ADO.NET y algunos servicios de Azure. También muestra los objetos de bajo nivel, como las colas de mensajes, los registros de eventos y contadores de rendimiento del sistema. Si un origen de datos no tiene ningún proveedor ADO.NET, no se mostrará aquí, pero todavía puede usarlo desde Visual Studio mediante la conexión mediante programación.  
  
 Cloud Explorer  
 Instale esta ventana manualmente como una extensión de Visual Studio seleccionando **herramientas** > **extensiones y actualizaciones** > **Online**  >  **Galería de visual Studio**. Proporciona la funcionalidad especializada para explorar y conectarse a servicios de Azure.  
  
 Explorador de objetos de SQL Server  
 Instale con SQL Server Data Tools y se muestre en el **vista** menú. Si no ve allí, vaya a **programas y características** en el Panel de Control, busque Visual Studio y, a continuación, seleccione **cambio** para volver a ejecutar el programa de instalación después de seleccionar la casilla de verificación para SQL Server Data Tools. Use **Explorador de objetos de SQL Server** para ver bases de datos SQL (si tienen un proveedor de ADO.NET), crear nuevas bases de datos, modificar esquemas, crear procedimientos almacenados, recuperar cadenas de conexión, ver los datos y mucho más. Las bases de datos SQL que no tienen instalado ningún proveedor de ADO.NET no se mostrarán aquí, pero todavía puede conectarse a ellos mediante programación.  
  
## <a name="add-a-connection-in-server-explorer"></a>Agregar una conexión en el Explorador de servidores  
 Para crear una conexión a la base de datos, haga clic en el **Agregar conexión** icono en **Explorador de servidores**, o haga clic en **Explorador de servidores** en el **datos Las conexiones** nodo y seleccione **Agregar conexión**. Desde aquí, también puede conectarse a una base de datos en otro servidor, un servicio de SharePoint o un servicio de Azure.  
  
 ![Icono de explorador nueva conexión de servidor](../data-tools/media/raddata-server-explorer-new-connection-icon.png "raddata icono de explorador nueva conexión de servidor")  
  
 Se abrirá el **Agregar conexión** cuadro de diálogo. En este caso, hemos especificado el nombre de la instancia de SQL Server LocalDB.  
  
 ![Agregar nueva conexión](../data-tools/media/raddata-add-new-connection-dialog.png "raddata el cuadro de diálogo de agregar nueva conexión")  
  
## <a name="change-the-provider"></a>Cambiar el proveedor  
 Si el origen de datos no es lo que desea, haga clic en el **cambio** botón para elegir un origen de datos o un nuevo proveedor de datos ADO.NET. El nuevo proveedor podría solicitar sus credenciales, en función de cómo haya configurado.  
  
 ![Cambiar el proveedor de datos de AD0.NET](../data-tools/media/raddata-change-ad0-net-data-provider.png "raddata proveedor de datos de cambio AD0.NET")  
  
## <a name="test-the-connection"></a>Probar la conexión  
 Una vez que haya elegido el origen de datos, haga clic en **Probar conexión**. Si no tiene éxito, deberá solucionar según la documentación del fabricante.  
  
 ![Probar conexión](../data-tools/media/raddata-test-connection.png "raddata Probar conexión")  
  
 Si la prueba se realiza correctamente, está listo para crear un *origen de datos*, que es un término de Visual Studio que en realidad significa un *modelo de datos* que se basa en la base de datos o el servicio subyacente.  
  
## <a name="see-also"></a>Vea también  
 [Visual Studio Data Tools para .NET](../data-tools/visual-studio-data-tools-for-dotnet.md)

