---
title: 'Tutorial: Crear un instalador personalizado para una aplicación ClickOnce | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-deployment
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, custom installer
- installer [ClickOnce], custom
- deploying applications [ClickOnce], custom installer
- InPlaceHostingManager [ClickOnce], custom installer
- custom installer [ClickOnce]
ms.assetid: fb222cc5-8aeb-4b94-8c49-b93e342f5f69
caps.latest.revision: 36
author: mikejo5000
ms.author: mikejo
manager: wpickett
ms.openlocfilehash: 2e544bf49437ce6e3c1e8de1b7c792c63a32700a
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47576194"
---
# <a name="walkthrough-creating-a-custom-installer-for-a-clickonce-application"></a>Tutorial: Crear un instalador personalizado para una aplicación ClickOnce
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [Tutorial: crear un instalador personalizado para una aplicación ClickOnce](https://docs.microsoft.com/visualstudio/deployment/walkthrough-creating-a-custom-installer-for-a-clickonce-application).  
  
Cualquier aplicación ClickOnce basada en un archivo .exe se puede instalar en modo silencioso y actualizado mediante un instalador personalizado. Un instalador personalizado puede implementar la experiencia de usuario personalizada durante la instalación, incluidos los cuadros de diálogo personalizados para las operaciones de mantenimiento y seguridad. Para realizar operaciones de instalación, el instalador personalizado utiliza la <xref:System.Deployment.Application.InPlaceHostingManager> clase. Este tutorial muestra cómo crear a un instalador personalizado que instala silenciosamente una aplicación ClickOnce.  
  
## <a name="prerequisites"></a>Requisitos previos  
  
### <a name="to-create-a-custom-clickonce-application-installer"></a>Para crear a un instalador personalizado de la aplicación ClickOnce  
  
1.  En la aplicación ClickOnce, agregue referencias a System.Deployment y System.Windows.Forms.  
  
2.  Agregar una nueva clase a la aplicación y especificar cualquier nombre. En este tutorial usa el nombre `MyInstaller`.  
  
3.  Agregue el siguiente `Imports` o `using` instrucciones a la parte superior de la nueva clase.  
  
    ```vb  
    Imports System.Deployment.Application  
    Imports System.Windows.Forms  
    ```  
  
    ```csharp  
    using System.Deployment.Application;  
    using System.Windows.Forms;  
    ```  
  
4.  Agregue los métodos siguientes a la clase.  
  
     Estos métodos llaman a <xref:System.Deployment.Application.InPlaceHostingManager> métodos para descargar el manifiesto de implementación, validar los permisos adecuados, pedir al usuario permiso para instalar y, a continuación, descargue e instale la aplicación en la memoria caché de ClickOnce. Un instalador personalizado puede especificar que una aplicación ClickOnce es de confianza previamente, o puede diferir la decisión de confianza para el <xref:System.Deployment.Application.InPlaceHostingManager.AssertApplicationRequirements%2A> llamada al método. Este código previamente confía en la aplicación.  
  
    > [!NOTE]
    >  Los permisos asignados previamente confiando en no pueden superar los permisos del código de instalador personalizado.  
  
     [!code-csharp[System.Deployment.Application.InPlaceHostingManager#1](../snippets/csharp/VS_Snippets_Winforms/System.Deployment.Application.InPlaceHostingManager/CS/Form1.cs#1)]
     [!code-vb[System.Deployment.Application.InPlaceHostingManager#1](../snippets/visualbasic/VS_Snippets_Winforms/System.Deployment.Application.InPlaceHostingManager/VB/Form1.vb#1)]  
  
5.  Para intentar la instalación desde el código, llame a la `InstallApplication` método. Por ejemplo, si la clase se llama `MyInstaller`, te-tí `InstallApplication` de la manera siguiente.  
  
    ```vb  
    Dim installer As New MyInstaller()  
    installer.InstallApplication("\\myServer\myShare\myApp.application")  
    MessageBox.Show("Installer object created.")  
    ```  
  
    ```csharp  
    MyInstaller installer = new MyInstaller();  
    installer.InstallApplication(@"\\myServer\myShare\myApp.application");  
    MessageBox.Show("Installer object created.");  
    ```  
  
## <a name="next-steps"></a>Pasos siguientes  
 Una aplicación ClickOnce también puede agregar lógica de actualización personalizada, incluida una interfaz de usuario personalizada para mostrar durante el proceso de actualización. Para obtener más información, consulta <xref:System.Deployment.Application.UpdateCheckInfo>. Una aplicación ClickOnce también puede suprimir la entrada estándar del menú Inicio, acceso directo y entrada en Agregar o quitar programas usando un `<customUX>` elemento. Para obtener más información, consulte [ \<entryPoint > elemento](../deployment/entrypoint-element-clickonce-application.md) y <xref:System.Deployment.Application.DownloadApplicationCompletedEventArgs.ShortcutAppId%2A>.  
  
## <a name="see-also"></a>Vea también  
 [Manifiesto de aplicación ClickOnce](../deployment/clickonce-application-manifest.md)   
 [\<entryPoint > elemento](../deployment/entrypoint-element-clickonce-application.md)



