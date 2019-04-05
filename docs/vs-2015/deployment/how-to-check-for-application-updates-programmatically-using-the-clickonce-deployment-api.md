---
title: Filtrar Buscar actualizaciones de aplicaciones mediante programación con la API de implementación ClickOnce | Documentos de Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, updates
- application updates
ms.assetid: 1a886310-67c8-44e5-a382-c2f0454f887d
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: ac7a5665b287f51e59d99d21802acc252a55a99a
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2019
ms.locfileid: "58998312"
---
# <a name="how-to-check-for-application-updates-programmatically-using-the-clickonce-deployment-api"></a>Filtrar Comprobación de actualizaciones de aplicaciones mediante programación utilizando la API de implementación de ClickOnce
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

ClickOnce ofrece dos maneras de actualizar una aplicación una vez que se implementa. En el primer método, puede configurar la implementación de ClickOnce para buscar automáticamente actualizaciones en determinados intervalos. En el segundo método, puede escribir código que usa el <xref:System.Deployment.Application.ApplicationDeployment> clase para comprobar si hay actualizaciones en función de un evento, como una solicitud de usuario.  
  
 Los procedimientos siguientes muestran código para realizar una actualización mediante programación y también describen cómo configurar la implementación de ClickOnce para habilitar las comprobaciones de actualización mediante programación.  
  
 Para actualizar una aplicación ClickOnce mediante programación, debe especificar una ubicación para las actualizaciones. Esto se conoce a veces como un proveedor de implementación. Para obtener más información sobre cómo establecer esta propiedad, vea [elegir una estrategia de actualización de ClickOnce](../deployment/choosing-a-clickonce-update-strategy.md).  
  
> [!NOTE]
>  También puede usar la técnica descrita a continuación para implementar la aplicación desde una ubicación pero actualizarla desde otra. Para obtener más información, vea [Cómo: Especificar una ubicación alternativa para las actualizaciones de implementación](../deployment/how-to-specify-an-alternate-location-for-deployment-updates.md).  
  
### <a name="to-check-for-updates-programmatically"></a>Para comprobar las actualizaciones mediante programación  
  
1.  Cree una nueva aplicación de Windows Forms mediante sus herramientas preferidas de la línea de comandos o visuales.  
  
2.  Cree cualquier botón, el elemento de menú u otro elemento de interfaz de usuario desea que los usuarios para que se seleccione esta opción para comprobar si hay actualizaciones. Desde el controlador de eventos de ese elemento, llame al método siguiente para buscar e instalar las actualizaciones.  
  
     [!code-cpp[ClickOnceAPI#6](../snippets/cpp/VS_Snippets_Winforms/ClickOnceAPI/cpp/form1.cpp#6)]
     [!code-csharp[ClickOnceAPI#6](../snippets/csharp/VS_Snippets_Winforms/ClickOnceAPI/CS/Form1.cs#6)]
     [!code-vb[ClickOnceAPI#6](../snippets/visualbasic/VS_Snippets_Winforms/ClickOnceAPI/VB/Form1.vb#6)]  
  
3.  Compile la aplicación.  
  
### <a name="using-mageexe-to-deploy-an-application-that-checks-for-updates-programmatically"></a>Utilizar Mage.exe para implementar una aplicación que busca actualizaciones mediante programación  
  
-   Siga las instrucciones para implementar su aplicación mediante Mage.exe como se explica en [Tutorial: Implementar manualmente una aplicación ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md). Al llamar a Mage.exe para generar el manifiesto de implementación, asegúrese de usar el modificador de línea de comandos `providerUrl`así como para especificar la dirección URL donde ClickOnce debe comprobar las actualizaciones. Si la aplicación se actualizará desde [ http://www.adatum.com/MyApp ](http://www.adatum.com/MyApp), por ejemplo, la llamada para generar el manifiesto de implementación podría ser similar al siguiente:  
  
    ```  
    mage -New Deployment -ToFile WindowsFormsApp1.application -Name "My App 1.0" -Version 1.0.0.0 -AppManifest 1.0.0.0\MyApp.manifest -providerUrl http://www.adatum.com/MyApp/MyApp.application  
    ```  
  
### <a name="using-mageuiexe-to-deploy-an-application-that-checks-for-updates-programmatically"></a>Mediante MageUI.exe para implementar una aplicación que busca actualizaciones mediante programación  
  
-   Siga las instrucciones para implementar su aplicación mediante Mage.exe como se explica en [Tutorial: Implementar manualmente una aplicación ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md). En el **opciones de implementación** pestaña, establezca el **iniciar ubicación** campo al manifiesto de aplicación ClickOnce debe comprobar las actualizaciones. En el **opciones de actualización** ficha, desactive la **esta aplicación debe buscar actualizaciones** casilla de verificación.  
  
## <a name="net-framework-security"></a>Seguridad de .NET Framework  
 La aplicación debe tener permisos de plena confianza para utilizar la actualización mediante programación.  
  
## <a name="see-also"></a>Vea también  
 [Cómo: Especificar una ubicación alternativa para las actualizaciones de implementación](../deployment/how-to-specify-an-alternate-location-for-deployment-updates.md)   
 [Elegir una estrategia de actualización de ClickOnce](../deployment/choosing-a-clickonce-update-strategy.md)   
 [Publicar aplicaciones ClickOnce](../deployment/publishing-clickonce-applications.md)
