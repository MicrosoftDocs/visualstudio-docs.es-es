---
title: "Como: Buscar actualizaciones de aplicaciones mediante programaci&#243;n utilizando la API de implementaci&#243;n de ClickOnce | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-deployment"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "actualizaciones de aplicaciones"
  - "implementación ClickOnce, actualizaciones"
ms.assetid: 1a886310-67c8-44e5-a382-c2f0454f887d
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Como: Buscar actualizaciones de aplicaciones mediante programaci&#243;n utilizando la API de implementaci&#243;n de ClickOnce
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

ClickOnce proporciona dos maneras de actualizar una aplicación una vez implementada.  En el primer método, puede configurar la implementación ClickOnce para comprobar automáticamente las actualizaciones en ciertos intervalos.  En el segundo método, puede escribir código que utiliza la clase <xref:System.Deployment.Application.ApplicationDeployment> para comprobar las actualizaciones basadas en un evento, como una solicitud del usuario.  
  
 Los procedimientos siguientes muestran código para realizar una actualización de programación y describen cómo configurar una implementación ClickOnce para habilitar las comprobaciones de actualización de programación.  
  
 Para actualizar una aplicación ClickOnce mediante programación, debe especificar la ubicación de las actualizaciones.  A veces, esto se denomina proveedor de implementación.  Para obtener más información sobre cómo establecer esta propiedad, vea [Elegir una estrategia de actualización de ClickOnce](../deployment/choosing-a-clickonce-update-strategy.md).  
  
> [!NOTE]
>  También puede utilizar la técnica descrita a continuación para implementar su aplicación desde una ubicación y actualizarla desde otra.  Para obtener más información, vea [Cómo: Especificar una ubicación alternativa para las actualizaciones de la implementación](../deployment/how-to-specify-an-alternate-location-for-deployment-updates.md).  
  
### Para buscar actualizaciones mediante programación  
  
1.  Cree una nueva aplicación de formularios Windows Forms mediante su línea de comandos o herramientas visuales preferidas.  
  
2.  Cree cualquier botón, elemento de menú u otro elemento de la interfaz de usuario que desee que los usuarios seleccionen para comprobar las actualizaciones.  Desde el controlador de eventos del elemento, llame al método siguiente para comprobar si hay actualizaciones e instalarlas.  
  
     [!CODE [ClickOnceAPI#6](../CodeSnippet/VS_Snippets_Winforms/ClickOnceAPI#6)]  
  
3.  Compile la aplicación.  
  
### Utilizar Mage.exe para implementar una aplicación que comprueba mediante programación las actualizaciones  
  
-   Siga las instrucciones para implementar su aplicación mediante Mage.exe como se explica en [Tutorial: Implementar manualmente una aplicación ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md).  Al llamar a Mage.exe para generar el manifiesto de implementación, asegúrese de utilizar el modificador de la línea de comandos `providerUrl` y de especificar la dirección URL donde ClickOnce debe comprobar las actualizaciones.  Si la aplicación se va a actualizar desde [http:\/\/www.adatum.com\/MyApp](http://www.adatum.com/MyApp), por ejemplo, la llamada para generar el manifiesto de implementación sería similar a la siguiente:  
  
    ```  
    mage -New Deployment -ToFile WindowsFormsApp1.application -Name "My App 1.0" -Version 1.0.0.0 -AppManifest 1.0.0.0\MyApp.manifest -providerUrl http://www.adatum.com/MyApp/MyApp.application  
    ```  
  
### Utilizar MageUI.exe para implementar una aplicación que comprueba mediante programación las actualizaciones  
  
-   Siga las instrucciones para implementar su aplicación mediante Mage.exe como se explica en [Tutorial: Implementar manualmente una aplicación ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md).  En la ficha **Deployment Options** \(Opciones de implementación\), establezca el campo **Start Location** \(Iniciar ubicación\) en el manifiesto de aplicación en el que ClickOnce debe comprobar las actualizaciones.  En la ficha **Update Options** \(Opciones de actualización\), desactive la casilla **This application should check for updates** \(Esta aplicación buscará actualizaciones\).  
  
## Seguridad de .NET Framework  
 La aplicación debe tener permisos de plena confianza para utilizar la actualización mediante programación.  
  
## Vea también  
 [Cómo: Especificar una ubicación alternativa para las actualizaciones de la implementación](../deployment/how-to-specify-an-alternate-location-for-deployment-updates.md)   
 [Elegir una estrategia de actualización de ClickOnce](../deployment/choosing-a-clickonce-update-strategy.md)   
 [Publicar aplicaciones ClickOnce](../deployment/publishing-clickonce-applications.md)