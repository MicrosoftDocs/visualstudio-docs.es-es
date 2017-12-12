---
title: "Tutorial de Visual Studio Tools para Unity Azure: Cliente móvil | Microsoft Docs"
ms.custom: 
ms.date: 10/19/2017
ms.reviewer: crdun
ms.suite: 
ms.technology: tgt-pltfrm-cross-plat
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5A8762A1-D843-4FD8-A89B-E5E489ECA03D
author: dantogno
ms.author: v-davian
manager: crdun
ms.openlocfilehash: 294942641aa0739d105a888f4fbfe6ba9cf05a16
ms.sourcegitcommit: ee42a8771f0248db93fd2e017a22e2506e0f9404
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/09/2017
---
# <a name="implement-the-azure-mobileserviceclient"></a>Implementación de MobileServiceClient de Azure

En el SDK de Azure Mobile Client, <a href="https://msdn.microsoft.com/en-us/library/azure/microsoft.windowsazure.mobileservices.mobileserviceclient(v=azure.10).aspx">MobileServiceClient</a> es fundamental y permite el acceso al back-end de la aplicación móvil.

## <a name="locate-the-url-of-the-mobile-app-backend"></a>Buscar la dirección URL del back-end de la aplicación móvil

El constructor `MobileServiceClient` toma la dirección URL de la aplicación móvil como un parámetro, por lo que antes de continuar, busque la dirección URL.

1. En Azure Portal, haga clic en el botón **App Services**.

    ![Hacer clic en App Services](media/vstu_azure-implement-azure-mobileserviceclient-image1.png)

2. Haga clic en la entrada de la aplicación móvil.

    ![Hacer clic en la aplicación móvil](media/vstu_azure-implement-azure-mobileserviceclient-image2.png)

3. Copie la dirección URL del back-end de la aplicación móvil.

    ![Copiar la dirección URL](media/vstu_azure-implement-azure-mobileserviceclient-image3.png)

## <a name="create-the-mobileserviceclient-singleton"></a>Crear el singleton MobileServiceClient

Solo debe haber una instancia de `MobileServiceClient`, por lo que en el tutorial se usa una variación del patrón de singleton.

1. Dentro del directorio **Assets/Scripts** del proyecto de Unity, cree un script de C# denominado **AzureMobileServiceClient**.

2. Abra el script `AzureMobileServiceClient` y elimine cualquier código de plantilla existente, incluidas las instrucciones using y la declaración de clase.

3. Agregue el código siguiente:

  ```csharp
  using Microsoft.WindowsAzure.MobileServices;

  public static class AzureMobileServiceClient
  {
      private const bool ignoreTls = true;
      private const string backendUrl = "MOBILE_APP_URL";
      private static MobileServiceClient client;

      public static MobileServiceClient Client
      {
          get
          {
              if (client == null)
              {
                  client = new MobileServiceClient(backendUrl);
              }

              return client;
          }
      }
  }
  ```

  > [!NOTE]
  > Si IntelliSense no reconoce el espacio de nombres Microsoft.WindowsAzure, compruebe que ha completado todos los pasos de la sección [Preparación del entorno de desarrollo]().

4. En el código anterior, reemplace `MOBILE_APP_URL` con la dirección URL del back-end de la aplicación móvil.

## <a name="next-step"></a>Paso siguiente

* [Actualizar el almacén de seguridad de Unity Mono](visual-studio-tools-for-unity-azure-security.md)
