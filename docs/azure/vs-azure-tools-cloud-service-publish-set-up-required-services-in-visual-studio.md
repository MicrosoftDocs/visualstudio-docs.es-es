---
title: Preparación para publicar o implementar un servicio en la nube
description: Obtenga más información sobre los procedimientos para configurar los servicios de cuenta de almacenamiento y en la nube y establecer la configuración de la aplicación de Azure.
author: ghogen
manager: jillfra
ms.workload: azure-vs
ms.topic: how-to
ms.date: 11/10/2017
ms.author: ghogen
ms.openlocfilehash: c048968ca97484812b7423a16e4a1834e1c8a66b
ms.sourcegitcommit: 86e98df462b574ade66392f8760da638fe455aa0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/19/2020
ms.locfileid: "94902511"
---
# <a name="prepare-to-publish-or-deploy-a-cloud-service-from-visual-studio"></a>Preparación para publicar o implementar un servicio en la nube desde Visual Studio

Para publicar un proyecto de servicio en la nube, debe configurar los siguientes servicios, según se describe en este artículo:

* Un **servicio en la nube** para ejecutar sus roles en el entorno de Azure
* Una **cuenta de almacenamiento** que proporcione acceso a los servicios Blob, Queue y Table.

## <a name="create-a-cloud-service"></a>un servicio en la nube

Un servicio en la nube ejecuta los roles en el entorno de Azure. Puede crear un servicio en la nube en Visual Studio o a través de [Azure Portal](https://portal.azure.com/), como se describe en las secciones siguientes.

### <a name="create-a-cloud-service-from-visual-studio"></a>Creación de un servicio en la nube desde Visual Studio

1. Con un proyecto de servicio en la nube creado anteriormente, haga clic con el botón derecho y seleccione **Publicar**.
1. Si es necesario, inicie sesión con la cuenta Microsoft o la cuenta de organización asociada con la suscripción de Azure y después seleccione **Siguiente** para avanzar a la página **Configuración**.
1. Se abre el cuadro de diálogo **Crear servicio en la nube y cuenta de almacenamiento** (si no aparece, seleccione **Crear nuevo** en la lista **Servicio en la nube**).
1. Escriba un nombre que no distinga mayúsculas y minúsculas para el servicio en la nube, que forma parte de la dirección URL y debe ser exclusivo. Elija también una región o un grupo de afinidad y seleccione una opción de replicación.

### <a name="create-a-cloud-service-through-the-azure-portal"></a>Creación de un servicio en la nube en Azure Portal

1. Inicie sesión en [Azure Portal](https://portal.azure.com/).
1. Seleccione **Cloud Services (clásico)** en el lado izquierdo de la página.
1. Seleccione **+ Agregar** y después proporcione la información necesaria (nombre DNS, suscripción, grupo de recursos y ubicación). No es necesario cargar un paquete en este momento, ya que lo hará más adelante en Visual Studio.
1. Seleccione **Crear** para completar el proceso.

## <a name="create-a-storage-account"></a>Crear una cuenta de almacenamiento

Una cuenta de almacenamiento proporciona acceso a los servicios Blob, Queue y Table. Puede crear una cuenta de almacenamiento mediante Visual Studio o en [Azure Portal](https://portal.azure.com/).

### <a name="create-a-storage-account-from-visual-studio"></a>Creación de una cuenta de almacenamiento en Visual Studio

1. En el **Explorador de soluciones** con un proyecto de servicio en la nube creado anteriormente, localice el nodo **Servicios conectados** en un proyecto de rol, haga clic con el botón derecho y seleccione **Agregar servicio conectado**. (En Visual Studio 2015, haga clic con el botón derecho en el nodo **Storage** y seleccione **Crear cuenta de almacenamiento**).
1. En la lista de **Servicios conectados** que aparece, seleccione **Almacenamiento en la nube con Azure Storage**.
1. En el cuadro de diálogo de Azure Storage que aparece, seleccione **+Crear nueva cuenta de almacenamiento** para que se abra un cuadro de diálogo en el que debe especificar la suscripción, el nombre de la cuenta, un plan de tarifa, el grupo de recursos y la ubicación.
1. Seleccione **Crear** cuando haya terminado. La nueva cuenta de almacenamiento aparece en la lista de cuentas de almacenamiento disponibles en su suscripción.
1. Seleccione esa cuenta y, después, **Agregar**.

### <a name="create-a-storage-account-through-the-azure-portal"></a>Creación de una cuenta de almacenamiento en Azure Portal

1. Inicie sesión en [Azure Portal](https://portal.azure.com/).
1. Seleccione **+ Nuevo** en el lado superior izquierdo.
1. Seleccione **Storage** en "Azure Marketplace" y, después, **Cuenta de almacenamiento: blob, archivo, tabla, cola** en el lado derecho.
1. Proporcione la información necesaria (nombre, modelo de implementación, etc.).
1. Seleccione **Crear** para completar el proceso.

## <a name="configure-your-app-to-use-the-storage-account"></a>Configuración de la aplicación para usar la cuenta de almacenamiento

Después de crear una cuenta de almacenamiento, si se conecta a ella desde Visual Studio, se actualizan automáticamente las configuraciones del servicio relacionadas con el proyecto, incluidas las direcciones URL y las claves de acceso.

Si creó un servicio en la nube en Visual Studio con la opción **Agregar servicio conectado**, puede comprobar las conexiones si abre `ServiceConfiguration.Cloud.cscfg` y `ServiceConfiguration.Local.cscfg`.

Si creó un servicio en la nube en Azure Portal, siga los mismos pasos descritos en [Creación de una cuenta de almacenamiento en Visual Studio](#create-a-storage-account-from-visual-studio), pero seleccione la cuenta existente en lugar de crear otra. Visual Studio se encarga de actualizar la configuración.

Para realizar la configuración manualmente, use las páginas de propiedades de Visual Studio para el rol aplicable del proyecto de servicio en la nube (haga clic con el botón derecho en el rol y seleccione **Propiedades**). Para más información, vea [Configuración de una cadena de conexión para una cuenta de almacenamiento](vs-azure-tools-multiple-services-project-configurations.md#configuring-a-connection-string-for-a-storage-account).

### <a name="about-access-keys"></a>Acerca de las claves de acceso

Azure Portal muestra las direcciones URL que puede usar para acceder a recursos en cada uno de los servicios de almacenamiento de Azure, además de las claves de acceso principal y secundaria para la cuenta. Use estas claves para autenticar las solicitudes realizadas en los servicios de almacenamiento.

La clave de acceso secundaria proporciona el mismo acceso a la cuenta de almacenamiento que la clave de acceso principal y se genera como copia de seguridad en caso de que la clave de acceso principal estuviese en peligro. Además, se recomienda volver a generar las claves de acceso de forma periódica. Puede modificar la configuración de una cadena de conexión para que use la clave secundaria mientras se regenera la clave principal y, luego, volver a modificarla para que use la clave principal regenerada mientras se regenera la clave secundaria.

## <a name="next-steps"></a>Pasos siguientes

Para obtener más información acerca de la publicación de aplicaciones en Azure desde Visual Studio, consulte [Publicar un servicio en la nube mediante Azure Tools](vs-azure-tools-publishing-a-cloud-service.md).
