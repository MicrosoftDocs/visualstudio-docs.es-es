---
title: Uso de Emulator Express para ejecutar y depurar un servicio en la nube de Azure en un sistema local | Microsoft Docs
description: Uso de Emulator Express para ejecutar y depurar un servicio en la nube en un sistema local
author: mikejo5000
manager: jillfra
ms.assetid: 73108f98-a552-4817-b7a1-551367b71906
ms.topic: conceptual
ms.workload: azure-vs
ms.date: 03/06/2017
ms.author: mikejo
ms.prod: visual-studio-dev14
ms.technology: vs-azure
ms.openlocfilehash: b7e1d5e63a93f8fe1f67de920a1ccf7966d97ed6
ms.sourcegitcommit: 117ece52507e86c957a5fd4f28d48a0057e1f581
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/28/2019
ms.locfileid: "66263770"
---
# <a name="using-emulator-express-to-run-and-debug-an-azure-cloud-service-on-a-local-machine"></a>Uso de Emulator Express para ejecutar y depurar un servicio en la nube de Azure en un sistema local
Con Emulator Express, puede probar y depurar un servicio en la nube sin ejecutar Visual Studio como administrador. Puede establecer la configuración del proyecto para usar Emulator Express o el emulador completo, según los requisitos de su servicio en la nube. Para obtener más información sobre el emulador completo, consulte [Ejecutar una aplicación de Azure en el emulador de proceso](/azure/storage/common/storage-use-emulator).

## <a name="using-emulator-express-in-visual-studio"></a>Uso de Emulator Express en Visual Studio
Al crear un proyecto de Azure en Azure SDK 2.3 o posterior, Emulator Express se usa automáticamente. En los proyectos existentes que se crearon con una versión anterior de Azure SDK, siga estos pasos para seleccionar Emulator Express:

1. Cree o abra un proyecto de servicio en la nube de Azure en Visual Studio.

1. En el **Explorador de soluciones**, haga clic con el botón derecho en el proyecto y, en el menú contextual, seleccione **Propiedades**.

1. En las páginas de propiedades de proyectos, seleccione la pestaña **Web**.

    ![Propiedades de proyecto de servicio en la nube de Azure](./media/vs-azure-tools-emulator-express-debug-run/web-properties.png)

1. En **Servidor de desarrollo local**, seleccione la opción **Usar IIS Express**.

1. En **Emulador**, seleccione **usar Emulator Express**.
   
1. Ejecute el siguiente comando en un símbolo del sistema para iniciar Emulator Express: 

    ```
    csrun.exe /useemulatorexpress
    ```

## <a name="emulator-express-limitations"></a>Limitaciones de Emulator Express
Los siguientes problemas son limitaciones conocidas de Emulator Express: 

- Emulator Express no es compatible con el servidor web de IIS.
- Su servicio en la nube puede contener varios roles, pero cada rol se limita a una instancia.
- No puede tener acceso a los números de puerto inferiores a 1000. Si utiliza un proveedor de autenticación que suele usar un puerto inferior a 1000, puede que tenga que cambiar este valor a un número de puerto superior a 1000.
- Las limitaciones que se aplican al emulador de Azure Compute se aplican también a Emulator Express. Por ejemplo, no puede tener más de 50 instancias de rol por implementación. Para obtener más información sobre el emulador de Azure Compute, consulte [Ejecutar una aplicación de Azure en el emulador de proceso](http://go.microsoft.com/fwlink/p/?LinkId=623050).

## <a name="next-steps"></a>Pasos siguientes
[Depuración de servicios en la nube de Azure](vs-azure-tools-debugging-cloud-services-overview.md)
