---
title: Creación de un proyecto de servicio en la nube de Azure
description: Obtenga información sobre cómo crear un proyecto de servicio en la nube de Azure con Visual Studio
author: ghogen
manager: jmartens
ms.workload: azure-vs
ms.topic: how-to
ms.date: 03/19/2019
ms.author: ghogen
ms.openlocfilehash: d652172bde2ecd3aea4bb027e46173eaa5fe7b17
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99844507"
---
# <a name="create-an-azure-cloud-service-project-with-visual-studio"></a>Creación de un proyecto de servicio en la nube de Azure con Visual Studio

Visual Studio proporciona una plantilla de proyecto que le permite crear un [servicio en la nube de Azure](/azure/cloud-services/cloud-services-choose-me), que es un servicio de Azure de uso general sencillo. Una vez creado el proyecto, Visual Studio le permite configurar, depurar e implementar el servicio en la nube en Azure.

## <a name="steps-to-create-an-azure-cloud-service-project-in-visual-studio"></a>Pasos para crear un proyecto de servicio en la nube de Azure en Visual Studio
En esta sección se le enseñará cómo crear un proyecto de servicio en la nube de Azure en Visual Studio con uno o más roles web.

::: moniker range="vs-2017"
1. Abra Visual Studio como administrador.

1. En el menú principal, seleccione **Archivo** > **Nuevo** > **Proyecto**.

1. Seleccione **Nube** en los nodos de plantillas de proyectos de Visual C# o Visual Basic y, luego, seleccione **Servicio en la nube de Azure** en la lista de plantillas.

    ![Nuevo servicio en la nube de Azure](./media/vs-azure-tools-azure-project-create/new-project-wizard-for-cloud-service.png)

1. Especifique la versión de .NET Framework que quiere usar para desarrollar el proyecto.

1. Escriba un nombre y una ubicación para el proyecto y un nombre para la solución.

1. Seleccione **Aceptar**.
::: moniker-end
::: moniker range=">=vs-2019"
1. En la ventana de inicio, elija **Crear un proyecto**.

1. En el cuadro de búsqueda, escriba *Nube* y luego elija **Azure Cloud Service**.

   ![Nuevo servicio en la nube de Azure](./media/vs-azure-tools-azure-project-create/vs-2019/new-project-cloud-service.png)

1. Asigne un nombre al proyecto y elija **Crear**.

   ![Asignación de un nombre al proyecto](./media/vs-azure-tools-azure-project-create/vs-2019/new-project-cloud-service-2.png)
::: moniker-end

1. En el cuadro de diálogo **Nuevo servicio en la nube de Microsoft Azure**, seleccione los roles que desea agregar y elija el botón de flecha a la derecha para agregarlos a la solución.

    ![Selección de nuevos roles de servicio en la nube de Azure](./media/vs-azure-tools-azure-project-create/new-cloud-service.png)

1. Para cambiar el nombre de un rol que haya agregado, mantenga el puntero sobre el rol en el cuadro de diálogo **Nuevo servicio en la nube de Microsoft Azure** y, en el menú contextual, seleccione **Cambiar nombre**. También puede cambiar el nombre de un rol dentro de la solución (en el **Explorador de soluciones**) una vez que lo haya agregado.

    ![Cambio de nombre de rol de servicio en la nube de Azure](./media/vs-azure-tools-azure-project-create/new-cloud-service-rename.png)

El proyecto de Azure de Visual Studio tiene asociaciones a los proyectos de rol de la solución. El proyecto incluye también el *archivo de definición de servicio* y el *archivo de configuración de servicio*:

- **Archivo de definición de servicio**: define la configuración del entorno de tiempo de ejecución de la aplicación, incluidos los roles que se requieren, los puntos de conexión y el tamaño de máquina virtual.
- **Archivo de configuración de servicio**: configura el número de instancias de un rol que se ejecutan y los valores de la configuración definida para un rol.

Para obtener más información sobre estos archivos, consulte [configuración de los roles para un servicio en la nube de Azure con Visual Studio](vs-azure-tools-configure-roles-for-cloud-service.md).

## <a name="next-steps"></a>Pasos siguientes
- [Administración de roles en los proyectos de servicio en la nube de Azure con Visual Studio](./vs-azure-tools-cloud-service-project-managing-roles.md)
