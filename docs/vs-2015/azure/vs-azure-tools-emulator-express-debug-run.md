---
title: Uso de Emulator Express para ejecutar y depurar un servicio de nube de Azure en un equipo local | Microsoft Docs
description: Uso de Emulator Express para ejecutar y depurar un servicio en la nube en un equipo local
author: mikejo5000
manager: douge
ms.assetid: 73108f98-a552-4817-b7a1-551367b71906
ms.topic: conceptual
ms.workload: azure-vs
ms.date: 03/06/2017
ms.author: mikejo
ms.prod: visual-studio-dev14
ms.technology: vs-azure
ms.openlocfilehash: 28dd59e3d691df0199afffe93d68d60668c6afe4
ms.sourcegitcommit: e481d0055c0724d20003509000fd5f72fe9d1340
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/05/2018
ms.locfileid: "51002345"
---
# <a name="using-emulator-express-to-run-and-debug-an-azure-cloud-service-on-a-local-machine"></a>Uso del emulador rápido para ejecutar y depurar un servicio en la nube de Azure en un equipo local
Mediante el uso de Emulator Express, puede probar y depurar un servicio en la nube sin ejecutar Visual Studio como administrador. Puede establecer la configuración del proyecto para usar Emulator Express o el emulador completo, según los requisitos del servicio en la nube. Para obtener más información sobre el emulador completo, vea [ejecutar una aplicación de Azure en el emulador de proceso](/azure/storage/common/storage-use-emulator).

## <a name="using-emulator-express-in-visual-studio"></a>Uso de Emulator Express en Visual Studio
Cuando se crea un proyecto de Azure en Azure SDK 2.3 o posterior, Emulator Express se utiliza automáticamente. Para obtener información sobre los proyectos existentes que se crearon con una versión anterior del SDK de Azure, siga estos pasos para seleccionar Emulator Express:

1. Cree o abra un proyecto de servicio de nube de Azure en Visual Studio.

1. En **el Explorador de soluciones**, haga clic en el proyecto y, en el menú contextual, seleccione **propiedades**.

1. En las páginas de propiedades de proyectos, seleccione el **Web** ficha.

    ![Propiedades de un proyecto de servicio de nube de Azure](./media/vs-azure-tools-emulator-express-debug-run/web-properties.png)

1. En **servidor de desarrollo Local**, seleccione **opción usar IIS Express**.

1. En **emulador**, seleccione **usar Emulator Express**.
   
1. Para iniciar Emulator Express, ejecute el siguiente comando en un símbolo del sistema: 

    ```
    csrun.exe /useemulatorexpress
    ```

## <a name="emulator-express-limitations"></a>Limitaciones de Emulator Express
Los siguientes problemas son limitaciones conocidos de Emulator Express: 

- Emulator Express no es compatible con el servidor Web de IIS.
- El servicio de nube puede contener varios roles, pero cada rol se limita a una instancia.
- No se puede tener acceso a los números de puerto inferiores a 1000. Si usa un proveedor de autenticación que suele usa un puerto inferior a 1000, es posible que deba cambiar este valor a un número de puerto superior a 1000.
- Las limitaciones que se aplican al emulador de Azure Compute se aplican también a Emulator Express. Por ejemplo, no puede tener más de 50 instancias de rol por implementación. Para obtener más información sobre el emulador de proceso de Azure, consulte [ejecutar una aplicación de Azure en el emulador de proceso](http://go.microsoft.com/fwlink/p/?LinkId=623050).

## <a name="next-steps"></a>Pasos siguientes
[Depuración de Azure cloud services](https://msdn.microsoft.com/library/azure/ee405479.aspx)
