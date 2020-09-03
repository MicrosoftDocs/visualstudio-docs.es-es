---
title: 'Cómo: buscar actualizaciones de aplicaciones mediante programación con la API de implementación de ClickOnce | Microsoft Docs'
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
ms.openlocfilehash: 5250e719cce945bdcce90a9d49d2ed8c27555612
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "81444989"
---
# <a name="how-to-check-for-application-updates-programmatically-using-the-clickonce-deployment-api"></a>Como: Buscar actualizaciones de aplicaciones mediante programación utilizando la API de implementación de ClickOnce
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

ClickOnce proporciona dos maneras de actualizar una aplicación una vez que se implementa. En el primer método, puede configurar la implementación ClickOnce para comprobar automáticamente si hay actualizaciones en determinados intervalos. En el segundo método, puede escribir código que use la <xref:System.Deployment.Application.ApplicationDeployment> clase para buscar actualizaciones en función de un evento, como una solicitud de usuario.  
  
 Los procedimientos siguientes muestran código para realizar una actualización mediante programación y también describen cómo configurar la implementación ClickOnce para habilitar las comprobaciones de actualizaciones mediante programación.  
  
 Para actualizar una aplicación ClickOnce mediante programación, debe especificar una ubicación para las actualizaciones. A veces, esto se conoce como proveedor de implementación. Para obtener más información sobre cómo establecer esta propiedad, vea [elegir una estrategia de actualización de ClickOnce](../deployment/choosing-a-clickonce-update-strategy.md).  
  
> [!NOTE]
> También puede usar la técnica que se describe a continuación para implementar la aplicación desde una ubicación, pero actualizarla desde otra. Para obtener más información, consulte [Cómo: especificar una ubicación alternativa para las actualizaciones de implementación](../deployment/how-to-specify-an-alternate-location-for-deployment-updates.md).  
  
### <a name="to-check-for-updates-programmatically"></a>Para buscar actualizaciones mediante programación  
  
1. Cree una nueva aplicación de Windows Forms con su línea de comandos o herramientas visuales preferidas.  
  
2. Cree el botón, el elemento de menú u otro elemento de la interfaz de usuario que desee que los usuarios seleccionen para buscar actualizaciones. En el controlador de eventos de ese elemento, llame al método siguiente para buscar e instalar actualizaciones.  
  
     [!code-cpp[ClickOnceAPI#6](../snippets/cpp/VS_Snippets_Winforms/ClickOnceAPI/cpp/form1.cpp#6)]
     [!code-csharp[ClickOnceAPI#6](../snippets/csharp/VS_Snippets_Winforms/ClickOnceAPI/CS/Form1.cs#6)]
     [!code-vb[ClickOnceAPI#6](../snippets/visualbasic/VS_Snippets_Winforms/ClickOnceAPI/VB/Form1.vb#6)]  
  
3. Compile la aplicación.  
  
### <a name="using-mageexe-to-deploy-an-application-that-checks-for-updates-programmatically"></a>Usar Mage.exe para implementar una aplicación que compruebe las actualizaciones mediante programación  
  
- Siga las instrucciones para implementar la aplicación mediante Mage.exe como se explica en [Tutorial: implementar manualmente una aplicación ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md). Al llamar a Mage.exe para generar el manifiesto de implementación, asegúrese de usar el modificador de la línea de comandos `providerUrl` y para especificar la dirección URL donde ClickOnce debe comprobar si hay actualizaciones. Si la aplicación va a actualizar desde `http://www.adatum.com/MyApp` , por ejemplo, la llamada para generar el manifiesto de implementación podría tener el siguiente aspecto:  
  
    ```  
    mage -New Deployment -ToFile WindowsFormsApp1.application -Name "My App 1.0" -Version 1.0.0.0 -AppManifest 1.0.0.0\MyApp.manifest -providerUrl http://www.adatum.com/MyApp/MyApp.application  
    ```  
  
### <a name="using-mageuiexe-to-deploy-an-application-that-checks-for-updates-programmatically"></a>Usar MageUI.exe para implementar una aplicación que compruebe las actualizaciones mediante programación  
  
- Siga las instrucciones para implementar la aplicación mediante Mage.exe como se explica en [Tutorial: implementar manualmente una aplicación ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md). En la pestaña **Opciones de implementación** , establezca el campo Ubicación de **Inicio** en el manifiesto de aplicación ClickOnce debe comprobar si hay actualizaciones. En la pestaña **Opciones de actualización** , desactive la casilla **esta aplicación debe buscar actualizaciones** .  
  
## <a name="net-framework-security"></a>Seguridad de .NET Framework  
 La aplicación debe tener permisos de plena confianza para usar la actualización mediante programación.  
  
## <a name="see-also"></a>Consulte también  
 [Cómo: especificar una ubicación alternativa para las actualizaciones de implementación](../deployment/how-to-specify-an-alternate-location-for-deployment-updates.md)   
 [Elegir una estrategia de actualización de ClickOnce](../deployment/choosing-a-clickonce-update-strategy.md)   
 [Publicar aplicaciones ClickOnce](../deployment/publishing-clickonce-applications.md)
