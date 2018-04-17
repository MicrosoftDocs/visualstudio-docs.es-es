---
title: 'Tutorial: Crear un instalador personalizado para una aplicación ClickOnce | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-deployment
ms.topic: conceptual
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
author: stevehoag
ms.author: shoag
manager: wpickett
ms.workload:
- multiple
ms.openlocfilehash: 585a33a8a3c49792be0cc986b36636e7107290ac
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="walkthrough-creating-a-custom-installer-for-a-clickonce-application"></a>Tutorial: Crear un instalador personalizado para una aplicación ClickOnce
Cualquier aplicación ClickOnce basada en un archivo .exe se pueden instalar en modo silencioso y actualizar a través de un instalador personalizado. Un instalador personalizado puede implementar la experiencia de usuario personalizada durante la instalación, incluidos los cuadros de diálogo personalizados para las operaciones de seguridad y mantenimiento. Para llevar a cabo operaciones de instalación, el instalador personalizado utiliza la <xref:System.Deployment.Application.InPlaceHostingManager> clase. Este tutorial muestra cómo crear a un instalador personalizado que instala silenciosamente una aplicación ClickOnce.  
  
## <a name="prerequisites"></a>Requisitos previos  
  
### <a name="to-create-a-custom-clickonce-application-installer"></a>Para crear a un instalador personalizado de la aplicación ClickOnce  
  
1.  En la aplicación ClickOnce, agregue referencias a System.Deployment y System.Windows.Forms.  
  
2.  Agregar una nueva clase a la aplicación y especifique cualquier nombre. Este tutorial utiliza el nombre `MyInstaller`.  
  
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
  
     Llamar estos métodos <xref:System.Deployment.Application.InPlaceHostingManager> métodos para descargar el manifiesto de implementación, validar los permisos adecuados, pedir al usuario permiso para instalar y, a continuación, descargue e instale la aplicación en la caché de ClickOnce. Un instalador personalizado puede especificar que una aplicación ClickOnce es de confianza previamente o puede diferir la decisión de confianza para el <xref:System.Deployment.Application.InPlaceHostingManager.AssertApplicationRequirements%2A> llamada al método. Este código previamente confía en la aplicación.  
  
    > [!NOTE]
    >  Los permisos asignados previamente confiando en no pueden superar los permisos del código del instalador personalizado.  
  
     [!code-vb[System.Deployment.Application.InPlaceHostingManager#1](../deployment/codesnippet/VisualBasic/walkthrough-creating-a-custom-installer-for-a-clickonce-application_1.vb)]
     [!code-csharp[System.Deployment.Application.InPlaceHostingManager#1](../deployment/codesnippet/CSharp/walkthrough-creating-a-custom-installer-for-a-clickonce-application_1.cs)]  
  
5.  Para intentar la instalación desde el código, llame a la `InstallApplication` método. Por ejemplo, si el nombre de la clase `MyInstaller`, puede llamar a `InstallApplication` de la manera siguiente.  
  
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
 Una aplicación ClickOnce también puede agregar lógica de actualización personalizada, incluida una interfaz de usuario personalizada para mostrar durante el proceso de actualización. Para obtener más información, consulta <xref:System.Deployment.Application.UpdateCheckInfo>. Una aplicación ClickOnce también puede suprimir la entrada estándar del menú Inicio, el acceso directo y la entrada agregar o quitar programas mediante un `<customUX>` elemento. Para obtener más información, consulte [ \<entryPoint > elemento](../deployment/entrypoint-element-clickonce-application.md) y <xref:System.Deployment.Application.DownloadApplicationCompletedEventArgs.ShortcutAppId%2A>.  
  
## <a name="see-also"></a>Vea también  
 [Manifiesto de aplicación ClickOnce](../deployment/clickonce-application-manifest.md)   
 [\<entryPoint > elemento](../deployment/entrypoint-element-clickonce-application.md)