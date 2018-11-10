---
title: Crear un proyecto de servicio de nube de Azure con Visual Studio | Microsoft Docs
description: Aprenda a crear un proyecto de servicio de nube de Azure con Visual Studio
author: ghogen
manager: douge
assetId: ec580df7-3dcc-45a9-a1d9-8c110678dfb5
ms.prod: visual-studio-dev14
ms.technology: vs-azure
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 03/21/2017
ms.author: ghogen
ms.openlocfilehash: 8149f60440becb3c7a8d0dc08b2a1a9c00fb171a
ms.sourcegitcommit: e481d0055c0724d20003509000fd5f72fe9d1340
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/05/2018
ms.locfileid: "51003026"
---
# <a name="creating-an-azure-cloud-service-project-with-visual-studio"></a>Crear un proyecto de servicio de nube de Azure con Visual Studio
Azure Tools para Visual Studio proporciona una plantilla de proyecto que le permite crear un [servicio nube de Azure](/azure/cloud-services/cloud-services-choose-me), que es un simple servicio de Azure de propósito general. Una vez creado el proyecto, Visual Studio le permite configurar, depurar e implementar el servicio en la nube en Azure.

## <a name="steps-to-create-an-azure-cloud-service-project-in-visual-studio"></a>Pasos para crear un proyecto de servicio de nube de Azure en Visual Studio
En esta sección explica cómo crear un proyecto de servicio de nube de Azure en Visual Studio con uno o varios roles web.  

1. Inicie Visual Studio como administrador.

1. En el menú principal, seleccione **archivo** > **New** > **proyecto**.

1. Seleccione **en la nube** del objeto Visual C# o Visual Basic nodos de plantilla de proyecto y seleccione **Azure Cloud Service** en la lista de plantillas.

    ![Nuevo servicio de nube de Azure](./media/vs-azure-tools-azure-project-create/new-project-wizard-for-cloud-service.png)

1. Especifique qué versión de .NET Framework que desea usar para desarrollar el proyecto.

1. Escriba un nombre y ubicación para el proyecto y un nombre para la solución. 

1. Seleccione **Aceptar**.

1. En el **nuevo servicio en la nube de Microsoft Azure** cuadro de diálogo, seleccione los roles que desea agregar y elija el botón de flecha derecha para agregarlos a la solución.

    ![Seleccione los nuevos roles de servicio de nube de Azure](./media/vs-azure-tools-azure-project-create/new-cloud-service.png)

1. Para cambiar el nombre de un rol que haya agregado, mantenga el mouse sobre el rol en el **nuevo servicio en la nube de Microsoft Azure** cuadro de diálogo y, en el menú contextual, seleccione **cambiar el nombre**. También puede cambiar el nombre un rol dentro de la solución (en el **el Explorador de soluciones**) después de que se ha agregado.

    ![Cambiar el nombre de rol de servicio de nube de Azure](./media/vs-azure-tools-azure-project-create/new-cloud-service-rename.png)

El proyecto de Azure en Visual Studio tiene asociaciones a los proyectos de rol de la solución. El proyecto también incluye el *archivo de definición de servicio* y *archivo de configuración de servicio*:

- **Archivo de definición de servicio** -define la configuración de tiempo de ejecución de la aplicación, incluidos los roles que son necesarios, los puntos de conexión y tamaño de máquina virtual. 
- **Archivo de configuración de servicio** -configura el número de instancias de un rol son ejecución y los valores de la configuración definida para un rol. 

Para obtener más información acerca de estos archivos, consulte [configurar los Roles para un servicio de nube de Azure con Visual Studio](vs-azure-tools-configure-roles-for-cloud-service.md).

## <a name="next-steps"></a>Pasos siguientes
- [Administración de roles en proyectos de servicio de nube de Azure con Visual Studio](./vs-azure-tools-cloud-service-project-managing-roles.md)
