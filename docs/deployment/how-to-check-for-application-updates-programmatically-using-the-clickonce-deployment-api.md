---
title: Actualizaciones automáticas de aplicaciones mediante la API de implementación de ClickOnce
description: Obtenga información sobre cómo escribir código en ClickOnce que use la clase ApplicationDeployment para buscar actualizaciones en función de un evento, como una solicitud de usuario.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, updates
- application updates
ms.assetid: 1a886310-67c8-44e5-a382-c2f0454f887d
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 6e7168b78303f93ccf89fad324992dd580481ac2
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99888451"
---
# <a name="how-to-check-for-application-updates-programmatically-using-the-clickonce-deployment-api"></a>Como: buscar actualizaciones de aplicaciones mediante programación con la API de implementación ClickOnce
ClickOnce proporciona dos maneras de actualizar una aplicación una vez que se implementa. En el primer método, puede configurar la implementación ClickOnce para comprobar automáticamente si hay actualizaciones en determinados intervalos. En el segundo método, puede escribir código que use la <xref:System.Deployment.Application.ApplicationDeployment> clase para buscar actualizaciones en función de un evento, como una solicitud de usuario.

 Los procedimientos siguientes muestran código para realizar una actualización mediante programación y también describen cómo configurar la implementación ClickOnce para habilitar las comprobaciones de actualizaciones mediante programación.

 Para actualizar una aplicación ClickOnce mediante programación, debe especificar una ubicación para las actualizaciones. A veces, esto se conoce como proveedor de implementación. Para obtener más información sobre cómo establecer esta propiedad, vea [elegir una estrategia de actualización de ClickOnce](../deployment/choosing-a-clickonce-update-strategy.md).

> [!NOTE]
> También puede usar la técnica que se describe a continuación para implementar la aplicación desde una ubicación, pero actualizarla desde otra. Para obtener más información, consulte [Cómo: especificar una ubicación alternativa para las actualizaciones de implementación](../deployment/how-to-specify-an-alternate-location-for-deployment-updates.md).

### <a name="to-check-for-updates-programmatically"></a>Para buscar actualizaciones mediante programación

1. Cree una nueva aplicación de Windows Forms con su línea de comandos o herramientas visuales preferidas.

2. Cree el botón, el elemento de menú u otro elemento de la interfaz de usuario que desee que los usuarios seleccionen para buscar actualizaciones. En el controlador de eventos de ese elemento, llame al método siguiente para buscar e instalar actualizaciones.

     [!code-csharp[ClickOnceAPI#6](../deployment/codesnippet/CSharp/how-to-check-for-application-updates-programmatically-using-the-clickonce-deployment-api_1.cs)]
     [!code-cpp[ClickOnceAPI#6](../deployment/codesnippet/CPP/how-to-check-for-application-updates-programmatically-using-the-clickonce-deployment-api_1.cpp)]
     [!code-vb[ClickOnceAPI#6](../deployment/codesnippet/VisualBasic/how-to-check-for-application-updates-programmatically-using-the-clickonce-deployment-api_1.vb)]

3. Compile la aplicación.

### <a name="use-mageexe-to-deploy-an-application-that-checks-for-updates-programmatically"></a>Usar Mage.exe para implementar una aplicación que compruebe las actualizaciones mediante programación

- Siga las instrucciones para implementar la aplicación mediante Mage.exe como se explica en [Tutorial: implementar manualmente una aplicación ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md). Al llamar a Mage.exe para generar el manifiesto de implementación, asegúrese de usar el modificador de la línea de comandos `providerUrl` y para especificar la dirección URL donde ClickOnce debe comprobar si hay actualizaciones. Si la aplicación va a actualizar desde `http://www.adatum.com/MyApp` , por ejemplo, la llamada para generar el manifiesto de implementación podría tener el siguiente aspecto:

    ```cmd
    mage -New Deployment -ToFile WindowsFormsApp1.application -Name "My App 1.0" -Version 1.0.0.0 -AppManifest 1.0.0.0\MyApp.manifest -providerUrl http://www.adatum.com/MyApp/MyApp.application
    ```

### <a name="using-mageuiexe-to-deploy-an-application-that-checks-for-updates-programmatically"></a>Usar MageUI.exe para implementar una aplicación que compruebe las actualizaciones mediante programación

- Siga las instrucciones para implementar la aplicación mediante Mage.exe como se explica en [Tutorial: implementar manualmente una aplicación ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md). En la pestaña **Opciones de implementación** , establezca el campo Ubicación de **Inicio** en el manifiesto de aplicación ClickOnce debe comprobar si hay actualizaciones. En la pestaña **Opciones de actualización** , desactive la casilla **esta aplicación debe buscar actualizaciones** .

## <a name="net-framework-security"></a>Seguridad de .NET Framework
 La aplicación debe tener permisos de plena confianza para usar la actualización mediante programación.

## <a name="see-also"></a>Vea también
- [Cómo: especificar una ubicación alternativa para las actualizaciones de implementación](../deployment/how-to-specify-an-alternate-location-for-deployment-updates.md)
- [Selección de una estrategia de actualización de ClickOnce](../deployment/choosing-a-clickonce-update-strategy.md)
- [Publicación de aplicaciones ClickOnce](../deployment/publishing-clickonce-applications.md)