---
title: Configuración de credenciales de autenticación con nombre | Microsoft Docs
description: Aprenda a proporcionar credenciales que Visual Studio pueda usar para autenticar solicitudes en Azure para publicar una aplicación en Azure desde Visual Studio o para supervisar un servicio en la nube existente.
author: ghogen
manager: jillfra
assetId: 61570907-42a1-40e8-bcd6-952b21a55786
ms.prod: visual-studio-dev14
ms.technology: vs-azure
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 11/11/2017
ms.author: ghogen
ms.openlocfilehash: 27837390306ad29da55c7c5262ecd8fa6bcf75b3
ms.sourcegitcommit: 939407118f978162a590379997cb33076c57a707
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/13/2020
ms.locfileid: "75917365"
---
# <a name="set-up-named-authentication-credentials"></a>Configuración de credenciales de autenticación con nombre

Para publicar una aplicación en Azure o supervisar un servicio de nube existente, Visual Studio requiere credenciales para autenticar solicitudes en Azure, es decir, el identificador de la suscripción de Azure y un certificado X.509 v3 válido con una clave de al menos 2048 bits. Puede proporcionar estas credenciales a través de alguno de los siguientes métodos:

- En Visual Studio, seleccione **Ver > Explorador de servidores**, haga clic con el botón derecho en el nodo **Azure**, seleccione **Conectar a la suscripción de Microsoft Azure** e inicie sesión.
- Cree un archivo de suscripción (`.publishsettings`), que contiene una clave pública para el certificado. El archivo de suscripción puede contener credenciales para más de una suscripción, como se describe en este artículo.

Nota: Estas credenciales son distintas de las que se utilizan para autenticar las solicitudes en los servicios de almacenamiento de Azure.

## <a name="create-a-subscription-file"></a>Creación de un archivo de suscripción

En el Explorador de servidores, haga clic con el botón derecho en el nodo **Azure** y seleccione **Administrar y filtrar suscripciones**. Seleccione la pestaña **Certificados** y después realice alguna de las siguientes acciones:

- Seleccione **Importar** para abrir el cuadro de diálogo **Importar suscripciones de Microsoft Azure**. Seleccione el vínculo **Descargar archivo de suscripción** y, en el explorador, guarde el archivo descargado en una ubicación temporal. Vuelva al cuadro de diálogo, vaya a la ubicación de descarga y después importe el archivo para utilizarlo en la autenticación.
- Elija una suscripción activa y seleccione **Editar**, para abrir un cuadro de diálogo en el que va a editar una suscripción existente para su uso en la autenticación.
- Seleccione **Nuevo** para abrir el cuadro de diálogo **Nueva suscripción** y proporcione los detalles necesarios. Para cargar el certificado en el servicio en la nube indicado en el cuadro de diálogo, inicie sesión en Azure Portal, vaya al servicio en la nube, seleccione **Configuración > Certificados de administración** y **Cargar** y, después, especifique la ruta de acceso al archivo `.cer`.

Si desea crear un certificado por sí mismo, puede consultar las instrucciones de [Creación y carga de un certificado de administración para Azure](https://msdn.microsoft.com/library/windowsazure/gg551722.aspx) y después cargar manualmente el certificado en [Azure Portal](https://portal.azure.com/).

## <a name="next-steps"></a>Pasos siguientes

- [Introducción general sobre Web Apps](/azure/app-service/)
- [Documentación de implementación de Azure App Service](/azure/app-service/app-service-deploy-local-git) 
- [Implementar trabajos web con Visual Studio](/azure/app-service/websites-dotnet-deploy-webjobs)
- [Crear e implementar un servicio en la nube](/azure/cloud-services/cloud-services-how-to-create-deploy-portal)