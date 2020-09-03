---
title: Conservación de una dirección IP virtual constante para un servicio en la nube de Azure
description: Obtenga información para garantizar que no cambia la dirección IP virtual (VIP) de su servicio en la nube de Azure.
author: ghogen
manager: jillfra
assetId: 4a58e2c6-7a79-4051-8a2c-99182ff8b881
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: how-to
ms.date: 03/21/2017
ms.author: ghogen
ms.openlocfilehash: e7e7d9a6c1c417b3802ef1f94ac51fec14bf682a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "85280855"
---
# <a name="retain-a-constant-virtual-ip-address-for-an-azure-cloud-service"></a>Conservación de una dirección IP virtual constante para un servicio en la nube de Azure
Al actualizar un servicio en la nube que se hospeda en Azure, es posible que deba asegurarse de que no cambia la dirección IP virtual (VIP) del servicio. Muchos de los servicios de administración de dominio usan el Sistema de nombres de dominio (DNS) para registrar nombres de dominio. DNS solo funciona si la dirección VIP sigue siendo la misma. Puede usar el **Asistente para publicación** en Azure Tools para asegurarse de que la dirección VIP del servicio en la nube no cambia cuando la actualiza. Para más información sobre cómo usar la administración de dominios DNS para servicios en la nube, vea [Configuración de un nombre de dominio personalizado para un servicio en la nube de Azure](/azure/cloud-services/cloud-services-custom-domain-name-portal).

## <a name="publish-a-cloud-service-without-changing-its-vip"></a>Publicación de un servicio en la nube sin cambiar su VIP
La dirección VIP de un servicio en la nube se asigna al implementarla por primera vez en Azure en un entorno determinado, como el entorno de producción. La dirección VIP solo cambia si elimina la implementación de manera explícita o si se elimina implícitamente por el proceso de actualización de implementación. Para conservar la dirección VIP, no debe eliminar su implementación y debe asegurarse de que Visual Studio no elimina su implementación automáticamente.

Puede especificar la configuración de implementación en el **Asistente para publicación**, que admite varias opciones de implementación. Puede especificar una nueva implementación o una implementación de actualización, que puede ser incremental o simultánea. Ambos tipos de implementaciones de actualización conservan la dirección VIP. Para obtener definiciones de estos tipos diferentes de implementación, vea [Asistente Publicar aplicaciones de Azure](vs-azure-tools-publish-azure-application-wizard.md). Además, puede controlar si la implementación anterior de un servicio en la nube se elimina si se produce un error. Si no se establece correctamente esta opción, la dirección VIP podría cambiar de forma inesperada.

## <a name="update-a-cloud-service-without-changing-its-vip"></a>Actualización de un servicio en la nube sin cambiar su VIP
1. Cree o abra un proyecto de servicio en la nube de Azure en Visual Studio.

2. En el **Explorador de soluciones**, haga clic con el botón derecho en el proyecto. En el menú contextual, seleccione **Publicar**.

    ![Publish menu](./media/vs-azure-tools-cloud-service-retain-a-constant-virtual-ip-address/solution-explorer-publish-menu.png)

3. En el cuadro de diálogo **Publicar aplicación de Azure**, seleccione la suscripción de Azure en la que desea realizar la implementación. Inicie sesión en si es necesario y seleccione **Siguiente**.

    ![Página de inicio de sesión de Publicar aplicación de Azure](./media/vs-azure-tools-cloud-service-retain-a-constant-virtual-ip-address/azure-publish-signin.png)

4. En la pestaña **configuración común** , compruebe que el nombre del servicio en la nube en el que está implementando, el **entorno**, la **configuración de compilación**y la configuración del **servicio** son todos correctos.

    ![Pestaña Configuración común de Publicar aplicación de Azure](./media/vs-azure-tools-cloud-service-retain-a-constant-virtual-ip-address/azure-publish-common-settings.png)

5. En la pestaña **Configuración avanzada**, compruebe que la **etiqueta de implementación** y la **cuenta de almacenamiento** son correctas. Compruebe que la casilla **Eliminar implementación en caso de error** está desactivada y compruebe que la casilla **Actualización de implementación**. Al desactivar la casilla **eliminar implementación en caso de error** , se asegura de que no se pierda la dirección VIP si se produce un error durante la implementación. Seleccione la casilla **Actualización de implementación** para asegurarse de que no se elimine la implementación y de que no se pierda la dirección VIP al volver a publicar la aplicación.

    ![Pestaña Configuración avanzada de Publicar aplicación de Azure](./media/vs-azure-tools-cloud-service-retain-a-constant-virtual-ip-address/azure-publish-advanced-settings.png)

6. Para especificar con más detalle cómo desea que se actualicen los roles, seleccione **Configuración** junto a **Actualización de implementación**. Seleccione **Actualización incremental** o **Actualización simultánea** y seleccione **Aceptar**. Elija **Actualización incremental** para actualizar cada instancia de la aplicación, una tras otra, para que la aplicación siempre esté disponible. Elija **Actualización simultánea** para actualizar todas las instancias de la aplicación al mismo tiempo. La actualización simultánea es más rápida, pero es posible que el servicio no esté disponible durante el proceso de actualización. Cuando haya terminado, seleccione **Siguiente**.

    ![Página Configuración de implementación de Publicar aplicación de Azure](./media/vs-azure-tools-cloud-service-retain-a-constant-virtual-ip-address/azure-publish-deployment-update-settings.png)

7. En el cuadro de diálogo **Publicar aplicación de Azure**, seleccione **Siguiente** hasta que muestre la página **Resumen**. Compruebe la configuración y, luego, seleccione **Publicar**.

    ![Página de resumen de Publicar aplicación de Azure](./media/vs-azure-tools-cloud-service-retain-a-constant-virtual-ip-address/azure-publish-summary.png)

## <a name="next-steps"></a>Pasos siguientes
- [Uso del Asistente Publicar aplicación de Azure de Visual Studio](vs-azure-tools-publish-azure-application-wizard.md)
