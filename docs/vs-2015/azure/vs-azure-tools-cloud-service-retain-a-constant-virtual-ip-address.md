---
title: Cómo conservar una dirección IP virtual constante para un servicio de nube de Azure | Microsoft Docs
description: Obtenga información sobre cómo asegurarse de que no cambia la dirección IP virtual (VIP) del servicio en la nube de Azure.
author: ghogen
manager: douge
assetId: 4a58e2c6-7a79-4051-8a2c-99182ff8b881
ms.prod: visual-studio-dev14
ms.technology: vs-azure
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 03/21/2017
ms.author: ghogen
ms.openlocfilehash: e74cc5b9bbbfea92d2dea2c00ee5b0f98dc02f21
ms.sourcegitcommit: e481d0055c0724d20003509000fd5f72fe9d1340
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/05/2018
ms.locfileid: "51002896"
---
# <a name="retain-a-constant-virtual-ip-address-for-an-azure-cloud-service"></a>Conservación de una dirección IP virtual constante para un servicio en la nube de Azure
Cuando se actualiza un servicio en la nube que se hospeda en Azure, debe asegurarse de que no cambia la dirección IP virtual (VIP) del servicio. Muchos servicios de dominio de administración usan el sistema de nombres de dominio (DNS) para registrar nombres de dominio. DNS solo funciona si la dirección VIP sigue siendo el mismo. Puede usar el **Asistente para publicación** en herramientas de Azure para asegurarse de que la dirección VIP del servicio en la nube no cambia cuando se actualice. Para obtener más información sobre cómo usar la administración de dominios DNS para servicios en la nube, consulte [configurar un nombre de dominio personalizado para un servicio de nube de Azure](/azure/cloud-services/cloud-services-custom-domain-name-portal).

## <a name="publish-a-cloud-service-without-changing-its-vip"></a>Publicar un servicio en la nube sin cambiar su VIP
La dirección VIP de un servicio en la nube se asigna al primer lugar implementarla en Azure en un entorno determinado, como el entorno de producción. La dirección VIP sólo cambia si elimina la implementación de forma explícita o implícitamente se elimina la implementación por el proceso de actualización de implementación. Para conservar a la dirección VIP, no debe eliminar su implementación, y debe asegurarse de que Visual Studio no elimina automáticamente la implementación. 

Puede especificar la configuración de implementación en el **Asistente para publicación**, que admite varias opciones de implementación. Puede especificar una nueva implementación o una implementación de actualizaciones, que puede ser incremental o simultánea. Ambos tipos de implementación de actualización conservan a la dirección VIP. Para obtener definiciones de estos diferentes tipos de implementación, vea [asistente Publicar aplicación de Azure](vs-azure-tools-publish-azure-application-wizard.md). Además, puede controlar si se ha eliminado la implementación anterior de un servicio en la nube si se produce un error. Si no establece esta opción correctamente, la dirección VIP podría cambiar de forma inesperada.

## <a name="update-a-cloud-service-without-changing-its-vip"></a>Actualizar un servicio en la nube sin cambiar su VIP
1. Cree o abra un proyecto de servicio de nube de Azure en Visual Studio. 

2. En **el Explorador de soluciones**, haga clic en el proyecto. En el menú contextual, seleccione **publicar**.

    ![Menú Publicar](./media/vs-azure-tools-cloud-service-retain-a-constant-virtual-ip-address/solution-explorer-publish-menu.png)

3. En el **publicar aplicación de Azure** cuadro de diálogo, seleccione la suscripción de Azure a la que desea implementar. Inicio de sesión si es necesario y, a continuación, seleccione **siguiente**.

    ![Inicio de sesión de aplicación de Azure en la página de publicación](./media/vs-azure-tools-cloud-service-retain-a-constant-virtual-ip-address/azure-publish-signin.png)

4. En el **configuración común** , compruebe que el nombre de la nube de servicio en el que está implementando, el **entorno**, **configuración de compilación**y el **Configuración del servicio** son todos correctos.

    ![Publicar la pestaña Configuración común de aplicación de Azure](./media/vs-azure-tools-cloud-service-retain-a-constant-virtual-ip-address/azure-publish-common-settings.png)

5. En el **configuración avanzada** , compruebe que la **etiqueta de implementación** y **cuenta de almacenamiento** son correctos. Compruebe que la **eliminar implementación en caso de error** casilla de verificación está desactivada y compruebe que la **actualización de implementación** casilla está activada. Si desactiva la **eliminar implementación en caso de error** casilla de verificación, se asegura de que la dirección VIP no se pierda si se produce un error durante la implementación. Si selecciona el **actualización de implementación** casilla de verificación, se garantiza que no se elimina la implementación y la dirección VIP no se pierda cuando vuelva a publicar la aplicación. 

    ![Publicar la pestaña Configuración avanzada de aplicación de Azure](./media/vs-azure-tools-cloud-service-retain-a-constant-virtual-ip-address/azure-publish-advanced-settings.png)

6. Para especificar cómo desea que se actualicen los roles, seleccione **configuración** junto a **actualización de implementación**. Seleccione **actualización Incremental** o **actualización simultánea**y seleccione **Aceptar**. Elija **actualización Incremental** para actualizar cada instancia de la aplicación, una tras otra, para que la aplicación siempre esté disponible. Elija **actualización simultánea** para actualizar todas las instancias de la aplicación al mismo tiempo. La actualización simultánea es más rápida, pero el servicio no esté disponible durante el proceso de actualización. Cuando haya terminado, seleccione **siguiente**.

    ![Publicar la página Configuración de implementación de aplicación de Azure](./media/vs-azure-tools-cloud-service-retain-a-constant-virtual-ip-address/azure-publish-deployment-update-settings.png)

7. En el **publicar aplicación de Azure** cuadro de diálogo, seleccione **siguiente** hasta que el **resumen** se muestra la página. Compruebe la configuración y, a continuación, seleccione **publicar**.
   
    ![Publicar la página de resumen de la aplicación de Azure](./media/vs-azure-tools-cloud-service-retain-a-constant-virtual-ip-address/azure-publish-summary.png)

## <a name="next-steps"></a>Pasos siguientes
- [Uso de Visual Studio asistente Publicar aplicación de Azure](vs-azure-tools-publish-azure-application-wizard.md)

