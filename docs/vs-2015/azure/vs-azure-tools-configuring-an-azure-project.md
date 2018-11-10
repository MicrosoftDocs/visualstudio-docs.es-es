---
title: Configurar un proyecto de servicio de nube de Azure con Visual Studio | Microsoft Docs
description: Obtenga información sobre cómo configurar un proyecto de servicio de nube de Azure en Visual Studio, dependiendo de los requisitos para ese proyecto.
author: ghogen
manager: douge
assetId: 609d6965-05cc-47b1-82dc-c76a92d4f295
ms.prod: visual-studio-dev14
ms.technology: vs-azure
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 03/06/2017
ms.author: ghogen
ms.openlocfilehash: 7417bc117de7dc472f413dd9145944cad2d48bb4
ms.sourcegitcommit: e481d0055c0724d20003509000fd5f72fe9d1340
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/05/2018
ms.locfileid: "51002955"
---
# <a name="configure-an-azure-cloud-service-project-with-visual-studio"></a>Configuración de un proyecto de servicio en la nube de Azure con Visual Studio
Puede configurar un proyecto de servicio de nube de Azure, dependiendo de los requisitos para ese proyecto. Puede establecer las propiedades del proyecto para las siguientes categorías:

- **Publicar un servicio en la nube en Azure** : puede establecer una propiedad para asegurarse de que no se elimina accidentalmente un servicio en la nube existente implementado en Azure.
- **Ejecutar o depurar un servicio en la nube en el equipo local** -puede seleccionar una configuración de servicio para utilizarla e indicar si desea iniciar el emulador de almacenamiento de Azure.
- **Validar un paquete de servicio en la nube cuando se crea** -puede decidir tratar las advertencias como errores, por lo que puede asegurarse de que implementa el paquete de servicio en la nube sin ningún problema. 

## <a name="steps-to-configure-an-azure-cloud-service-project"></a>Pasos para configurar un proyecto de servicio de nube de Azure
1. Abra o cree un proyecto de servicio en la nube en Visual Studio

1. En **el Explorador de soluciones**, haga clic en el proyecto y, en el menú contextual, seleccione **propiedades**.
   
1. En la página de propiedades del proyecto, seleccione el **desarrollo** ficha.

    ![Menú propiedades del proyecto](./media/vs-azure-tools-configuring-an-azure-project/solution-explorer-project-properties-menu.png)

1. Establecer **Preguntar antes de eliminar una implementación existente** a **True**. Esta configuración ayuda a garantizar que no elimina accidentalmente una implementación existente en Azure

1. Seleccione el elemento **configuración del servicio** para indicar qué configuración de servicio que desea usar al ejecutar o depurar su servicio en la nube localmente. Para obtener más información sobre cómo modificar una configuración de servicio para un rol, consulte [cómo configurar los roles para un servicio de nube de Azure con Visual Studio](./vs-azure-tools-configure-roles-for-cloud-service.md).

1. Establecer **emulador de almacenamiento de Azure inicie** a **True** para iniciar el emulador de almacenamiento de Azure al ejecutar o depurar su servicio en la nube localmente.

1. Establecer **tratar advertencias como errores** a **True** para asegurarse de que no se puede publicar si hay errores de validación del paquete.

1. Establecer **usar puertos de proyecto web** a **True** para asegurarse de que su rol web usa el mismo puerto cada vez que se inicia localmente en IIS Express.

1. En la barra de herramientas de Visual Studio, seleccione **guardar**.

## <a name="next-steps"></a>Pasos siguientes
- [Configurar un proyecto de Azure mediante varias configuraciones de servicio](vs-azure-tools-multiple-services-project-configurations.md)

