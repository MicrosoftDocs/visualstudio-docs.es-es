---
title: Emulator Express para ejecutar o depurar el servicio en la nube de Azure localmente
ms.custom: SEO-VS-2020
description: Uso de Emulator Express para ejecutar y depurar un servicio en la nube en un sistema local
author: mikejo5000
manager: jillfra
ms.topic: how-to
ms.workload: azure-vs
ms.date: 03/06/2017
ms.author: mikejo
ms.openlocfilehash: dee97ab487f4e165fd372559e51b6f19c3501e9f
ms.sourcegitcommit: 86e98df462b574ade66392f8760da638fe455aa0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/19/2020
ms.locfileid: "94902446"
---
# <a name="using-emulator-express-to-run-and-debug-an-azure-cloud-service-on-a-local-machine"></a>Uso de Emulator Express para ejecutar y depurar un servicio en la nube de Azure en un sistema local
Con Emulator Express, puede probar y depurar un servicio en la nube sin ejecutar Visual Studio como administrador. Puede establecer la configuración del proyecto para usar Emulator Express o el emulador completo, según los requisitos de su servicio en la nube. Para obtener más información sobre el emulador completo, consulte [Ejecutar una aplicación de Azure en el emulador de proceso](/azure/storage/common/storage-use-emulator).

## <a name="using-emulator-express-in-visual-studio"></a>Uso de Emulator Express en Visual Studio
Al crear un proyecto de Azure en Azure SDK 2.3 o posterior, Emulator Express se usa automáticamente. En los proyectos existentes que se crearon con una versión anterior de Azure SDK, siga estos pasos para seleccionar Emulator Express:

1. Cree o abra un proyecto de servicio en la nube de Azure en Visual Studio.

1. En Explorador de soluciones, haga clic con el botón secundario en el proyecto y, en el menú contextual, seleccione **propiedades**.

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
- Las limitaciones que se aplican al emulador de Azure Compute se aplican también a Emulator Express. Por ejemplo, no puede tener más de 50 instancias de rol por implementación. Para obtener más información sobre el emulador de Azure Compute, consulte [Ejecutar una aplicación de Azure en el emulador de proceso](vs-azure-tools-performance-profiling-cloud-services.md).

## <a name="next-steps"></a>Pasos siguientes
[Depuración de servicios en la nube de Azure](vs-azure-tools-debugging-cloud-services-overview.md)
