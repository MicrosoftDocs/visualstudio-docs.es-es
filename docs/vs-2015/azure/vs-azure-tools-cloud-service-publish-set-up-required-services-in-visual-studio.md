---
title: Preparación para publicar o implementar un servicio en la nube desde Visual Studio | Microsoft Docs
description: Obtenga información sobre los procedimientos para configurar los servicios en la nube y el almacenamiento de la cuenta y configurar la aplicación de Azure.
author: ghogen
manager: douge
ms.assetid: 92ee2f9e-ec49-4c7a-900d-620abe5e9d8a
ms.prod: visual-studio-dev14
ms.technology: vs-azure
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 11/10/2017
ms.author: ghogen
ms.openlocfilehash: d7643d87f60b953b9c0928571036c7890e4d11f0
ms.sourcegitcommit: e481d0055c0724d20003509000fd5f72fe9d1340
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/05/2018
ms.locfileid: "51002976"
---
# <a name="prepare-to-publish-or-deploy-a-cloud-service-from-visual-studio"></a>Preparación para publicar o implementar un servicio en la nube desde Visual Studio

Para publicar un proyecto de servicio en la nube, debe configurar los siguientes servicios como se describe en este artículo:

* Un **servicio en la nube** para ejecutar sus roles en el entorno de Azure, y 
* Un **cuenta de almacenamiento** que proporciona acceso a los servicios Blob, Queue y Table.

## <a name="create-a-cloud-service"></a>Crear un servicio en la nube

Un servicio en la nube ejecuta sus roles en el entorno de Azure. Puede crear un servicio en la nube en Visual Studio o a través del [portal Azure](https://portal.azure.com/) como se describe en las secciones siguientes.

### <a name="create-a-cloud-service-from-visual-studio"></a>Crear un servicio de nube desde Visual Studio

1. Con un proyecto de servicio en la nube creado anteriormente, haga clic en el proyecto y seleccione **publicar**.
1. Si es necesario, inicie sesión con Microsoft o cuenta de organización asociada con su suscripción de Azure y luego seleccione **siguiente** para avanzar a la **configuración** página.
1. Un **crear servicio en la nube y cuenta de almacenamiento** aparece el cuadro de diálogo (si no, seleccione **crear nuevo** desde el **servicio en la nube** lista).
1. Escriba un nombre para el servicio en la nube, que forma parte de la dirección URL y debe ser único entre mayúsculas y minúsculas. También elegir un grupo de afinidad o región y seleccione una opción de replicación.

### <a name="create-a-cloud-service-through-the-azure-portal"></a>Crear un servicio de nube a través del portal de Azure

1. Inicie sesión en [Azure Portal](https://portal.azure.com/).
1. Seleccione **servicios en la nube (clásico)** en el lado izquierdo de la página.
1. Seleccione **+ agregar**, a continuación, proporcione la información necesaria (nombre DNS, suscripción, grupo de recursos y ubicación). No es necesario cargar un paquete en este momento porque hacerlo más adelante en Visual Studio.
1. Seleccione **crear** para completar el proceso.

## <a name="create-a-storage-account"></a>Crear una cuenta de almacenamiento

Una cuenta de almacenamiento proporciona acceso a los servicios Blob, Queue y Table. Puede crear una cuenta de almacenamiento a través de Visual Studio o el [portal Azure](https://portal.azure.com/).

### <a name="create-a-storage-account-from-visual-studio"></a>Crear una cuenta de almacenamiento desde Visual Studio

1. En **el Explorador de soluciones** con un proyecto de servicio en la nube creado anteriormente, busque el **Connected Services** nodo dentro de un proyecto de rol, contextual y seleccione **Agregar servicio conectado**. (En Visual Studio 2015, haga clic en el **almacenamiento** nodo y seleccione **crear cuenta de almacenamiento**.)
1. En el **Connected Services** lista que aparece, haga clic **almacenamiento en la nube con Azure Storage**.
1. En el cuadro de diálogo Azure Storage que aparece, seleccione **+ crear nueva cuenta de almacenamiento**, que abre un cuadro de diálogo en el que se debe especificar la suscripción, un nombre de la cuenta, una tarifa nivel, grupo de recursos y ubicación.
1. Seleccione **crear** cuando haya terminado. La nueva cuenta de almacenamiento aparece en la lista de cuentas de almacenamiento disponible en su suscripción.
1. Seleccione esa cuenta y seleccione **agregar**.

### <a name="create-a-storage-account-through-the-azure-portal"></a>Crear una cuenta de almacenamiento a través del portal de Azure

1. Inicie sesión en [Azure Portal](https://portal.azure.com/).
1. Seleccione **+ nuevo** en la esquina superior izquierda.
1. Seleccione **almacenamiento** en "Azure Marketplace,", a continuación, **cuenta de almacenamiento: blob, archivo, tabla, cola** desde el lado derecho.
1. Proporcione la información necesaria (nombre, modelo de implementación y así sucesivamente.
1. Seleccione **crear** para completar el proceso.

## <a name="configure-your-app-to-use-the-storage-account"></a>Configurar la aplicación para usar la cuenta de almacenamiento

Después de crear una cuenta de almacenamiento, se conecta a él desde Visual Studio automáticamente actualizaciones de las configuraciones de servicio para el proyecto, incluidas las direcciones URL y las claves de acceso.

Si crea un servicio de nube desde Visual Studio mediante el **Agregar servicio conectado**, puede comprobar las conexiones abriendo `ServiceConfiguration.Cloud.cscfg` y `ServiceConfiguration.Local.cscfg`.

Si ha creado un servicio de nube a través del portal de Azure, siga los mismos pasos en [crear una cuenta de almacenamiento desde Visual Studio](#create-a-storage-account-from-visual-studio) pero seleccione la cuenta existente, en lugar de crear uno nuevo. Visual Studio, a continuación, actualiza la configuración para usted.

Para configurar la configuración manualmente, use las páginas de propiedades en Visual Studio para el rol aplicable en el proyecto de servicio en la nube (haga clic en el rol y seleccione **propiedades**). Para obtener más información, consulte [configuración de una cadena de conexión a una cuenta de almacenamiento](vs-azure-tools-multiple-services-project-configurations.md#configuring-a-connection-string-for-a-storage-account).

### <a name="about-access-keys"></a>Acerca de las claves de acceso

Azure portal muestra las direcciones URL que puede usar para tener acceso a recursos en cada uno de los servicios de almacenamiento de Azure y también las claves de acceso principal y secundaria para la cuenta. Utilice estas claves para autenticar las solicitudes realizadas en los servicios de almacenamiento.

La clave de acceso secundaria proporciona el mismo acceso a la cuenta de almacenamiento como clave de acceso principal y se genera como una copia de seguridad debería en peligro su clave de acceso principal. Además, se recomienda volver a generar las claves de acceso de forma periódica. Puede modificar una configuración de la cadena de conexión para usar la clave secundaria mientras regenera la clave principal, a continuación, puede modificarla para usar la clave principal regenerada mientras se regenera la clave secundaria.

## <a name="next-steps"></a>Pasos siguientes

Para obtener más información sobre cómo publicar aplicaciones a Azure desde Visual Studio, consulte [publicar un servicio en la nube mediante Azure Tools](vs-azure-tools-publishing-a-cloud-service.md).
