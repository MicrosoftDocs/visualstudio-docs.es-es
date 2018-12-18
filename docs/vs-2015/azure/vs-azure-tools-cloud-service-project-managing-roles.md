---
title: Administración de roles en Azure cloud services con Visual Studio | Microsoft Docs
description: Obtenga información sobre cómo agregar y quitar roles en Azure cloud services con Visual Studio.
author: ghogen
manager: douge
assetId: 5ec9ae2e-8579-4e5d-999e-8ae05b629bd1
ms.prod: visual-studio-dev14
ms.technology: vs-azure
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 03/21/2017
ms.author: ghogen
ms.openlocfilehash: 35221cbf98f26a71e2b4adf0a7178342616ff7c0
ms.sourcegitcommit: e481d0055c0724d20003509000fd5f72fe9d1340
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/05/2018
ms.locfileid: "51002886"
---
# <a name="managing-roles-in-azure-cloud-services-with-visual-studio"></a>Administración de roles en Azure cloud services con Visual Studio
Después de haber creado el servicio de nube de Azure, puede agregarle nuevos roles o quitarle roles existentes. También puede importar un proyecto existente y convertirlo a un rol. Por ejemplo, puede importar una aplicación web ASP.NET y designarla como rol web.

## <a name="adding-a-role-to-an-azure-cloud-service"></a>Agregar un rol a un servicio de nube de Azure
Los siguientes pasos le guiarán a través de agregar un rol web o de trabajo a un proyecto de servicio de nube de Azure en Visual Studio.

1. Cree o abra un proyecto de servicio de nube de Azure en Visual Studio.

1. En **el Explorador de soluciones**, expanda el nodo del proyecto

1. Haga clic en el **Roles** nodo para mostrar el menú contextual. En el menú contextual, seleccione **agregar**, a continuación, seleccione un rol web existente o un rol de trabajo de la solución actual o crear un proyecto de rol web o de trabajo. También puede seleccionar un proyecto adecuado, por ejemplo, un proyecto de aplicación web ASP.NET y asociarlo a un proyecto de rol.

    ![Opciones de menú para agregar un rol a un proyecto de servicio de nube de Azure](./media/vs-azure-tools-cloud-service-project-managing-roles/add-role.png)

## <a name="removing-a-role-from-an-azure-cloud-service"></a>Quitar una función de un servicio de nube de Azure
Los siguientes pasos le guiarán a través de quitar un rol web o de trabajo de un proyecto de servicio de nube de Azure en Visual Studio.

1. Cree o abra un proyecto de servicio de nube de Azure en Visual Studio.

1. En **el Explorador de soluciones**, expanda el nodo del proyecto

1. Expanda el **Roles** nodo.

1. Haga clic en el nodo que desea quitar y, en el menú contextual, seleccione **quitar**. 

    ![Opciones de menú para agregar un rol a un servicio de nube de Azure](./media/vs-azure-tools-cloud-service-project-managing-roles/remove-role.png)

## <a name="readding-a-role-to-an-azure-cloud-service-project"></a>Intente volver a agregar un rol a un proyecto de servicio de nube de Azure
Si quitar una función de su proyecto de servicio en la nube pero posteriormente decide agregar el rol de nuevo al proyecto, solo la declaración de función y los atributos básicos, como los puntos de conexión e información de diagnóstico, se agregan. No hay recursos adicionales o las referencias se agregan a la `ServiceDefinition.csdef` archivo o a la `ServiceConfiguration.cscfg` archivo. Si desea agregar esta información, deberá agregarlo manualmente a estos archivos.

Por ejemplo, puede quitar un rol de servicio web y más adelante decide volver a agregar este rol a la solución. Si lo hace, se produce un error. Para evitar este error, tiene que agregar el `<LocalResources>` elemento mostrado en el siguiente código XML en el `ServiceDefinition.csdef` archivo. Use el nombre del rol de servicio web que agregó al proyecto como parte del nombre del atributo para el **<LocalStorage>** elemento. En este ejemplo, el nombre del rol de servicio web es **WCFServiceWebRole1**.

    <WebRole name="WCFServiceWebRole1">
        <Sites>
          <Site name="Web">
            <Bindings>
              <Binding name="Endpoint1" endpointName="Endpoint1" />
            </Bindings>
          </Site>
        </Sites>
        <Endpoints>
          <InputEndpoint name="Endpoint1" protocol="http" port="80" />
        </Endpoints>
        <Imports>
          <Import moduleName="Diagnostics" />
        </Imports>
       <LocalResources>
          <LocalStorage name="WCFServiceWebRole1.svclog" sizeInMB="1000" cleanOnRoleRecycle="false" />
       </LocalResources>
    </WebRole>

## <a name="next-steps"></a>Pasos siguientes
- [Configurar los Roles para un servicio de nube de Azure con Visual Studio](vs-azure-tools-configure-roles-for-cloud-service.md)
