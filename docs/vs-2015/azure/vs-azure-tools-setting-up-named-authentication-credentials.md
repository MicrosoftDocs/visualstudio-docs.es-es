---
title: Configurar las credenciales de autenticación con nombre | Microsoft Docs
description: Obtenga información sobre cómo proporcionar credenciales que Visual Studio puede usar para autenticar solicitudes en Azure, por lo que puede publicar una aplicación en Azure desde Visual Studio o supervisar un servicio en la nube existente.
author: ghogen
manager: douge
assetId: 61570907-42a1-40e8-bcd6-952b21a55786
ms.prod: visual-studio-dev14
ms.technology: vs-azure
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 11/11/2017
ms.author: ghogen
ms.openlocfilehash: 6f41ea2072ef5791735fac61205f68151d5a9f7e
ms.sourcegitcommit: e481d0055c0724d20003509000fd5f72fe9d1340
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/05/2018
ms.locfileid: "51002915"
---
# <a name="set-up-named-authentication-credentials"></a>Configuración de credenciales de autenticación con nombre

Para publicar una aplicación en Azure o supervisar un servicio en la nube existente, Visual Studio requiere credenciales para autenticar solicitudes en Azure, es decir, el identificador de suscripción de Azure y un certificado X.509 v3 válido con una clave de al menos 2048 bits. Puede proporcionar estas credenciales a través de cualquiera de los métodos siguientes:

- En Visual Studio, seleccione **Vista > Explorador de servidores**, haga clic en el **Azure** nodo, seleccione **conectar a la suscripción de Microsoft Azure**e inicie sesión.
- Crear un archivo de suscripción (`.publishsettings`), que contiene una clave pública del certificado. El archivo de suscripción puede contener credenciales para más de una suscripción, como se describe en este artículo.

Nota: estas credenciales son diferentes de las credenciales usadas para autenticar las solicitudes a los servicios de almacenamiento de Azure.

## <a name="create-a-subscription-file"></a>Crear un archivo de suscripción

En el Explorador de servidores, haga clic en el **Azure** nodo y seleccione **administrar y filtrar suscripciones**. A continuación, seleccione el **certificados** pestaña y, a continuación, realice una de las siguientes acciones:

- Seleccione **importación** para abrir el **Importar suscripciones de Microsoft Azure** cuadro de diálogo. Seleccione el **Descargar archivo de suscripción** vincular y, en el explorador, guarde el archivo descargado en una ubicación temporal. En el cuadro de diálogo, vaya a la ubicación de descarga y, a continuación, importarlo para usarlo en la autenticación.
- Elija una suscripción activa y seleccione **editar**, que abre un cuadro de diálogo en el que edita una suscripción existente para usarlo en la autenticación.
- Seleccione **New** para abrir el **nueva suscripción** diálogo cuadro y proporcione los detalles necesarios. Para cargar el certificado a la nube de servicio se indican en el cuadro de diálogo, inicie sesión en Azure portal, vaya a su servicio en la nube, seleccione **configuración > certificados de administración**, seleccione **cargar**, a continuación, Especifique la ruta de acceso a la `.cer` archivo.

Si desea crear un certificado usted mismo, puede hacer referencia a las instrucciones de [crear y cargar un certificado de administración para Azure](https://msdn.microsoft.com/library/windowsazure/gg551722.aspx) y, a continuación, cargar manualmente el certificado en el [portal Azure](https://portal.azure.com/).

## <a name="next-steps"></a>Pasos siguientes

- [Información general de las aplicaciones Web](https://docs.microsoft.com/azure/app-service/)
- [Implementar la aplicación en Azure App Service](https://docs.microsoft.com/azure/app-service/app-service-deploy-local-git) 
- [Implementación de WebJobs mediante Visual Studio](https://docs.microsoft.com/azure/app-service/websites-dotnet-deploy-webjobs)
- [Crear e implementar un servicio en la nube](https://docs.microsoft.com/azure/cloud-services/cloud-services-how-to-create-deploy-portal)