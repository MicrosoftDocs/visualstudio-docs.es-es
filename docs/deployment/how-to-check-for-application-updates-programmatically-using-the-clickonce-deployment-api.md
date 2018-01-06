---
title: "Cómo: buscar actualizaciones de aplicaciones mediante programación con la API de implementación de ClickOnce | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-deployment
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, updates
- application updates
ms.assetid: 1a886310-67c8-44e5-a382-c2f0454f887d
caps.latest.revision: "9"
author: stevehoag
ms.author: shoag
manager: wpickett
ms.workload: multiple
ms.openlocfilehash: 02e6a4c0b69bf9e9d6170175b4324ccb226854e2
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-check-for-application-updates-programmatically-using-the-clickonce-deployment-api"></a>Como: Buscar actualizaciones de aplicaciones mediante programación utilizando la API de implementación de ClickOnce
ClickOnce proporciona dos maneras de actualizar una aplicación una vez que se implementa. En el primer método, puede configurar la implementación de ClickOnce para buscar automáticamente actualizaciones a determinados intervalos. En el segundo método, puede escribir código que usa el <xref:System.Deployment.Application.ApplicationDeployment> clase para buscar actualizaciones en función de un evento, como una solicitud de usuario.  
  
 Los procedimientos siguientes muestran código para realizar una actualización mediante programación y también describen cómo configurar la implementación de ClickOnce para habilitar las comprobaciones de actualización mediante programación.  
  
 Para actualizar una aplicación ClickOnce mediante programación, debe especificar una ubicación para las actualizaciones. Esto se conoce a veces como un proveedor de implementación. Para obtener más información acerca de cómo establecer esta propiedad, vea [elegir una estrategia de actualización de ClickOnce](../deployment/choosing-a-clickonce-update-strategy.md).  
  
> [!NOTE]
>  También puede utilizar la técnica descrita a continuación para implementar su aplicación desde una ubicación pero actualizarla desde otra. Para obtener más información, consulte [Cómo: especificar una ubicación alternativa para las actualizaciones de la implementación](../deployment/how-to-specify-an-alternate-location-for-deployment-updates.md).  
  
### <a name="to-check-for-updates-programmatically"></a>Para buscar actualizaciones mediante programación  
  
1.  Cree una nueva aplicación de formularios Windows Forms mediante sus herramientas de línea de comandos o visuales preferidas.  
  
2.  Cree cualquier botón, el elemento de menú y otros elementos de interfaz de usuario quiere que los usuarios que seleccione esta opción para comprobar si hay actualizaciones. Desde el controlador de eventos de ese elemento, llame al método siguiente para buscar e instalar actualizaciones.  
  
     [!code-csharp[ClickOnceAPI#6](../deployment/codesnippet/CSharp/how-to-check-for-application-updates-programmatically-using-the-clickonce-deployment-api_1.cs)]
     [!code-cpp[ClickOnceAPI#6](../deployment/codesnippet/CPP/how-to-check-for-application-updates-programmatically-using-the-clickonce-deployment-api_1.cpp)]
     [!code-vb[ClickOnceAPI#6](../deployment/codesnippet/VisualBasic/how-to-check-for-application-updates-programmatically-using-the-clickonce-deployment-api_1.vb)]  
  
3.  Compile la aplicación.  
  
### <a name="using-mageexe-to-deploy-an-application-that-checks-for-updates-programmatically"></a>Utilizar Mage.exe para implementar una aplicación que comprueba si hay actualizaciones mediante programación  
  
-   Siga las instrucciones para implementar su aplicación mediante Mage.exe como se explica en [Tutorial: implementar manualmente una aplicación ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md). Al llamar a Mage.exe para generar el manifiesto de implementación, asegúrese de usar el modificador de línea de comandos `providerUrl`así como para especificar la dirección URL donde ClickOnce debe comprobar las actualizaciones. Si la aplicación se actualizará desde [http://www.adatum.com/MyApp](http://www.adatum.com/MyApp), por ejemplo, la llamada para generar el manifiesto de implementación podría ser similar al siguiente:  
  
    ```  
    mage -New Deployment -ToFile WindowsFormsApp1.application -Name "My App 1.0" -Version 1.0.0.0 -AppManifest 1.0.0.0\MyApp.manifest -providerUrl http://www.adatum.com/MyApp/MyApp.application  
    ```  
  
### <a name="using-mageuiexe-to-deploy-an-application-that-checks-for-updates-programmatically"></a>Utilizar MageUI.exe para implementar una aplicación que comprueba si hay actualizaciones mediante programación  
  
-   Siga las instrucciones para implementar su aplicación mediante Mage.exe como se explica en [Tutorial: implementar manualmente una aplicación ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md). En el **opciones de implementación** pestaña, establezca el **iniciar ubicación** campo al manifiesto de aplicación ClickOnce debe comprobar las actualizaciones. En el **opciones de actualización** ficha, desactive la **esta aplicación debe buscar actualizaciones** casilla de verificación.  
  
## <a name="net-framework-security"></a>Seguridad de .NET Framework  
 La aplicación debe tener permisos de plena confianza para usar la actualización mediante programación.  
  
## <a name="see-also"></a>Vea también  
 [Cómo: especificar una ubicación alternativa para las actualizaciones de implementación](../deployment/how-to-specify-an-alternate-location-for-deployment-updates.md)   
 [Elegir una estrategia de actualización de ClickOnce](../deployment/choosing-a-clickonce-update-strategy.md)   
 [Publicar aplicaciones ClickOnce](../deployment/publishing-clickonce-applications.md)