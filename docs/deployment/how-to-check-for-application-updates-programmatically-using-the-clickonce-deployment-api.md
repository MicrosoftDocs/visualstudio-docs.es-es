---
title: Actualizaciones automáticas de aplicaciones mediante la API de implementación de ClickOnce
ms.date: 11/04/2016
ms.topic: conceptual
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9300fbf8b348b1016d36d414d17a66c45f6494b9
ms.sourcegitcommit: 7b60e81414a82c6d34f6de1a1f56115c9cd26943
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2020
ms.locfileid: "81444622"
---
# <a name="how-to-check-for-application-updates-programmatically-using-the-clickonce-deployment-api"></a>Como: buscar actualizaciones de aplicaciones mediante programación con la API de implementación ClickOnce
ClickOnce proporciona dos maneras de actualizar una aplicación una vez que se implementa. En el primer método, puede configurar la implementación ClickOnce para comprobar automáticamente si hay actualizaciones en determinados intervalos. En el segundo método, puede escribir <xref:System.Deployment.Application.ApplicationDeployment> código que use la clase para buscar actualizaciones basadas en un evento, como una solicitud de usuario.

 Los procedimientos siguientes muestran código para realizar una actualización mediante programación y también describen cómo configurar la implementación ClickOnce para habilitar las comprobaciones de actualización mediante programación.

 Para actualizar una aplicación ClickOnce mediante programación, debe especificar una ubicación para las actualizaciones. Esto se conoce a veces como un proveedor de implementación. Para obtener más información sobre cómo establecer esta propiedad, vea Elegir una estrategia de [actualización ClickOnce](../deployment/choosing-a-clickonce-update-strategy.md).

> [!NOTE]
> También puede usar la técnica que se describe a continuación para implementar la aplicación desde una ubicación, pero actualizarla desde otra. Para obtener más información, consulte [Cómo: especificar una ubicación alternativa para las actualizaciones de implementación.](../deployment/how-to-specify-an-alternate-location-for-deployment-updates.md)

### <a name="to-check-for-updates-programmatically"></a>Para buscar actualizaciones mediante programación

1. Cree una nueva aplicación de formularios Windows Forms con la línea de comandos o las herramientas visuales preferidas.

2. Cree cualquier botón, elemento de menú u otro elemento de interfaz de usuario que desee que los usuarios seleccionen para buscar actualizaciones. Desde el controlador de eventos de ese elemento, llame al método siguiente para buscar e instalar actualizaciones.

     [!code-csharp[ClickOnceAPI#6](../deployment/codesnippet/CSharp/how-to-check-for-application-updates-programmatically-using-the-clickonce-deployment-api_1.cs)]
     [!code-cpp[ClickOnceAPI#6](../deployment/codesnippet/CPP/how-to-check-for-application-updates-programmatically-using-the-clickonce-deployment-api_1.cpp)]
     [!code-vb[ClickOnceAPI#6](../deployment/codesnippet/VisualBasic/how-to-check-for-application-updates-programmatically-using-the-clickonce-deployment-api_1.vb)]

3. Compile la aplicación.

### <a name="use-mageexe-to-deploy-an-application-that-checks-for-updates-programmatically"></a>Use Mage.exe para implementar una aplicación que busque actualizaciones mediante programación

- Siga las instrucciones para implementar la aplicación mediante Mage.exe como se explica en [Tutorial: Implementar manualmente una aplicación ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md). Al llamar a Mage.exe para generar el manifiesto de `providerUrl`implementación, asegúrese de usar el modificador de línea de comandos y especificar la dirección URL donde ClickOnce debe buscar actualizaciones. Si la aplicación `http://www.adatum.com/MyApp`se actualizará desde , por ejemplo, la llamada para generar el manifiesto de implementación podría tener este aspecto:

    ```cmd
    mage -New Deployment -ToFile WindowsFormsApp1.application -Name "My App 1.0" -Version 1.0.0.0 -AppManifest 1.0.0.0\MyApp.manifest -providerUrl http://www.adatum.com/MyApp/MyApp.application
    ```

### <a name="using-mageuiexe-to-deploy-an-application-that-checks-for-updates-programmatically"></a>Uso de MageUI.exe para implementar una aplicación que comprueba si hay actualizaciones mediante programación

- Siga las instrucciones para implementar la aplicación mediante Mage.exe como se explica en [Tutorial: Implementar manualmente una aplicación ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md). En la pestaña Opciones de **implementación,** establezca el campo Ubicación de **inicio** en el manifiesto de aplicación ClickOnce debe buscar actualizaciones. En la pestaña Opciones de **actualización,** desactive la casilla **Esta aplicación debe comprobar si hay actualizaciones.**

## <a name="net-framework-security"></a>Seguridad de .NET Framework
 La aplicación debe tener permisos de plena confianza para usar la actualización mediante programación.

## <a name="see-also"></a>Consulte también
- [Cómo: Especificar una ubicación alternativa para las actualizaciones de la implementación](../deployment/how-to-specify-an-alternate-location-for-deployment-updates.md)
- [Selección de una estrategia de actualización de ClickOnce](../deployment/choosing-a-clickonce-update-strategy.md)
- [Publicar aplicaciones ClickOnce](../deployment/publishing-clickonce-applications.md)